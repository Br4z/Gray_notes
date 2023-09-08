---
id: lwyj2bi4w2stkvr9e2cq3oa
title: Processing
desc: ''
updated: 1692300427196
created: 1691856758554
---

## Course

- Playlist title: Curso: Aprende a programar con processing.

- [Source](https://www.youtube.com/playlist?list=PLFXPMjONHtCSUiJ6NPq5S7JJ9CUjk5W8d).

[Processing reference](https://processing.org/reference/).

Processing is a free graphical library and integrated development environment (IDE) built for the electronic arts, new media art, and visual design communities with the purpose of teaching non-programmers the fundamentals of computer programming in a visual context.

### Cordinates displayer

```JAVA
void setup() {
	size(400, 400);
}

void draw() {
	background(0);
	text("X: " + mouseX + " Y: " + mouseY, mouseX + 10, mouseY - 10);
}
```

### Circle moving horizontally

```JAVA
int positionX = 50;

void setup() {
	size(500, 500);
}

void draw() {
	background(0);
	if (positionX + 50 < width) positionX++;

	circle(positionX, height / 2, 100);
}
```

### Coloring sections of a 2x2 canvas

```JAVA
void setup() {
	size(600, 600);
}

void draw() {
	background(0);
	if (mouseX > width / 2) {
		if (mouseY < height / 2) rect(width / 2, 0, width, height /2);
		else rect(width / 2, height /2, width, height);
	} else {
		if (mouseY < height / 2) rect(0, 0, width / 2, height /2);
		else rect(0, height / 2, width / 2, height);
	}
}
```

### Drawing lines in the middle of a 1x3 canvas

```JAVA
int sectionWidth;

void setup() {
	size(600, 600);
	sectionWidth = width / 3;
}

void draw() {
	if (sectionWidth < mouseX && mouseX < sectionWidth * 2) line(mouseX, 0, mouseX, height);
}
```

### Coloring the background and drawing shapes (circle or square)

```JAVA
boolean isCircle, isIncreasing;
int colorValue;

void setup() {
	size(600, 600);
	isCircle = false;
	isIncreasing = true;
	colorValue = 1;
}

void draw() {
	background(colorValue);
	if (isCircle) circle(width / 2, height / 2, 100);
	else square(width / 2 - 50, height / 2 - 50, 100);

	if (isIncreasing) colorValue++;
	else colorValue--;

	if (colorValue == 255 || colorValue == 0) isIncreasing = !isIncreasing;
}

void mouseClicked() {
	isCircle = !isCircle;
}
```

### Drawing custom shapes

```JAVA
void setup() {
	size(600, 600);
	customSquare(width / 4 - 50, height / 2 - 50, 100);
	fill(255);
	customCircle(width / 2 + width / 4, height / 2, 100);
}

void customSquare(float x1, float y1, float squareSize) {
	square(x1, y1, squareSize);
	fill(0);
	square(x1 + squareSize / 2, y1, squareSize / 2);
	square(x1, y1 + squareSize / 2, squareSize / 2);
}

void customCircle(float x, float y, float diameter) {
	circle(x, y, diameter);
	line(x - diameter / 2, y, x + diameter / 2, y);
	line(x, y - diameter / 2, x, y + diameter / 2);
}
```

### Drawing a grid

```JAVA
void setup() {
	size(600, 600);

	for (int x = 0; x <= width; x += 30) line(x, 0, x, height);
	for (int y = 0; y < height; y += 30) line(0, y, width, y);
}
```

### Drawing a circle grid with gradient

```JAVA
void setup() {
	size(600, 600);
}

void draw() {
	background(0);
	for (int x = 0; x <= width; x += 30) {
		for (int y = 0; y <= height; y += 30) {
			fill(x % 255, y % 255, 0);
			circle(x + frameCount % 30, y, 20);
		}
	}
}
```

### Electron trajectory

```JAVA
PImage nucleus, electron;
float x, y, r;

void setup() {
	size(600, 600);
	nucleus = loadImage("Nucleus.png");
	electron = loadImage("Electron.png");
	r = 100;
}

void draw() {
	background(0);

	x = mouseX + r * cos(frameCount * 0.1);
	y = mouseY + r * sin(frameCount * 0.1);

	text(x + " " + y, 100, 100);

	image(nucleus, mouseX - 50, mouseY - 50, 100, 100);
	image(electron, x - 25, y - 25, 50, 50);
}
```

### Spraying with the mouse buttons

```JAVA
boolean isPainting;
float range;

void setup() {
	size(600, 600);
	background(180);
	noStroke();
	isPainting = false;
	range = 10;
}

void draw() {
	if (isPainting) {
		circle(random(mouseX - range, mouseX + range), random(mouseY - range, mouseY + range), 10);
	}
}

void mousePressed() {
	if (mouseButton == LEFT) fill(255);
	else if (mouseButton == RIGHT) fill(0);
	isPainting = true;
}

void mouseReleased() {
	isPainting = false;
}
```

### Sniper reticle

```JAVA
float x, y, d;

void setup() {
	size(600, 600);
	noFill();
	stroke(0, 255, 0);
	strokeWeight(5);

	x = width / 2;
	y = height / 2;
	d = 50;
}

void draw() {
	background(0);
	circle(x, y, d);
	line(0, y, width, y);
	line(x, 0, x, height);
}

void keyPressed() {
	if (keyCode == UP && y - d / 2 >= 0) y -= 10;
	else if (keyCode == LEFT && x - d / 2 >= 0) x -= 10;
	else if (keyCode == DOWN && y + d / 2 <= height) y += 10;
	else if (keyCode == RIGHT && x + d / 2 <= width) x += 10;
	else if (key == 32) background(255, 0, 0);
}
```

### Interactive ellipse

```JAVA
color[] colors = { color(255, 0, 0), color(0, 255, 0), color(0, 0, 255) };
float ellipseWidth, ellipseHeight;
int ellipseColor;

void setup() {
	size(600, 600);
}

void draw() {
	background(0);

	ellipseColor = (int) map(mouseX, 0, width, 0, colors.length);
	ellipseWidth = map(mouseX, 0, width, 0, width);
	ellipseHeight = map(mouseY, 0, height, 0, height);

	fill(colors[ellipseColor]);
	ellipse(width / 2, height / 2, ellipseWidth, ellipseHeight);
}
```

### Resistor app

```JAVA
color[] colors = {
	color(0, 0, 0), // Black
	color(98, 50, 50), // Brown
	color(255, 0, 0), // Red
	color(255, 128, 0), // Orange
	color(255, 255, 0), // Yellow
	color(0, 128, 0), // Green
	color(0, 128, 192), // Blue
	color(128, 0, 255), // Violet
	color(128, 128, 128), // Gray
	color(255, 255, 255) // White
};
int[] bands = { 5, 0, 0 };
int colorCliked;
boolean isDragging;

void setup() {
	size(360, 640);
	textSize(30);
}

void draw() {
	background(255);

	for (int i = 0; i < 10; i++) {
		fill(colors[i]);
		square(width - 0.1 * height, 0.1 * i * height, 0.1 * height);
	}

	fill(247, 203, 145);
	rect(0.25 * width, 0.1 * height, 0.3 * width, 0.6 * height);
	fill(colors[bands[0]]);
	rect(0.25 * width, 0.2 * height, 0.3 * width, 0.05 * height);
	fill(colors[bands[1]]);
	rect(0.25 * width, 0.35 * height, 0.3 * width, 0.05 * height);
	fill(colors[bands[2]]);
	rect(0.25 * width, 0.5 * height, 0.3 * width, 0.05 * height);

	if (isDragging) {
		fill(colors[colorCliked]);
		circle(mouseX, mouseY, 20);
	}

	int value = (bands[0] * 10 + bands[1]) * (int) pow(10, bands[2]);

	if (value >= 1000000) text(value / 1000000 + " MΩ", 0.25 * width, 0.75 * height);
	else if (value >= 1000) text(value / 1000 + " KΩ", 0.25 * width, 0.75 * height);
	else text(value + " Ω", 0.25 * width, 0.75 * height);
}


void mousePressed() {
	if (width - 0.1 * height < mouseX) {
		isDragging = true;
		colorCliked = (int) map(mouseY, 0 , height, 0, 9);
	}
}

void mouseReleased() {
	isDragging = false;

	if (0.25 * width <= mouseX && mouseX <= 0.55 * width) {
		int bandNumber = (int) map(mouseY, 0.2 * height, 0.6 * height, 0, 3);
		if (0 <= bandNumber && bandNumber <= 2) bands[bandNumber] = colorCliked;
	}
}
```

### Calculation game

```JAVA
float x, y, side, margin;
int number1, number2, operator, answer, userOperator;


void setup() {
	size(360, 640);
	x = 0.1 * width;
	y = 0.5 * height;
	side = 0.8 * width;
	margin = x;
	textSize(0.15 * side);
	getOperation();
}

void draw() {
	background(255);
	fill(255);
	square(x, y, side);
	line(x, y + side / 2, x + side, y + side / 2);
	line(x + side / 2, y, x + side / 2, y + side);

	drawOperators();
	fill(0);
	text(number1 + " ? " + number2 + " = " + answer, x, 0.25 * height);
	println(userOperator + " = " + operator);
}

void drawOperators() {
	strokeWeight(20);
	// Sum
	line(x + margin, y + side / 4, x + side / 2 - margin, y + side / 4);
	line(x + side / 4, y + margin, x + side / 4, y + side / 2 - margin);

	// Rest
	line(x + side / 2 + margin, y + side / 4, x + side - margin, y + side / 4);

	// Division
	circle(x + side / 4, y + side / 2 + margin, 5);
	line(x + margin, y + side / 2 + side / 4, x + side / 2 - margin, y + side / 2 + side / 4);
	circle(x + side / 4, y + side - margin, 5);

	// Multiplication
	line(x + side / 2 + margin, y + side / 2 + margin, x + side - margin, y + side - margin);
	line(x + side / 2 + margin, y + side - margin, x + side - margin, y + side / 2 + margin);

	strokeWeight(3);
}

void getOperation() {
	number1 = (int) random(1, 11);
	number2 = (int) random(1, 11);
	operator = (int) random(4);

	switch (operator) {
		case 0:
			answer = number1 + number2;
			break;

		case 1:
			answer = number1;
			number1 *= number2;
			break;

		case 2:
			answer = number1 - number2;
			break;

		case 3:
			answer = number1 * number2;
			break;
	}
}

void mousePressed() {
	if (x <= mouseX && mouseX <= x + side) {
			if (mouseX <= x + side / 2) {
					if (mouseY <= y + side / 2) userOperator = 0;
					else userOperator = 1;
			} else {
					if (mouseY <= y + side / 2) userOperator = 2;
					else userOperator = 3;
			}
	}

	if (operator == userOperator) getOperation();
	else background(255, 0, 0);
}
```

### Interactive cartesian plane

```JAVA
float x, y1, y2, side, sliderM, sliderB, m , b, gridSize;
boolean movingM, movingB;

void setup() {
	size(360, 640);
	x = 0.1 * width;
	y1 = 0.8 * height;
	y2 = 0.9 * height;
	side = 0.8 * width;
	sliderM = width / 2;
	sliderB = width / 2;
	gridSize = 0.05 * width;
	textSize(x);
}

void draw() {
	background(255);
	line(x, y1, x + side, y1);
	circle(sliderM, y1, 30);
	line(x, y2, x + side, y2);
	circle(sliderB, y2, 30);

	m = ((int) map(sliderM, x, x + side, -80, 80)) / 10.0;
	b = ((int) map(sliderB, x, x + side, -80, 80)) / 10.0;


	fill(0);
	text("y = " + m + "x + (" + b + ")", x, 0.6 * height);
	fill(255);

	if (x < mouseX && mouseX < x + side) {
			if (movingM) sliderM = mouseX;
			else if (movingB) sliderB = mouseX;
	}

	drawPlane();
	drawEquation();
}

void mousePressed() {
	if (abs(mouseY - y1) < 30) movingM = true;
	else if (abs(mouseY - y2) < 30) movingB = true;
}

void mouseReleased() {
	if (movingM) movingM = false;
	else if (movingB) movingB = false;
}

void drawPlane() {
	strokeWeight(1);
	square(x, x, side);

	for (float i = x; i <= x + side; i += gridSize) {
		line(i, x, i, x + side); // Horizontal lines
		line(x, i, x + side, i); // Vertical lines
	}

	strokeWeight(3);

	line(x + side / 2, x, x + side / 2, x + side); // y axis
	line(x, x + side / 2, x + side, x + side / 2); // x axis
}

void drawEquation() {
	// mx + b = -8, mx + b = 8
	float x1 =  (-8 - b) / m;
	float x2 =  (8 - b) / m;

	if (abs(x1) > 8 || abs(x2) > 8) {
		float y1 = -1 * (m * -8 + b);
		float y2 = -1 * (m * 8 + b);

		y1 *= gridSize;
		y2 *= gridSize;

		y1 += x + side / 2;
		y2 += x + side / 2;

		stroke(0, 0, 255);
		line(x, y1, x + side, y2); // from (-8,y1) to (8,y2)
		stroke(0);

	} else {
		x1 *= gridSize;
		x2 *= gridSize;

		x1 += x + side / 2;
		x2 += x + side / 2;

		stroke(0, 0, 255);
		line(x1, x + side, x2, x); // from (x1,-8) to (x2,8)
		stroke(0);
	}
}
```
