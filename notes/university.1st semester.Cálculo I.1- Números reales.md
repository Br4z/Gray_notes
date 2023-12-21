---
id: klwkyyk0lmhg2az72q7889k
title: 1- Números reales
desc: ''
updated: 1703188578598
created: 1680208075055
---

1. Simplifique tanto como sea posible las siguientes expresiones.

	- $\frac{ 24 x^3 y^4 }{ 1 - x^2 } \left ( \frac{ 18 x^{ -2 } y^5 }{ y + x y } \right )^{ -1 }$

		Primero manipulamos la expresión.

		$$
		\frac{ 24 x^3 y^4 }{ (1 - x) (1 + x) } \left (\frac{ y (1 + x) }{ \frac{ 18 }{ x^2 } y^5 } \right ) \\[10 pt]

		\frac{ 24 x^3 y^4 }{ (1 - x) (1 + x) } \left ( \frac{ x^2 (1 + x) }{ 18 y^4 } \right )
		$$

		Por último simplificamos la expresión.

		$$
		\frac{ 4 x^5 }{ 3 (1 - x) }
		$$

	- $[(x^2 + y^2) (x - y)^{ -1 } + 2 (x^{ -1 } - y^{ -1 })^{ -1 }]^{ -1 }$.

		$$
		\left [(x^2 + y^2) \left (\frac{ 1 }{ x - y } \right ) + 2 \left (\frac{ 1 }{ x } - \frac{ 1 }{ y } \right )^{ -1 } \right ]^{ -1 } \\[10 pt]

		\left [(x^2 + y^2) \left (\frac{ 1 }{ x - y } \right ) + 2 \left (\frac{ x y }{ y - x } \right ) \right ]^{ -1 } \\[10 pt]

		\left [\frac{ x^2 + y^2 }{ x - y } + \frac{ 2 x y }{ y - x } \right ]^{ -1 }
		$$

		Podemos escribir $y - x$ como $-(x - y)$.

		$$
		\left [\frac{ x^2 + y^2 }{ x - y } - \frac{ 2 x y }{ x - y } \right ]^{ -1 } = \left [\frac{ x^2 - 2 x y + y^2 }{ x - y } \right ]^{ -1 } \\[10 pt]

		\frac{ (x - y) }{ (x - y)^2 } = (x - y)^{ -1 }
		$$

	- $\frac{ \frac{ x - y }{ x } - \frac{ x + y }{ y } }{ \frac{ x - y }{ y } + \frac{ x + y }{ x } }$.

		$$
		\frac{ \frac{ y (x - y) - x (x + y) }{ x y } }{ \frac{ x (x - y) + y (x + y) }{ x y } } = \frac{ x y (y (x - y) - x (x + y)) }{ x y (x - y) + y (x + y) } \\[10 pt]

		\frac{ x y - y^2 - x^2 - x y }{ x^2 - x y + x y + y^2 } \\[10 pt]

		\frac{ -x^2 - y^2 }{ x^2 + y^2 } = \frac{ -(x^2 + y^2) }{ x^2 + y^2 } = -1
		$$

2. El inverso multiplicativo de $(1 - (1 + x^{ -1 })^{ -1 })$

	Recordemos que si $a$ es el inverso multiplicativo de $b$ se debe cumplir que $a b = 1$ y como consecuencia $a = \frac{ 1 }{ b } = b^{ -1 }$, entonces:

	$$
	(1 - (1 + x^{ -1 })^{ -1 })^{ -1 } \\[10 pt]

	\left (1 - \frac{ x }{ x + 1 } \right )^{ -1 } = \left (\frac{ x + 1 - x }{ x + 1 } \right )^{ -1 } \\[10 pt]

	\left (\frac{ 1 }{ x + 1 } \right )^{ -1 } = x + 1
	$$

3. ¿Cuál debe ser el valor de $c$ para que la solución de la ecuación $7 - (8 - 2 c) x^{ -1 } = 3 + (2 + 3 c) x^{ -1 }$ sea 2?

	Solucionando para $c$.

	$$
	7 - \left (\frac{ 8 - 2 c }{ x } \right ) = 3 + \frac{ 2 + 3 c }{ x } \\[10 pt]

	\frac{ 7 x - (8 - 2 c) }{ x } = \frac{ 3 x + 2 + 3 c }{ x } \quad 7 x - (8 - 2 c) = 3 x + 2 + 3 c \\[10 pt]

	c = 4 x - 10
	$$

	Con la condición $x = 2$, nos queda que $c = 4 (2) - 10 = -2$.

