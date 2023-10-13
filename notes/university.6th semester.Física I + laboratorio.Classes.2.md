---
id: hcifjbuqfqw25p3zz1evy53
title: '2'
desc: ''
updated: 1696983560491
created: 1695501972725
---

## Week 5

### Movimiento en 2D

- Desplazamiento.

	$$
	\vec{ r }_1 = r_{ 1x } \hat{ \imath } + r_{ 1y } \hat{ \jmath } \quad \vec{ r }_2 = r_{ 2x } \hat{ \imath } + r_{ 2y } \hat{ \jmath } \\[10 pt]

	\vec{ r } = (r_{ 1x } - r_{ 2x }) \hat{ \imath } + (r_{ 1y } - r_{ 2y }) \hat{ \jmath }
	$$

	![Displacement](./assets/University/Física%20I%20+%20laboratorio/1_2-1%20Displacement.jpg)

- Velocidad media.

	$$
	\vec{ v }_m = \frac{ \Delta{ \vec{ r } } }{ \Delta{ t } } = \frac{ \vec{ r }_2 - \vec{ r }_1 }{ t_2 - t_1 } = \frac{ (r_{ 1x } - r_{ 2x }) \hat{ \imath } + (r_{ 1y } - r_{ 2y }) \hat{ \jmath } }{ t_2 - t_1 }
	$$

- Velocidad instantánea.

	$$
	\vec{ v } = \lim_{ \Delta{ t } \to 0 }{ \frac{ \Delta{ \vec{ r } } }{ \Delta{ t } } } = \frac{ d x_x }{ dt } \hat{ \imath } + \frac{ d x_y }{ dt } \hat{ \jmath }
	$$

	![Instantaneous velocity](./assets/University/Física%20I%20+%20laboratorio/1_2-2%20Instantaneous_velocity.jpg)

- Rapidez.

	$$
	| \vec{ v } | = \sqrt{ { v_x }^2 + { v_y }^2 }
	$$

- Aceleración media.

	$$
	\vec{ a }_m = \frac{ \Delta{ \vec{ v } } }{ \Delta{ t } } = \frac{ \vec{ v }_2 - \vec{ v }_1 }{ t_2 - t_1 } = \frac{ (v_{ 1x } - v_{ 2x }) \hat{ \imath } + (v_{ 1y } - v_{ 2y }) \hat{ \jmath } }{ t_2 - t_1 }
	$$

- Aceleración instantánea.

	$$
	\vec{ a } = \frac{ d v_x }{ dt } \hat{ \imath } + \frac{ d v _y }{ dt } \hat{ \jmath }
	$$

Estas definiciones se pueden extrapolar para el movimiento en **3D**, pues, solo se tendría que considerar la componente $\hat{ k }$.

## Movimiento parabólico

![Parabolic movement](./assets/University/Física%20I%20+%20laboratorio/1_2-3%20Parabolic_movement.jpg)

- MRU.

	$$
	x = x_0 + v_{ 0x } t \\[5 pt]

	x = x_0 + | v_0 | \cos{ \theta } t \quad (1) \\[10 pt]

	v_x = \frac{ d x }{ dt } = | v_0 | \cos{ \theta } \quad (2) \\[10 pt]

	a_x = \frac{ d v_x }{ dt } = 0
	$$

- MRUA.

	$$
	y = y_0 + v_{ 0y } t + \frac{ 1 }{ 2 } a t^2 \\[5 pt]

	y = y_0 + | v_0 | \sin{ \theta } t - \frac{ 1 }{ 2 } g t^2 \quad (3) \\[10 pt]

	v_y = \frac{ d y }{ dt } = | v_0 | \sin{ \theta } - g t \quad (4) \\[10 pt]

	a_y = \frac{ d v_y }{ dt } = -g
	$$

### Altura máxima y alcance máximo

Se puede determinar el $y_{ \text{ max } }$ al notar que, en el punto más alto del proyectil, $v_y = 0 \frac{ \text{ m } }{ \text{ s } }$.

$$
\text{ Despejando $t$ de $(4)$ } \quad t_{ \text{ s } } = \frac{ v_0 \sin{ \theta } }{ g } \quad (5) \\[10 pt]
$$

> Nos referiremos a este tiempo como tiempo de subida y además encontraremos que el tiempo de vuelo (total) es igual a dos veces el tiempo de subida $t_T = 2t_s$.

