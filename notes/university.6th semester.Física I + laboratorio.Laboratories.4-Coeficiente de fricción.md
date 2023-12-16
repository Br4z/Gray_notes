---
id: elz06dqa1gao9g6npqxjo37
title: 4-Coeficiente de fricción
desc: ''
updated: 1699298642415
created: 1699234500782
---

## Consideraciones teóricas

$$
f = \mu N
$$

El coeficiente $\mu$ se refiere al tipo de fricción, ya sea estático o cinético.

### Determinación de $\mu_s$ al encontrar el ángulo en que inicia el movimiento en un plano inclinado

![Assembly for finding the coefficient of static friction on an inclined plane](./assets/University/Física%20I%20+%20laboratorio/3_4-1%20Static_friction_coefficient%20_inclined_plane.jpg)

El proceso comienza con un cuerpo que se encuentra sobre una superficie rugosa horizontal. Luego, se incrementa el ángulo de inclinación, lo que produce una componente del peso paralela a la superficie que se contrarresta por la fuerza de fricción. La superficie se eleva en un ángulo $\theta$ hasta que el cuerpo se desliza hacia abajo.

![Assembly for finding the coefficient of static friction on an inclined plane](./assets/University/Física%20I%20+%20laboratorio/3_4-2%20Static_friction_coefficient%20_inclined_plane.jpg)

$$
\sum{ \vec{ F } } = \vec{ N } + \vec{ w } + \vec{ f_s } = 0 \\[10 pt]

\sum{ \vec{ F }_x } = f_s - m g \sin{ \theta } = 0 \quad f_s = m g \sin{ \theta } \\[10 pt]

\sum{ \vec{ F }_y } = N - m g \cos{ \theta } = 0 \quad N = m g \cos{ \theta } \\[10 pt]

\text{ Como $f_s = \mu_s N$ } \quad f_s = \mu_s m g \cos{ \theta }
$$

A medida que el ángulo $\theta$ aumenta, la componente del peso paralela a la superficie ($m g \sin{ \theta }$), también aumenta. Esta componente es contrarrestada por la fuerza de fricción $f_s$. El sistema permanece en reposo mientras $m g \sin{ \theta } \leq f_s$, es decir, $m g \sin{ \theta } \leq \mu_s m g \cos{ \theta }$.

En el caso límite en el que $m g \sin{ \theta } = \mu_s m g \cos{ \theta }$, encontraremos que $\mu_s = \tan{ \theta }$.

> Este caso límite ocurre con el mínimo ángulo que inicia el movimiento.

### Determinación de $\mu_s$ al encontrar la masa que inicia el movimiento en un plano horizontal

![Assembly for finding the coefficient of static friction on an horizontal plane](./assets/University/Física%20I%20+%20laboratorio/3_4-3%20Static_friction_coefficient%20_horizontal_plane.jpg)

En este caso, se ajusta la masa suspendida $m_2$ hasta un valor máximo que garantice que el sistema permanece en reposo. Tanto la tensión de la cuerda como la componente del peso paralela a la superficie son contrarrestadas por la fuerza de fricción.

- $m_1$.

	$$
	\sum{ \vec{ F } } = \vec{ N } + \vec{ w } + \vec{ T } + \vec{ f_s } = 0 \\[10 pt]

	\sum{ F_x } = T - f_s = 0 \quad \sum{ F_y } = N - w = 0 \\[5 pt]

	N = w \quad f_s = T = \mu_s N = \mu_s m g \quad (1)
	$$

- $m_2$.

	$$
	\sum{ \vec{ F } } = \vec{ w } + \vec{ T } = 0 \\[10 pt]

	\sum{ F_y } = T - m g = 0 \\[5 pt]

	T = m g \quad (2)
	$$

Debido a que la masa de la cuerda es despreciable, la cuerda es inextensible, la polea no rota y la fricción en el rodamiento es despreciable, se puede considerar que la tensión en la cuerda es igual en ambos extremos.

El sistema permanece en reposo mientras $T \leq f_s$, es decir, $m_2 g \leq \mu_s m_1 g$. En el caso límite en el que $m_2 g = \mu_s m_1 g$, encontraremos que:

$$
\text{ Reemplazando $(2)$ en $(1)$ } \quad m_2 g = \mu_s m_1 g \\[10 pt]

\mu_s = \frac{ m_2 }{ m_1 }
$$

> Este caso límite ocurre con la mínima masa en $m_2$ que inicia el movimiento.

### Coeficiente de fricción cinético

### Determinación de $\mu_k$ al encontrar la aceleración constante ascendente en el plano inclinado

![Assembly for finding the coefficient of kinetic friction on an inclined plane](./assets/University/Física%20I%20+%20laboratorio/3_4-4%20Kinetic_friction_coefficient%20_inclined_plane.jpg)

- $m_1$.

	$$
	\sum{ \vec{ F } } = \vec{ N } + \vec{ w } + \vec{ T } + \vec{ f_k } = m \vec{ a } \\[10 pt]

	\sum{ F_x } = T - m g \sin{ \theta } - f_k = m a \quad (1) \quad \sum{ F_y } = N - m g \cos{ \theta } = 0 \\[5 pt]

	N = m g \cos{ \theta } \quad f_k = \mu_k N = \mu_k m g \cos{ \theta } \quad (2)
	$$

- $m_2$.

	$$
	\sum{ \vec{ F } } = \vec{ T } + \vec{ w } = m a \\[10 pt]

	\sum{ F_y } = m g - T = m a \\[5 pt]

	T = m (g - a) \quad (3)
	$$

Debido a las características del sistema, diremos que los dos cuerpos ($m_1$ y $m_2$) comparten tanto la aceleración como la tensión.

$$
\text{ Reemplazando $(2)$ y $(3)$ en $(1)$ } \quad m_2 (g - a) - m_1 g \sin{ \theta } - \mu_k m_1 g \cos{ \theta } = m_1 a \\[10 pt]

\mu_k = \frac{ m_2 (g - a) - m_1 (a + g \sin{ \theta }) }{ m_1 g \cos{ \theta } } = \frac{ (m_2 - m_1 \sin{ \theta }) g - (m_1 + m_2) a }{ m_1 g \cos{ \theta } }
$$

### Determinación de $u_k$ al encontrar la aceleración constante en el plano horizontal

Para el caso del plano horizontal, simplemente hacemos $\theta = 0$ en la ecuación para el plano inclinado.

$$
\mu_k = \frac{ m_2 g - (m_1 + m_2) a }{ m_1 g }
$$