4. Resuelva las siguientes ecuaciones.

	- $\frac{ 4 }{ 1 - x^2 } = \frac{ 3 }{ x - 1 } + \frac{ 2 }{ x + 1 }$.

		Las condiciones de su solución debe cumplir $x \neq -1 \quad y \quad x \neq 1$.

		$$
		\frac{ 4 }{ -(x^2 - 1) } = \frac{ 3 (x + 1) + 2 (x - 1) }{ x^2 -1 } \\[10 pt]

		4 = -\frac{ 3 (x + 1) + 2 (x - 1) }{ x^2 - 1 } (x^2 - 1) \\[10 pt]

		4 = -5 x - 1 \quad x = \frac{ 5 }{ -5 } = -1
		$$

		Como $x = -1$, entonces decimos que la ecuación no tiene solución.

	- $\sqrt{ (x - 2) } - x + 4 = 0$.

		Las condiciones de su solución debe cumplir que $x \in [2, \infty)$.

		$$
		(\sqrt{ x - 2 })^2 = (x - 4)^2 \quad x - 2 = x^2 - 8x + 16 \\[10 pt]

		x^2 - 9 x + 18 = (x - 6) (x - 3) = 0
		$$

		Entonces $x = 6$ o $x = 3$, números que están en el dominio de la ecuación.

	- $|3x + 6| - 2 |x - 4| = -11$.

		Analizando todos los casos ($2^2$).

		1. $3 x + 6 \geq 0 \quad x - 4 \geq 0$.

			$$
			x \geq -2 \quad x \geq 4 \\[10 pt]

			x \in [-2,\infty) \quad x \in [4,\infty) \quad x \in [4,\infty) \\[10 pt]

			3 x + 6 - 2 (x - 4) = -11 \quad x + 14 = -11 \quad x = -25
			$$

			Como $x = -25$ no está en el intervalo, **no es solución**.

		2. $3x + 6 < 0 \quad x - 4 < 0$.

			$$
			x < -2 \quad x < 4 \\[10 pt]

			x \in (-\infty,-2) \quad x \in (-\infty,4) \quad x \in [-\infty,-2) \\[10 pt]

			-(3x + 6) - 2 (-(x - 4)) = -11 \quad -x - 14 = -11 \quad x = -3
			$$

			Como $x = -3$ está en el intervalo, entonces es **solución**.

		3. $3x + 6 \geq 0 \quad x - 4 < 0$.

			$$
			x \geq -2 \quad x < 4 \\[10 pt]

			x \in [-2,\infty) \quad x \in (-\infty,4) \quad x \in [-2,4) \\[10 pt]

			3 x + 6 - 2 (-(x - 4)) = -11 \quad 5 x - 2 = -11 \quad x = -\frac{ 9 }{ 5 }
			$$

			Como $-\frac{ 9 }{ 5 }$ está en el intervalo, es **solución**.

		4. $3x + 6 < 0 \quad x - 4 \geq 0$.

			$$
			x < -2 \quad x \geq 4 \quad x \in \empty
			$$

			Ningún número podrá satisfacerla las condiciones, por lo que diremos que **no tiene solución**.

		Diremos que $x \in \{ -3,-\frac{ 9 }{ 5 } \}$.

