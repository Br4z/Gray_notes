---
id: 96zr7fxv8uymh7ulwdybar2
title: '3'
desc: ''
updated: 1700318044256
created: 1697392826399
---

1. ![First problem](./assets/University/Física%20I%20+%20laboratorio/2_3-1%20Problem.jpg).

	- Si supone que el sistema está en equilibrio, encuentre las tensiones $T_1$, $T_2$ y $T_3$ en los alambres.

		$$
		\sum{ \vec{ F } } = 0 \\[10 pt]

		T_3 - w = 0 \quad T_3 = w = 325 \text{ N }
		$$

		> Todo ocurre en sus componentes de $y$.

		$$
		\sum{ \vec{ F } } = 0 \quad \sum{ \vec{ F_x } } = 0 \quad \sum{ \vec{ F_y } } = 0 \\[10 pt]

		\sum{ \vec{ F_x } } = -T_1 \cos{ \theta_1 } + T_2 \cos{ \theta_2 } = 0 \quad (1) \\[10 pt]

		\sum{ \vec{ F_y } } = T_1 \sin{ \theta_1 } + T_2 \sin{ \theta_2 } - T_3 = 0 \quad (2) \\[10 pt]

		\text{ De $(1)$ despejamos $T_2$ } \quad T_2 = \frac{ T_1 \cos{ \theta_1 } }{ \cos{ \theta_2 } } \quad (3) \\[10 pt]

		\text{ Reemplazamos $(3)$ en $(2)$ } \quad T_1 \sin{ \theta_1 } + \left ( \frac{ T_1 \cos{ \theta_1 } }{ \cos{ \theta_2 } } \right ) \sin{ \theta_2 } - T_3 = 0 \\[10 pt]

		T_1 \sin{ 60,0 \degree } + \left ( \frac{ T_1 \cos{ 60,0 \degree } }{ \cos{ 25,0 \degree } } \right ) \sin{ 25,0 \degree } - 325 = 0 \\[10 pt]

		T_1 = 295,7 \text{ N } \quad T_2 = \frac{ (295,7 ) \cos{ 60,0 \degree } }{ \cos{ 25,0 \degree } } = 163,24 \text{ N }
		$$

2. ![Second problem](./assets/University/Física%20I%20+%20laboratorio/2_3-2%20Problem.jpg).

	- Si el ángulo $\theta = 10,0 \degree$, calcule la tensión en la cuerda.

		Como está en la mitad de la cuerda $T_1 = T_2$.

		$$
		\sum{ \vec{ F_y } } = 0 \\[10 pt]

		T_1 \sin{ \theta } + T_2 \sin{ \theta } - w = 0 \quad 2 T_1 \sin{ \theta } - w = 0 \quad T_1 = \frac{ w }{ 2 \sin{ \theta } } \\[10 pt]

		T_1 = \frac{ 9 * 9.8 }{ 2 \sin{ 10 \degree } } = 2.540 \text{ N }
		$$

	- ¿Qué valor mínimo puede tener $\theta$ sin que se rompa la cuerda?

		$$
		T_1 = \frac{ 9 * 9.8 }{ 2 \sin{ \theta } } = 2,5 * 10^4 \\[10 pt]

		\theta = \arcsin{ \frac{ 9 * 9.8 }{ 2 * 2,5 * 10^4 } } = 1,01 \degree
		$$

3. ![Third problem](./assets/University/Física%20I%20+%20laboratorio/2_3-3%20Problem.jpg).

	- Encuentre la magnitud de la aceleración de los dos objetos y la tensión en la cuerda.

		$$
		\text{ Para $m_1$ tenemos } \quad \sum{ \vec{ F_y } } = m_1 a \quad T - w_1 = m_1 a \quad (1) \\[10 pt]

		\text{ Para $m_2$ tenemos } \quad \sum{ \vec{ F_x } } = m_1 a \quad w_2 \sin{ \theta } - T = m_2 a \quad (2) \\[10 pt]

		\text{ Sumando $(1)$ y $(2)$ } \quad w_2 \sin{ \theta } - w_1 = a (m_1 + m_2) \quad a = \frac{ w_2 \sin{ \theta } - w_1 }{ m_1 + m_2 } \\[10 pt]
		$$

		Para hallar la tensión, podemos usar tanto $(1)$ como $(2)$.

		> Una vez hemos hallado la aceleración del sistema.

		$$
		(1) \quad T = m_1 a + w_1 \quad (2) \quad T = \sin{ \theta } - m_2 a
		$$

