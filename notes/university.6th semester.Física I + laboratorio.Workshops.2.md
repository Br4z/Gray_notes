---
id: dlm8f1j8wu8ymhfsib7zrd2
title: '2'
desc: ''
updated: 1697157321083
created: 1696385447863
---

1. ![First problem](./assets/University/Física%20I%20+%20laboratorio/2_2-1%20Problem.jpg).

	- ¿A qué distancia, horizontalmente, desde la base del edificio, la bola golpea el suelo?

		$$
		v_x = 8 \cos{ 20 \degree } = 7,52 \frac{ \text{ m } }{ \text{ s } } \quad x(t) = x_0 + v_x t \\[10 pt]

		x(3) = 22,56 \text{ m }
		$$

	- Encuentre la altura desde la que se lanzó la bola.

		$$
		y(t) = y_0 + v_{ 0y } t + \frac{ 1 }{ 2 } g t^2 \quad y = v_{ 0y } (3) + \frac{ 1 }{ 2 } (9,81) (3)^2 = 52,32 \text{ m }
		$$

	- ¿Cuánto tarda la bola en llegar a un punto 10,0 m abajo del nivel de lanzamiento?

		$$
		10 = v_{ 0y } t + \frac{ 1 }{ 2 } g t^2 \quad 4,9t^2 + 2,74t - 10 = 0 \\[5 pt]

		t = \frac{ 2,74 \pm \sqrt{ (2,74)^2 - 4 (4,9) (-10) } }{ 2 (4,9) } \quad t_1 = 1,18 \text{ s } \quad t_2 = -1,73 \text{ s }
		$$

2. .

	- ¿Cuánto tarda la piedra en llegar al suelo?

		$$
		v_{ 0y } = 20 \sin{ 30 \degree } = 10 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		y(t) = y_0 + v_{ 0y } t - \frac{ 1 }{ 2 } g t^2 \quad -45 = 10t - 4,9t^2 \quad - 4,9t^2 + 10t + 45 = 0 \\[10 pt]

		t = \frac{ -10 \pm \sqrt{ 100 - 882 } }{ 2 (-4,9) } \quad t_1 = 4,2 \quad t_2 = -2,17
		$$

	- ¿Cuál es la rapidez de la piedra justo antes de golpear el suelo?

		$$
		v_{ x } = 20 \cos{ 30 \degree } = 17,3 \frac{ \text{ m } }{ \text{ s } } \\[5 pt]

		v_{ yf } = 10 - 9,8 (4,2) = -31,45 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		v_f = \sqrt{ (17,3)^2 + (-31,45)^2 } = 35,89 \frac{ \text{ m } }{ \text{ s } }
		$$

