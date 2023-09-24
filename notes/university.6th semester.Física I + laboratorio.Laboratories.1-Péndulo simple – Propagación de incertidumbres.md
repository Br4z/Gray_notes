---
id: plqtamo3c9c5ljz1e0k7ihs
title: 1-Péndulo simple – Propagación de incertidumbres
desc: ''
updated: 1694732867337
created: 1694298909790
---

![Simple pendulum](./assets/University/Física%20I%20+%20laboratorio/3_1-1%20Simple_pendulum.jpg)

$$
x = l \sin{ \theta } \quad y = l \cos{ \theta }
$$

Por segunda ley de Newton tenemos:

$$
\vec{ T } = m \vec{ g } = m \vec{ a } \\[10 pt]

e_r - \vec{ T } = m \vec{ a_r } \quad m \vec{ g } \cos{ \theta } = m \vec{ a_r } \\[10 pt]

e_\theta = m \vec{ a_\theta } \quad -m \vec{ g } \sin{ \theta } = m \vec{ a_\theta } \quad \vec{ a_\theta } = -\vec{ g } \sin{ \theta }
$$

Recordando que en un movimiento circular de radio $R$, las aceleraciones lineal $\vec{ a_\theta }$ y angular $\alpha$, se relacionan según $\vec{ a_\theta } = \alpha R$ y utilizando para la aceleración angular la notación $\"{ \theta } = \frac{ d^2 \theta }{ dt^2 }$.

$$
-\vec{ g } \sin{ \theta } = \"{ \theta } l \quad \"{ \theta } l + \vec{ g } \sin{ \theta } = 0 \quad \"{ \theta } + \frac{ \vec{ g } }{ l } \sin{ \theta } = 0 \\[10 pt]

\"{ \theta } + \frac{ \vec{ g } }{ l } \theta = 0 \quad \sin{ \theta } \approx 0 \; \lim_{ \theta \to 0 } \sin{ \theta } = \theta
$$

De la solución de esa ecuación diferencial podemos hallar el periodo con la siguiente fórmula:

$$
T = 2 \pi \sqrt{ \frac{ l }{ \vec{ g } } } \\[10 pt]

\left ( \frac{ T }{ 2 \pi } \right )^2 = \quad \left ( \sqrt{ \frac{ l }{ \vec{ g } } } \right )^2 \\[10 pt]

\frac{ T^2 }{ 4 \pi^2 } = \frac{ l }{ \vec{ g } } \quad \vec{ g } = l \frac{ 4 \pi^2 }{ T^2 }
$$

Para hallar la incertidumbre asociada a la gravedad resolvemos su derivada total:

$$
\Delta { \vec{ g } } = \left | \frac{ d \vec{ g } }{ d l } \Delta { l } \right | + \left | \frac{ d \vec{ g } }{ d T } \Delta { T } \right | \quad \frac{ \Delta { \vec{ g } } }{ | \vec{ g } | } = \frac{ 4 l \pi^2 T^{ -2 } \Delta { l } - 8 l \pi^2 T^{ -3 } \Delta { T } }{ 4 l \pi^2 T^{ -2 } } \\[10 pt]

\Delta { \vec{ g } } = \left ( \frac{ \Delta { l } }{ l } - 2 \frac{ \Delta { T } }{ T } \right ) | \vec{ g } |
$$