4. ![Fourth problem](./assets/University/Física%20I%20+%20laboratorio/2_3-4%20Problem.jpg).

	- Encuentre la aceleración del automóvil, si supone que la pista no tiene fricción.

		$$
		\sum{ \vec{ F_y } } = 0 \quad \sum{ \vec{ F_x } } = m a \\[10 pt]

		\sum{ \vec{ F_x } } = w \sin{ \theta } = m a \quad a = \frac{ w \sin{ \theta } }{ m } = g \sin{ \theta }
		$$

	- Considere que el automóvil se libera desde el reposo en lo alto del plano y que la distancia desde la defensa frontal del automóvil hasta el fondo del plano inclinado es $d$. ¿Cuánto tarda la defensa frontal en llegar al fondo de la colina, y cuál es la rapidez del automóvil cuando llega ahí?

		$$
		x_0 = 0 \quad v_0 = 0 \\[10 pt]

		d = \frac{ 1 }{ 2 } a t^2 \quad t = \sqrt{ \frac{ 2 d }{ a } } = \sqrt{ \frac{ 2 d }{ g \sin{ \theta } } }
		$$

5. .

	- Dibuje un diagrama de cuerpo libre para la carga de ladrillos y otro para el contrapeso.

		- $m_1$.

			![M_1 free body diagram](./assets/University/Física%20I%20+%20laboratorio/2_3-5%20M1-free-body-diagram.jpg).

		- $m_2$.

			![M_2 free body diagram](./assets/University/Física%20I%20+%20laboratorio/2_3-6%20M2-free-body-diagram.jpg).

	- ¿Qué magnitud tiene la aceleración hacia arriba de la carga de ladrillos?

		- $m_1$.

			$$
			\sum{ \vec{ F_y } } = m_1 a \\[10 pt]

			\sum{ \vec{ F_y } } = T - m_1 g = m_1 a \quad (1)
			$$

		- $m_1$.

			$$
			\sum{ \vec{ F_y } } = m_2 a \\[10 pt]

			\sum{ \vec{ F_y } } = m_2 g - T = m_1 a \quad (2)
			$$

		$$
		\text{ Sumando $(1)$ y $(2)$ } \quad m_2 g - m_1 g = a (m_1 + m_2) \quad a = \frac{ m_2 g - m_1 g }{ m_1 + m_2 } = \frac{ g (m_2 - m_1) }{ m_1 + m_2 } \quad (3) \\[10 pt]

		a = \frac{ 9,8 (28,0 - 15,0) }{ 15,0 + 28,0 } = 2,96 \frac{ \text{ m } }{ \text{ s } }
		$$

	- ¿Qué tensión hay en la cuerda mientras la carga se mueve? Compare esa tensión con el peso de la carga de ladillos y con el del contrapeso.

		$$
		\text{ Reemplazando $(3)$ em $(1)$ } \quad T - m_1 g = m_1 \frac{ g (m_2 - m_1) }{ m_1 + m_2 } \\[10 pt]

		T = m_1 g \frac{ m_2 - m_1 }{ m_1 + m_2 } + m_1 g = m_1 g \left ( \frac{ m_2 - m_1 }{ m_1 + m_2 } + 1 \right ) = m_1 g \left ( \frac{ 2 m_2 }{ m_1 + m_2 } \right ) = \frac{ 2 g m_1 m_2 }{ m_1 + m_2 } \\[10 pt]

		T = \frac{ 2 (9,8) (15,0) (28,0) }{ 15,0 + 28,0 } = 191,4 \text{ N }
		$$

		$$
		T = \frac{ 191,4 } { (15,0) (9,8) } w_1 = 0,7 w_1 \\[10 pt]

		T = \frac{ 191,4 } { (28,0) (9,8) } w_2 = 1,3 w_2
		$$

6. ![Sixth problem](./assets/University/Física%20I%20+%20laboratorio/2_3-7%20Problem.jpg).

	¿Qué magnitud tiene la fuerza normal ejercida sobre el coche por las paredes del cilindro

	- en el punto $A$ (parte inferior del círculo vertical)?

		$$
		\sum{ \vec{ F_y } } = m \alpha = m \frac{ v^2 }{ R } \\[10 pt]

		\sum{ \vec{ F_y } } = N - m g = m \frac{ v^2 }{ R } \quad N = m \left ( \frac{ v^2 }{ R } + g \right ) = (1,6) \left ( \frac{ (12,0)^2 }{ (5,0) } + (9,8) \right ) = 61,8 \text{ N }
		$$

	- en el punto B (parte superior del círculo vertical)?

		$$
		\sum{ \vec{ F_y } } = m \alpha = m \frac{ v^2 }{ R } \\[10 pt]

		\sum{ \vec{ F_y } } = N + m g = m \frac{ v^2 }{ R } \quad N = m \left ( \frac{ v^2 }{ R } - g \right ) = (1,6) \left ( \frac{ (12,0)^2 }{ (5,0) } - (9,8) \right ) = 30,4 \text{ N }
		$$