3. .

	- ¿Qué rapidez se necesita en el tope de la rampa para alcanzar apenas el borde de la ribera lejana?

		$$
		v_{ x } = v \cos{ 53 \degree } \frac{ \text{ m } }{ \text{ s } } \quad v_{ 0y } = v \sin{ 53 \degree } \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		y(t) = y_0 + v_{ 0y } t - \frac{ 1 }{ 2 } g t^2 \quad -15 = v_{ 0y } t - \frac{ 1 }{ 2 } (9,8) t^2 \quad (1) \\[10 pt]

		x(t) = x_0 + v_{ x } t \quad 40 = v_{ x } t \quad t = \frac{ 40 }{ v_x } \quad (2) \\[10 pt]

		\text{ Reemplazando $(2)$ en $(1)$ } -15 = v_{ 0y } \left ( \frac{ 40 }{ v_x } \right ) - \frac{ 1 }{ 2 } (9,8) \left ( \frac{ 40 }{ v_x } \right )^2 \\[10 pt]

		\text{ Dejando todo en términos de $v$ } -15 = v \sin{ 53 \degree } \left ( \frac{ 40 }{ v \cos{ 53 \degree } } \right ) - \frac{ 1 }{ 2 } (9,8) \left ( \frac{ 40 }{ v \cos{ 53 \degree } } \right )^2 \\[10 pt]

		-15 = 40 \tan{ 53 \degree } - \frac{ 7840 }{ v^2 \cos^2{ 53 \degree } } \quad 15 + 40 \tan{ 53 \degree } = \frac{ 7840 }{ v^2 \cos^2{ 53 \degree } } \\[10 pt]

		(15 + 40 \tan{ 53 \degree }) { v_0 }^2 = \frac{ 7840 }{ \cos^2{ 53 \degree } } \quad v = \sqrt{ \frac{ 7840 }{ \cos^2{ 53 \degree } (15 + 40 \tan{ 53 \degree }) } } \\[10 pt]

		v_0 \approx 17,8 \frac{ \text{ m } }{ \text{ s } }
		$$

		En general podemos llegar a la siguiente igualdad cuando se comparte el mismo $t$:

		$$
		v_0 = \sqrt{ \frac{ g x^2 }{ 2 \cos^2{ \theta } (x \tan{ \theta } - y) } }
		$$

	- ¿Si su rapidez era solo la mitad del valor obtenido anteriormente en donde cayó?

		$$
		v_0 = 8,9 \frac{ \text{ m } }{ \text{ s } } \quad v_{ 0y } = 8,9 \sin{ 53 \degree } = 7,1 \frac{ \text{ m } }{ \text{ s } } \quad v_x = 8,9 \cos{ 53 \degree } = 5,4 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		y(t) = y_0 + v_{ 0y } t - \frac{ 1 }{ 2 } g t^2 \quad -100 = 7,1t - (4,9) t^2 \quad 4,9t^2 - 7,1t - 100 = 0 \\[10 pt]

		t = \frac{ -7,1 \pm \sqrt{ (-7,1)^2 - 4 (4,9) (-100) } }{ 2 (4,9) } \quad t_1 = -3,9 \text{ s } \quad t_2 = 5,3 \text{ s } \\[10 pt]

		x(5,3) = 5,4 (5,3) = 28,6 \text{ m }
		$$

4. .

	- ¿A qué distancia del borde del granero golpea la bola el piso si no golpea otra cosa al caer?

		$$
		v_{ 0y } = 7 \sin{ 40 \degree } = -4,5 \frac{ \text{ m } }{ \text{ s } } \quad v_x = 7 \cos{ 40 \degree } = 5,4 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		-14 = -4,5t - \frac{ 1 }{ 2 } g t^2 \quad 4,9t^2 + 4,5t - 14 = 0 \\[10 pt]

		t = \frac{ 4,5 \pm \sqrt{ (4,5)^2 - 4 (4,9) (-14) } }{ 2 (4,9) } \quad t_1 = -2,21 \text{ s } \quad t_2 = 1,29 \text{ s } \\[10 pt]

		x(1,29) = 5,4 (1,29) = 7 \text{ m }
		$$

	- Un hombre de 1,9 m de estatura está parado a 4,0 m del granero. ¿Lo golpeará la bola?

		$$
		4 = 5,4 t \quad t = \frac{ 4 }{ 5,4 } = 0,74 \text{ s } \\[10 pt]

		y(t) = -4,5 (0,74) - 4,9 (0,74)^2 = -6 \text{ m }
		$$

		> Como -6 m corresponde a una altura de 8 m del suelo, por lo que la bola no alcanza a golpear al hombre.

5. .

	- ¿A qué distancia horizontal del blanco el piloto debería soltar el bote?

		$$
		v_{ 0y } = 0 \frac{ \text{ m } }{ \text{ s } } \quad v_x = 64,0 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

		-90 = - \frac{ 1 }{ 2 } g t^2 \quad t^2 = \frac{ 90 }{ -4,9 } \quad t \approx \sqrt{ 18,4 } \approx 4,3 \text{ s } \\[10 pt]

		x(4,3) = 64,0 (4,3) = 275,2 \text{ m }
		$$

