---
id: 9vnwhogstuchoue2sxqb5sp
title: 3-Fuerzas concurrentes
desc: ''
updated: 1698091272668
created: 1697490236202
---

El montaje experimental es el siguiente:

![Front view of the experimental setup](./assets/University/Física%20I%20+%20laboratorio/3_3-1%20Front_view_experimental_setup.jpg)

![Free body diagrams](./assets/University/Física%20I%20+%20laboratorio/3_3-2%20Free_body_diagrams.jpg)

$$
\sum{ \vec{ F }_x } = -F_1 \cos{ \theta_1 } + F_2 \cos{ \theta_2 } = 0 \quad (1) \\[10 pt]

\sum{ \vec{ F }_y } = F_1 \sin{ \theta_1 } + F_2 \sin{ \theta_2 } - F_3 = 0 \quad (2)
$$

Las magnitudes de las tres fuerzas están dadas por los pesos de las masas correspondientes:

$$
F_1 = m_1 g \quad F_2 = m_2 g \quad F_3 = m_3 g \quad (3)
$$

---

Cuando $\theta_1 + \theta_2 = 90$ $\vec{ F }_1$ y $\vec{ F }_2$ son perpendiculares, por lo tanto, la resultante de las fuerzas (suma vectorial) es siempre vertical, igual a $-\vec{ F }_3$.

$$
{ m_1 }^2 + { m_2 }^2 = { m_3 }^2
$$

1. Deducción de las ecuaciones.

	$$
	\cos^2{ \theta } + \sin^2{ \theta } = 1 \quad \cos^2{ \theta } = 1 - \sin^2{ \theta } \quad \cos{ \theta } = \sqrt{ 1 - \sin^2{ \theta } } \\[10 pt]

	\text{ Reemplazando en $(1)$ } \quad -F_1 \sqrt{ 1 - \sin^2{ \theta_1 } } + F_2 \cos{ \theta_2 } = -m_1 \sqrt{ 1 - \sin^2{ \theta_1 } } + m_2 \cos{ \theta_2 } = 0 \\[10 pt]

	\sqrt{ 1 - \sin^2{ \theta_1 } } = \frac{ m_2 \cos{ \theta_2 } }{ m_1 } \quad \sin{ \theta_1 } = \sqrt{ 1 - \frac{ { m_2 }^2 \cos^2{ \theta_2 } }{ { m_1 }^2 } } \quad (4)\\[10 pt]

	\text{ Reemplazando $(4)$ en $(2)$ } \quad F_1 \sqrt{ 1 - \frac{ { m_2 }^2 \cos^2{ \theta_2 } }{ { m_1 }^2 } } + F_2 \sin{ \theta_2 } - F_3 = m_1 \sqrt{ 1 - \frac{ { m_2 }^2 \cos^2{ \theta_2 } }{ { m_1 }^2 } } + m_2 \sin{ \theta_2 } - m_3 = 0 \\[10 pt]

	{ m_1 }^2 \left ( 1 - \frac{ { m_2 }^2 \cos^2{ \theta_2 } }{ { m_1 }^2 } \right ) = (m_3 - m_2 \sin{ \theta_2 })^2 \quad { m_1 }^2 -{ m_2 }^2 \cos^2{ \theta_2 } = { m_3 }^2 - 2 m_3 m_2 \sin{ \theta_2 } + m_2^2 \sin{ \theta_2 }^2 \\[10 pt]

	{ m_1 }^2 - { m_2 }^2 (1 - \sin^2{ \theta_2 }) = { m_3 }^2 - 2 m_3 m_2 \sin{ \theta_2 } + m_2^2 \sin{ \theta_2 }^2 \quad \sin{ \theta_2 } = \frac{ { m_1 }^2 - { m_2 }^2 - { m_3 }^2 }{ -2 m_3 m_2 } = \frac{ -{ m_1 }^2 + { m_2 }^2 + { m_3 }^2 }{ 2 m_3 m_2 } \\[10 pt]

	\theta_2 = \arcsin{ \frac{ -{ m_1 }^2 + { m_2 }^2 + { m_3 }^2 }{ 2 m_3 m_2 } } \\[10 pt]
	$$

	De forma similar llegamos a $\theta_1$, despejando para $\sin{ \theta_2 }$ en $(1)$.

	> Después de reemplazar $\cos{ \theta_2 } = \sqrt{ 1 - \sin^2{ \theta_2 } }$.

	$$
	\theta_1 = \arcsin{ \frac{ { m_3 }^2 + { m_1 }^2 - { m_2 }^2 }{ 2 m_1 m_3 } } \\[10 pt]
	$$

2. Elija valores para las masas.

	- $m_1 = m_2 \neq m_3$.

		$$
		m_1 = m_2 = 100 \text{ g } \quad m_3 = 150 \text{ g } \\[10 pt]

		\theta_1 = \arcsin{ \frac{ (150)^2 + (100)^2 - (100)^2 }{ 2 (100) (150) } } = 45,6 \degree \\[10 pt]

		\theta_2 = \arcsin{ \frac{ (150)^2 + (100)^2 - (100)^2 }{ 2 (100) (150) } } = 45,6 \degree
		$$

	- $m_1 \neq m_2 \neq m_3$.

		$$
		m_1 = 100 \text{ g } \quad m_2 = 150 \text{ g } \quad m_3 = 200 \text{ g } \\[10 pt]

		\theta_1 = \arcsin{ \frac{ (200)^2 + (100)^2 - (150)^2 }{ 2 (100) (200) } } = 43,4 \degree \\[10 pt]

		\theta_2 = \arcsin{ \frac{ (200)^2 + (150)^2 - (100)^2 }{ 2 (150) (200) } } = 61 \degree
		$$

3. Para el caso c elija las masas $m_1$ y $m_2$ y calcule la masa $m_3$.

	$$
	m_1 = 175 \text{ g } \quad m_2 = 225 \text{ g } \\[10 pt]

	m_3 = \sqrt{ (175)^2 + (225)^2 } = 285,0 \text{ g } \\[10 pt]

	\theta_1 = \arcsin{ \frac{ (285,0)^2 + (175)^2 - (225)^2 }{ 2 (175) (285,0) } } = 37,9 \degree \\[10 pt]

	\theta_2 = \arcsin{ \frac{ (285,0)^2 + (225)^2 - (175)^2 }{ 2 (225) (285,0) } } = 52,1 \degree
	$$