$$
\text{ Reemplazando $(5)$ en $(3)$ } \quad y_{ \text{ max } } = v_0 \sin{ \theta } \left ( \frac{ v_0 \sin{ \theta } }{ g } \right ) - \frac{ 1 }{ 2 } g \left ( \frac{ v_0 \sin{ \theta } }{ g } \right )^2 \\[10 pt]

y_{ \text{ max } } = \frac{ { { v_0 }^2 \sin^2{ \theta } } }{ 2g }
$$

Remplazando $t_T$ en $(1)$ encontraremos el alcance máximo ($R$):

$$
x = x_0 + v_0 \cos{ \theta } \left ( \frac{ v_0 \sin{ \theta } }{ g } \right ) \quad R = \frac{ 2 { v_0 }^2 \sin{ \theta } }{ g }
$$

> $\sin{ 2\theta } = 2 \cos{ \theta } \sin{ \theta }$.

### Ecuación de la trayectoria

Conocemos totalmente la ecuación de la trayectoria de un proyectil si conocemos $v_i$ y $\theta$

$$
\text{ Despejando $t$ de $(1)$ } \quad t = \frac{ x - x_0 }{ v_0 \cos{ \theta } } = \frac{ X }{ v_0 \cos{ \theta } } \quad (6) \\[10 pt]

\text{ Reemplazando $(6)$ en $(3)$ } \quad y = y_0 + v_0 \sin{ \theta } \left ( \frac{ X }{ v_0 \cos{ \theta } } \right ) - \frac{ 1 }{ 2 } g \left ( \frac{ X }{ v_0 \cos{ \theta } } \right )^2 \\[10 pt]

y = y_0 + \tan{ \theta } X - \frac{ g }{ 2 { v_0 }^2 \cos^2{ \theta } } X^2
$$

### Problema (movimiento parabólico)

1. Usted está jugando Angry Birds y quiere derribar a un cerdo que se encuentra en una torre de cajas situada a 7 m de distancia y a una altura de 5 m. Si la resortera tiene una altura de 0,2 m y el tiempo de vuelo es de 1,45 segundos. ¿Con qué velocidad inicial y a qué ángulo con respecto a la horizontal se debe lanzar un pájaro para dar en el blanco?

	![Parabolic movement problem](./assets/University/Física%20I%20+%20laboratorio/1_2-4%20Parabolic%20movement%20problem.jpg)

	Lo recomendable es primero anotar todos los datos que nos da y nos pide el problema.

	$$
	x_f = 7 \text{ m } \\[5 pt]

	y_f = 5 \text{ m } \\[5 pt]

	y_0 = 0,2 \text{ m } \\[5 pt]

	t_T = 1,45 \text{ s } \\[5 pt]

	a = 9,8 \frac{ \text{ m } }{ \text{ s }^2 } \\[10 pt]

	\text{ Despejando $v_x$ de $x = x_0 + v_{ 0x } t$ } \quad v_x = \frac{ 7 }{ 1,45 } = 4,83 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

	\text{ Despejando $v_{ 0y }$ de $y = y_0 + v_{ 0y } t + \frac{ 1 }{ 2 } a t^2$ } \quad v_{ 0y } = \frac{ 5 - 0,2 + 4,9 * { 1,45 }^2 }{ 1,45 } = 10,42 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

	v_0 = \sqrt{ { 4,83 }^2 + { 10,42 }^2 } = 11,49 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

	v_0 \cos{ \theta } = v_x \quad \theta = \arccos{ \frac{ v_x }{ v_0 } } = \arccos{ \frac{ 4,83 }{ 11,49 } } \approx 65,13 \degree
	$$

## Movimiento circular

### Uniforme

Es el movimiento que realiza un objeto describiendo una trayectoria circular con rapidez tangencial constante.

> Una característica de este movimiento es que tiene una aceleración angular constante.

Este movimiento tiene medidas "equivalentes" al movimiento rectilíneo.

|                           Movimiento rectilíneo                           |                           Movimiento circular uniforme                           |
|:-------------------------------------------------------------------------:|:--------------------------------------------------------------------------------:|
|                  Desplazamiento $\Delta{ \vec{ x } }$ m                   |                  Desplazamiento angular $\Delta{ \theta }$ rad                   |
|    Velocidad promedio $\bar{ v }$ $\frac{ \text{ m } }{ \text{ s } }$     |       Velocidad promedio $\bar{ w }$ $\frac{ \text{ rad } }{ \text{ s } }$       |
|   Velocidad instantánea $\vec{ v }$ $\frac{ \text{ m } }{ \text{ s } }$   |     Velocidad instantánea $\vec{ w }$ $\frac{ \text{ rad } }{ \text{ s } }$      |
|  Aceleración promedio $\bar{ a }$ $\frac{ \text{ m } }{ \text{ s }^2 }$   |  Aceleración promedio $\bar{ \alpha }$ $\frac{ \text{ rad } }{ \text{ s }^2 }$   |
| Aceleración instantánea $\vec{ a }$ $\frac{ \text{ m } }{ \text{ s }^2 }$ | Aceleración instantánea $\vec{ \alpha }$ $\frac{ \text{ rad } }{ \text{ s }^2 }$ |