6. .

	- ¿Cuáles son la magnitud y dirección del vector aceleración total para el automóvil en este instante?

		$$
		\vec{ a }_t = 0,300 \frac{ \text{ m } }{ \text{ s }^2 } \\[5 pt]

		\vec{ v }_t = 6,00 \frac{ \text{ m } }{ \text{ s } } \\[5 pt]

		R = 500 \text{ m } \\[10 pt]

		a_c = - \frac{ v^2 }{ R } = -0,072 \frac{ \text{ m } }{ \text{ s }^2 } \\[10 pt]

		\vec{ a } = \sqrt{ { \vec{ a }_t }^2 + { \vec{ a }_c }^2 } = \sqrt{ (0,300)^2 + (-0,072 )^2 } = 0,31 \frac{ \text{ m } }{ \text{ s }^2 } \\[10 pt]

		\tan{ \theta } = \frac{ \vec{ a }_c }{ \vec{ a }_t } \quad \theta = \arctan{ \frac{ -0,072 }{ 0,300 } } = -13,5 \degree
		$$

7. .

	$$
	w_i = 30 \frac{ \text{ rev } }{ \text{ min } } \frac{ 2 \pi \text{ rad } }{ 60 \text{ s } } = \pi \frac{ \text{ rad } }{ \text{ s } }
	$$

	Calcular:

	- su aceleración angular.

		$$
		w_f = w_i + \alpha t \quad \alpha = \frac{ w_f - w_i }{ t }\\[10 pt]

		\vec{ \alpha } = \frac{ -2 \pi * 30 \frac{ \text{ rad } }{ 60 \text{ s } } }{ 60 \text{ s } } = -\frac{ \pi }{ 60 } \frac{ \text{ rad } }{ \text{ s }^2 }
		\\[10 pt]
		$$

	- el número de revoluciones hasta detenerse.

		$$
		\theta(t) = w_0 t + \frac{ 1 }{ 2 } \alpha t^2 \\[10 pt]

		\theta(60) = 2 \pi * 0.5 (60) + \frac{ 1 }{ 2 } \left (-\frac{ \pi }{ 60 } \right ) (60)^2 = 2 \pi * 15 \text{ rad } = 15 \text{ rev }
		$$

	- la rapidez tangencial de un punto del borde del disco antes de empezar a frenar.

		$$
		\vec{ v } = r w = 0,1 * \pi = \frac{ \pi }{ 10 } \frac{ \text{ m } }{ \text{ s } }
		$$

	- la aceleración centrípeta, tangencial y total para un punto del borde del disco.

		$$
		\vec{ a }_t = r \alpha = 0,1 * \left ( -\frac{ \pi }{ 60 } \right ) = -\frac{ \pi }{ 600 } \frac{ \text{ m } }{ \text{ s }^2 } \\[10 pt]

		\vec{ a }_c = \frac{ (r w)^2 }{ r } = \frac{ \left ( \frac{ \pi }{ 10 } \right )^2 }{ \frac{ 1 }{ 10 } } = \frac{ 10 \pi^2 }{ 100 } = \frac{ \pi^2 }{ 10 } \frac{ \text{ m } }{ \text{ s }^2 } \\[10 pt]

		\vec{ a } = \sqrt{ \left ( -\frac{ \pi }{ 600 } \right )^2 + \left (\frac{ \pi^2 }{ 10 } \right )^2 } = 0,98 \frac{ \text{ m } }{ \text{ s }^2 }
		$$

8. .

	$$
	\vec{ \alpha } = 3,50 \frac{ \text{ rad } }{ \text{ s }^2 } \quad w_0 = 2,00 \frac{ \text{ rad } }{ \text{ s } }
	$$

	- ¿A través de qué desplazamiento angular da vueltas la rueda en 2,00 s?

		$$
		\theta(t) = w_0 t + \frac{ 1 }{ 2 } \alpha t^2 \\[10 pt]

		\theta(2) = (2,00) (2,00) + \frac{ 1 }{ 2 } (3,50) (2,00)^2 = 11 \text{ rad }
		$$

	- ¿Cuántas revoluciones dio la rueda durante este intervalo de tiempo?

		$$
		11 \text{ rad } * \frac{ \text{ rev } }{ 2 \pi \text{ rad } } = 1,75 \text{ rev }
		$$

	- ¿Cuál es la rapidez angular de la rueda en $t = 2,00 \text{ s }$?

		$$
		w_f = w_i + \alpha t \quad w(2,00) = 2,00 + (3,50) (2,00) = 9,50 \frac{ \text{ rad } }{ \text{ s } }
		$$