5. Resuelva las siguientes inecuaciones.

	- $x (x - 2) < 15$.

		$$
		x^2 - 2 x < 15 \quad x^2 - 2 x - 15 < 0 \quad (x - 5) (x + 3) < 0
		$$

		Para que un producto sea menor a cero, sabemos que debe ocurrir alguno de los siguientes casos:

		1. El primer factor es negativo, y el segundo es positivo.

			$$
			x - 5 < 0 \quad x + 3 > 0 \\[10 pt]

			x < 5 \quad x > -3 \quad x \in (-3,5) \\[10 pt]
			$$

		2. El primer factor es positivo, y el segundo es negativo.

			$$
			x - 5 > 0 \quad x + 3 < 0 \\[10 pt]

			x > 5 \quad x < -3 \quad x \in \empty \\[10 pt]
			$$

		Entonces $x \in (-3,5)$.

	- $\frac{ 2 x + 3 }{ x - 4 } \geq 3$.

		$$
		\frac{ 2 x + 3 }{ x - 4 } - 3 \geq 0 \quad \frac{ 2 x + 3 - 3 (x - 4) }{ x - 4 } \geq \quad \frac{ -x + 15 }{ x - 4 } \geq 0
		$$

		Para que un cociente sea positivo, sabemos que debe ocurrir alguno de los siguientes casos:

		1. Tanto el denominador como el numerador son positivos.

			$$
			-x + 15 \geq 0 \quad x - 4 > 0 \\[10 pt]

			x \leq 15 \quad x > 4 \quad x \in (4,15] \\[10 pt]
			$$

		2. Tanto el denominador como el numerador son negativos.

			$$
			-x + 15 < 0 \quad x - 4 < 0 \\[10 pt]

			x > 15 \quad x < 4 \quad x \in \empty
			$$

		Entonces $x \in (4,15]$.

	- $|5 x - 2| \geq 4$.

		Analizando los 2 casos.

		1. $5 x - 2 \geq 0 \quad x \geq \frac{ 2 }{ 3 }$

			$$
			x \in \left [\frac{ 3 }{ 2 },\infty \right ) \\[10 pt]

			5 x - 2 \geq 4 \quad x \geq \frac{ 6 }{ 5 } \quad x \in \left [\frac{ 6 }{ 5 },\infty \right ) \\[10 pt]
			$$

			La intersección entre la condición de la ecuación y la solución es $x \in \left [\frac{ 6 }{ 5 },\infty \right )$.

		2. $5x - 3 < 0 \quad x < \frac{ 2 }{ 5 }$.

			$$
			x \in \left (-\infty,\frac{ 2 }{ 5 } \right ) \\[10 pt]

			-(5 x - 2) \geq 4 \quad x \leq -\frac{ 2 }{ 5 } \\[10 pt]
			$$

			La intersección entre la condición de la ecuación y la solución es $x \in \left (-\infty, -\frac{ 2 }{ 5 } \right ]$.

		La solución es la **unión** de las soluciones $\mathbb{ R } - \left (-\frac{ 2 }{ 5 }, \frac{ 6 }{ 5 } \right )$.

	- $|x + 3| - 2|x - 1| < 2$

		Considerando los $2^2$ casos.

		1. $x + 3 \geq 0 \quad x - 1 \geq 0$.

			$$
			x \geq -3 \quad x \geq 1 \\[10 pt]

			x \in [-3,\infty) \quad x \in [1,\infty) \quad x \in [1,\infty) \\[10 pt]

			x + 3 - 2x + 2 < 2 \quad -x < -3 \quad x > 3 \\[10 pt]

			x \in (3,\infty) \\[10 pt]
			$$

			La **intersección** del caso y la solución es $x \in (3,\infty)$.

		2. $x + 3 < 0 \quad x - 1 < 0$.

			$$
			x < -3 \quad x < 1 \\[10 pt]

			x \in (-\infty,-3) \quad x \in (-\infty, 1) \quad x \in (-\infty,-3) \\[10 pt]

			-x - 3 + 2x - 2 < 2 \quad x - 5 < 2 \quad x < 7 \\[10 pt]

			x \in (-\infty,7)
			$$

			La **intersección** del caso y la solución es $x \in (-\infty,-3)$.

		3. $x + 3 \geq 0 \quad x - 1 < 0$.

			$$
			x \geq -3 \quad x < 1 \\[10 pt]

			x \in [-3,\infty) \quad x \in (-\infty,1) \quad x \in [-3,1) \\[10 pt]

			x + 3 + 2 x - 2 < 2 \quad 3 x + 1 < 2 \quad x < \frac{ 1 }{ 3 } \quad x \in \left (-\infty, \frac{ 1 }{ 3 } \right )
			$$

			La **intersección** del caso y la solución es $x \in \left [-3,\frac{ 1 }{ 3 } \right ]$.
			$$

		4. $x + 3 < 0 \quad x - 1 \geq 0$.

			$$
			x < -3 \quad x \geq 1 \quad x \in \empty \\[10 pt]
			$$

			Desde las condiciones del caso podemos ver que es **imposible**.

		La solución de esta inecuación es la **unión** de todos los intervalos en los que encontramos solución.

		$$
		x \in (3,\infty) \cup [-3,1) \cup \left [-3,\frac{ 1 }{ 3 } \right ] \quad x \in \mathbb{ R } - \left (\frac{ 1 }{ 3 },3 \right )
		$$

6. El perímetro de un terreno rectangular es $58m$. Si el largo aumenta en $2m$ y el ancho se disminuye en $2m$, el área se disminuye en $40m^2$. Halle las dimensiones del terreno.

	Sí tenemos un rectángulo de medidas $a * b$.

	$$
	\text{ área } = a b \quad \text{ perímetro } = 2 (a + b) = 58 \\[10 pt]

	(a + 2) (b - 2) = \text{ área } - 46 = a b - 43 \quad (1) \\[10 pt]

	2 a + 2 b = 58 \quad a = 29 - b \quad (2)
	$$

	Reemplazando $(2)$ en $(1)$.

	$$
	((29 - b) + 2) (b - 2) = (29 - b) b - 46 \\[10 pt]

	(31 - b) (b - 2) = 29 b - b^2 - 46 \\[10 pt]

	31 b - b^2 - 62 + 2 b = -b^2 + 29 b - 46 \\[10 pt]

	4 b = 16 \quad b = 4 \quad a = 29 - 4 = 25 \quad (2)
	$$