---

- Velocidad tangencial: es una magnitud vectorial y se define como la velocidad tangente a la trayectoria, se representa como $\vec{ v }$ y sus unidades en el SI son $\frac{ \text{ m } }{ \text{ s } }$.

- Rapidez tangencial: es el módulo de la velocidad tangencial, es decir, un escalar que indica la longitud de arco que el objeto recorre por una unidad de tiempo, se representa como $v$ y sus unidades en el SI son $\frac{ \text{ m } }{ \text{ s } }$.

Si el movimiento que realiza un objeto describiendo una trayectoria circular tiene rapidez constante, pero cambia su dirección, entonces aparece una **aceleración**.

> Decimos entonces que tiene aceleración porque las velocidades no son iguales (aunque su módulo lo sea), pues en un vector también tiene una dirección asociada.

### Aceleración centrípeta

![Uniform circular movement](./assets/University/Física%20I%20+%20laboratorio/1_2-5%20Uniform_circular_movement.jpg)

Primero diremos que dos triángulos son semejantes si el ángulo entre cualquiera de los lados es el mismo para ambos triángulos y si la relación de las longitudes de dichos lados es la misma. Identificando además que se forma el mismo ángulo $\theta$ en el triángulo $ABC$ y $DFG$.

![Demonstration of the centripetal acceleration](./assets/University/Física%20I%20+%20laboratorio/1_2-6%20Demonstration%20_centripetal_acceleration.jpg)

$$
\frac{ \Delta{ \vec{ v } } }{ v } = \frac{ \Delta{ \vec{ s } } }{ R } \quad \Delta{ \vec{ v } } = \frac{ v }{ R } \Delta{ \vec{ s } } \quad (1) \\[10 pt]

\text{ Dividimos ambos lados de $(1)$ por $\Delta{ t }$ } \quad \frac{ \Delta{ \vec{ v } } }{ \Delta{ t } } = \frac{ v }{ R } \frac{ \Delta{ \vec{ s } } }{ \Delta{ t } } \\[10 pt]

a_c = \frac{ v }{ R } \frac{ \Delta{ \vec{ s } } }{ \Delta{ t } } = \frac{ v }{ R } v = \frac{ v^2 }{ R }
$$

### Uniformemente acelerado

Es el movimiento que realiza un objeto describiendo una trayectoria circular con rapidez tangencial uniformemente acelerada.

Calcularemos entonces la aceleración en cada punto como:

$$
\vec{ a } = \vec{ a }_c + \vec{ a }_t = -\frac{ v^2 }{ R } + \frac{ d v }{ dt } \\[10 pt]

\text{ Su magnitud entonces se define como } \sqrt{ { \vec{ a }_c }^2 + { \vec{ a }_t }^2 }
$$

---

La posición de la partícula se puede expresar en términos del ángulo $\theta$ y el arco de longitud $s$ recorrido por la partícula:

$$
\left \{ \begin{array}{cc}
	2 \pi r   & 2 \pi \\
	\vec{ s } & \theta
\end{array} \right . \quad \vec{ s } = \frac{ 2 \pi r \theta }{ 2 \pi } \\[10 pt]

\vec{ s } = r \theta
$$

- Desplazamiento angular: el cambio en el ángulo $\theta$ formado por la partícula al describir un arco de longitud $s$.

	$$
	\Delta{ \vec{ \theta } } = \theta_f + \theta_i
	$$

- Velocidad angular promedio.

	$$
	\bar{ w } = \frac{ \Delta{ \theta } }{ \Delta{ t } } = \frac{ \theta_f - \theta_i }{ t_f - t_i } \frac{ \text{ rad } }{ \text{ s } }
	$$

- Velocidad angular instantánea.

	$$
	\vec{ w } = \frac{ d \theta }{ dt } \frac{ \text{ rad } }{ \text{ s } }
	$$

- Aceleración angular promedio.

	$$
	\bar{ \alpha } = \frac{ \Delta{ \vec{ w } } }{ \Delta{ t } } = \frac{ w_f - w_i }{ t_f - t_i } \frac{ \text{ rad } }{ \text{ s }^2 }
	$$

- Aceleración angular instantánea.

	$$
	\vec{ \alpha } = \frac{ d w }{ dt } \frac{ \text{ rad } }{ \text{ s }^2 }
	$$

---

Existen relaciones entre las magnitudes angulares con las lineales.

- Velocidad lineal y velocidad angular.

	$$
	\vec{ v } = \frac{ d s }{ dt } = \frac{ d (r \theta) }{ dt } = r \frac{ d \theta }{ dt } = r w
	$$

- Aceleración tangencial y aceleración angular.

	$$
	\vec{ a_t } = \frac{ d v }{ dt } = \frac{ d (r w) }{ dt } = r \frac{ d w }{ dt } = r \alpha
	$$

- Aceleración centrípeta y velocidad angular.

	$$
	\vec{ a }_c = \frac{ v^2 }{ r } = r w^2
	$$

---

- Periodo: tiempo que tarda una partícula en dar una vuelta completa.

	$$
	w = \frac{ \Delta{ \theta } }{ \Delta{ t } } = \frac{ 2 \pi }{ T } \quad T = \frac{ w }{ 2 \pi } \text{ s }
	$$

- Frecuencia: el número de vueltas que da una partícula en una unidad de tiempo.

	$$
	f = \frac{ 1 }{ T } \text{ Hz }
	$$

## Week 6

### Movimiento semi parabólico (problema)

![Semi-parabolic movement problem](./assets/University/Física%20I%20+%20laboratorio/1_2-7%20Semi-parabolic%20movement%20problem.jpg)

Un tubo se encuentra a 3 m de altura del suelo e impulsa agua a una velocidad $v_0$ determinada, se sabe que el agua cae a una distancia horizontal de 6 m desde el extremo del tubo, según el gráfico dado.

> Empezamos con una $v_{ 0y } = 0$.

- ¿Cuál es el valor de la velocidad inicial?

	Podemos empezar hallando el tiempo:

	$$
	-3 = -4,9 t^2 \quad t = \sqrt{ \frac{ 3 }{ 4,9 } } = 0,78 \text{ s } \\[10 pt]

	x = x_0 + v_x t \quad v_x = \frac{ x - x_0 }{ t } = \frac{ 6 }{ 0,78 } = 7,68 \text{ m } \\[10 pt]

	v = \sqrt{ (0)^2 + (7,68)^2 } = v_x = 7,68 \frac{ \text{ m } }{ \text{ s } }
	$$

- ¿Cuál es la velocidad con la que impacta el agua en el piso?

	$$
	v_y(7,68) = -9,8 (7,68) = -7,64 \frac{ \text{ m } }{ \text{ s } }
	$$

- Si se duplica la velocidad con la se expulsa el agua. ¿Qué ocurre con el alcance máximo?

	$$
	v_0 = 2v_0 = 17,3 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

	x(7,68) = 17,3 (7,68) = 73,2 \text{ m }
	$$

### Movimiento circular (problemas)

1. Calcular la rapidez orbital de la traslación terrestre alrededor del sol y la aceleración centrípeta correspondiente.

	$$
	t = 1 \text{ año } \quad R = 1,496 * 10^{ 11 } \text{ m } \\[10 pt]

	v = \frac{ 2 \pi (1,496 * 10^{ 11 }) }{ 1 \text{ año } } \frac{ 1 \text{ año } }{ 3,159 * 10^{ 75 } } = 29.783,4 \frac{ \text{ m } }{ \text{ s } } \\[10 pt]

	a_c = -\frac{ (29.783,4)^2 }{ 1,496 * 10^{ 11 } } = -5,96 * 10^{ -3 } \frac{ \text{ m } }{ \text{ s }^2 }
	$$

2. Una rueda de 90 cm de diámetro parte del reposo, si a los 20 s alcanza una velocidad de $100 \frac{ \text{ rad } }{ \text{ s } }$, calcule su aceleración angular y desplazamiento angular en ese momento.

$$
\alpha = \frac{ 100 - 0 }{ 20 - 0 } = 5 \frac{ \text{ rad } }{ \text{ s }^2 } \\[10 pt]

\Delta{ \theta } = \theta_f - \theta_i = w_0 t + \frac{ 1 }{ 2 } \alpha t^2 \quad \Delta{ \theta } = 2,5 (20)^2 = 1.000 \text{ rad }
$$
