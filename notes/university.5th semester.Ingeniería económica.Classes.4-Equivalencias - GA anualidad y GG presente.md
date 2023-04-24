---
id: yjwjx1t24b45jazy30qtt7z
title: 4-Equivalencias - GA anualidad y GG presente
desc: ''
updated: 1681672669849
created: 1681612824743
---

# Entre un gradiente aritmético $(B,G)$ y un valor presente $(P)$

- Objetivo: Determinar el valor presente equivalente a flujos que **varían** en una cantidad **uniforme**, dada una tasa de interés ($i$) y un horizonte de tiempo ($n$).

![Arithmetic gradient](./assets/University/Ingenieria%20economica/1_4-1%20arithmetic_gradient.jpg)

![Arithmetic gradient decomposition](./assets/University/Ingenieria%20economica/1_4-2%20arithmetic_gradient_decomposition.jpg)

- Anualidad

    $$
    P_A = B \left (\frac{(1 + i)^n - 1}{i(1 + i)^n} \right )
    $$

- Gradiente estricto

    $$
    P = P_1 + P_2 + \dots + P_n \quad \text{si } P = \frac{F}{(1 + i)^n} \\[10 pt]

    P = \frac{F_1}{(1 + i)^1} + \frac{F_2}{(1 + i)^2} + \dots + \frac{F_n}{(1 + i)^n} \rightarrow \frac{0}{(1 + i)^1} + \frac{G}{(1 + i)^2} + \dots + \frac{(n - 1)G}{(1 + i)^n} \quad (1)\\[10 pt]

    \text{multiplicando ambos lados de $(1)$ por $(1 + i)$} \\[5 pt]

    P(1 + i) = \frac{0(1 + i)}{(1 + i)^1} + \frac{G(1 + i)}{(1 + i)^2} + \dots + \frac{(n - 1)G(1 + i)}{(1 + i)^n} \\[10 pt]

    P(1 + i) = 0 + \frac{G}{(1 + i)^1} + \dots + \frac{(n - 1)G}{(1 + i)^{n - 1}} \quad (2) \\[10 pt]

    \text{haciendo $(2) - (1)$} \\[5 pt]


    \begin{align*}

        Pi &= \frac{G}{(1 + i)^1} + \frac{G}{(1 + i)^2} + \dots + \frac{G}{(1 + i)^{n - 1}} - \frac{(n - 1)G}{(1 + i)^n} \\[10 pt]

        &= \frac{G}{(1 + i)^1} + \frac{G}{(1 + i)^2} + \dots + \frac{G}{(1 + i)^{n - 1}} - \left (\frac{Gn}{(1 + i)^n} - \frac{G}{(1 + i)^n} \right ) \\[10 pt]

        &= \left (\frac{G}{(1 + i)^1} + \frac{G}{(1 + i)^2} + \dots + \frac{G}{(1 + i)^{n - 1}} + \frac{G}{(1 + i)^n} \right ) - \frac{Gn}{(1 + i)^n} \quad (3)
    \end{align*} \\[10 pt]

    \text{sea } x = G \left (\frac{1}{(1 + i)^1} + \frac{1}{(1 + i)^2} + \dots + \frac{1}{(1 + i)^{n - 1}} + \frac{1}{(1 + i)^n} \right ) \quad (4) \\[10 pt]

    \text{multiplicando ambos lados de $(4)$ por $(1 + i)$} \\[5 pt]

    \frac{x}{(1 + i)} = G \left (\frac{1}{(1 + i)^2} + \frac{1}{(1 + i)^3} + \dots + \frac{1}{(1 + i)^n} + \frac{1}{(1 + i)^{n + 1}} \right ) \quad (5) \\[10 pt]

    \text{haciendo $(5) - (4)$} \\[5 pt]

    \frac{-ix}{(1 + i)} = G \left (\frac{-1}{(1 + i)^1} + \frac{1}{(1 + i)^{n +  1}} \right ) \quad x = \frac{G}{-i} \left (\frac{1}{(1 + i)^n} - 1 \right ) \\[10 pt]

    x = \frac{G}{-i} \left (\frac{1 - (1 + i)^n}{(1 + i)^n} \right ) = G \left (\frac{(1 + i)^n - 1}{i(1 + i)^n} \right ) \\[10 pt]

    \text{reemplazando $x$ en $(3)$} \\[5 pt]

    Pi = G \left (\frac{(1 + i)^n - 1}{i(1 + i)^n} \right ) - \frac{Gn}{(1 + i)^n} = G \left (\frac{(1 + i)^n - 1}{i(1 + i)^n} - \frac{n}{(1 + i)^n} \right ) = G \left (\frac{(1 + i)^n - 1 - in}{i(1 + i)^n} \right ) \\[10 pt]

    \therefore P_G = G \left (\frac{(1 + i)^n - 1 - in}{i^2(1 + i)^n} \right )
    $$

## Ejemplo

- Una serie de flujos de anuales consecutivos **inicia al final del año 1** con $200000 y **al final del año 9** el flujo corresponde a $80000. Determine el valor de G y el valor presente de los flujos considerando una tasa del 6% anual.

    $$
    B = 200000 \quad n = 9 \\[10 pt]

    B + (n - 1)G = 80000 \quad G = \frac{-120000}{8} = -15000 \\[10 pt]

    P_A = 200000 \left (\frac{(1 + 6\%)^9 - 1}{6\%(1 + 6\%)^9} \right ) \approx 1360338 \\[10 pt]

    P_G = -15000 \left (\frac{(1 + 6\%)^9 - 1 - 6\% * 9}{{6\%}^2(1 + 6\%)^9} \right ) \approx -368651 \\[10 pt]

    P = P_A + P_G \approx 1360338 + (-368651) = 991668
    $$

# Entre un gradiente aritmético $(B,G)$ y una anualidad $(A)$

- Objetivo: determinar la anualidad equivalente ($A$) de un gradiente aritmético, dada una tasa de interés ($i$) y un horizonte de tiempo ($n$).

> Teniendo en cuenta que la parte de $B$ ya es una anualidad.

$$
A = P \left (\frac{i(1 + i)^n}{(1 + i)^n - 1} \right ) \\[10 pt]

\begin{align*}
    A_G &= G \left (\frac{(1 + i)^n - 1 - in}{i^2(1 + i)^n} \right ) \left (\frac{i(1 + i)^n}{(1 + i)^n - 1} \right ) \\[10 pt]

    &= G \left (\frac{(1 + i)^n - 1 - in}{i((1 + i)^n - 1)} \right ) \\[10 pt]

    &= G \left (\frac{(1 + i)^n - 1}{i((1 + i)^n - 1)} - \frac{in}{i((1 + i)^n - 1)} \right ) \\[10 pt]

    &= G \left (\frac{1}{i} - \frac{n}{(1 + i)^n - 1} \right )
\end{align*} \\[10 pt]

A = B + G \left (\frac{1}{i} - \frac{n}{(1 + i)^n - 1} \right )
$$

## Ejemplo

- Power Electric es una empresa que manufactura motores eléctricos. Las utilidades estimadas de la empresa para el **próximo año** son de $800000000. El gerente financiero de la
empresa estima un **crecimiento anual** de $25000000 en utilidades. Si se considera una tasa del 12% anual y un horizonte de análisis de **6 años**, determinar los flujos anuales uniformes equivalentes.

    $$
    i = 12\% \text{ anual} \quad A_G = 25 \left (\frac{1}{12\%} - \frac{6}{(1 + 12\%)^6 - 1} \right ) \approx 54 \\[10 pt]

    A = 800 + 54 = 854 \text{ millones}
    $$

# Entre un gradiente geométrico $(T,s)$ y un valor presente (P)

- Objetivo: determinar el valor presente equivalente ($P$) de un gradiente geométrico, dada una tasa de interés ($i$) y un horizonte de tiempo ($n$).

![Geometric gradient](./assets/University/Ingenieria%20economica/1_4-3%20Geometric_gradient.jpg)

$$
P = P_1 + P_2 + \dots + P_n \quad \text{si } P = \frac{F}{(1 + i)^n} \\[10 pt]

P = \frac{F_1}{(1 + i)^1} + \frac{F_2}{(1 + i)^2} + \dots + \frac{F_n}{(1 + i)^n} \rightarrow \frac{T}{(1 + i)^1} + \frac{T(1 + s)^1}{(1 + i)^2} + \dots \frac{T(1 + s)^{n - 1}}{(1 + i)^n} \quad (6) \\[10 pt]

\text{multiplicamos ambos lados de $(6)$ por $\frac{1 + s}{1 + i}$} \\[5 pt]

P \left (\frac{1 + s}{1 + i} \right ) = \frac{T(1 + s)}{(1 + i)^2} + \frac{T(1 + s)^2}{(1 + i)^3} + \dots \frac{T(1 + s)^n}{(1 + i)^{n + 1}} \quad (7) \\[10 pt]

\text{haciendo $(7) - (6)$} \\[5 pt]

P \left (\frac{1 + s}{1 + i} - 1 \right ) = T \left (-\frac{1}{(1 + i)^1} + \frac{T(1 + s)^n}{(1 + i)^{n + 1}} \right ) \\[10 pt]

P \left (\frac{1 + s}{1 + i} - \frac{1 + i}{1 + i} \right ) = T \left (-\frac{1}{(1 + i)^1} + \frac{T(1 + s)^n}{(1 + i)^{n + 1}} \right ) \\[10 pt]

P \left (\frac{s - i}{1 + i} \right ) = T \left (-\frac{1}{(1 + i)^1} + \frac{T(1 + s)^n}{(1 + i)^{n + 1}} \right ) \\[10 pt]

P(s - i) = T \left (-1 + \frac{T(1 + s)^n}{(1 + i)^n} \right ) \quad P = T \left (\frac{ \left (\frac{T(1 + s)}{(1 + i)} \right )^n - 1}{(s - i)} \right ) \\[10 pt]

P = T \left (\frac{ 1 - \left (\frac{T(1 + s)}{(1 + i)} \right )^n}{(i - s)} \right ) \quad s \neq i \quad P = \frac{Tn}{1 + i} \quad s = 1
$$

## Ejemplo

- El ingeniero de mantenimiento de una planta de generación eléctrica a base de carbón desea actualizar la válvula de control de emisiones. Dicha modificación requiere una inversión inicial de US$8000. Se estima que la vida útil de la válvula es de **5 años**. Los costos de mantenimiento serán de US$1700 para el **primer año** los cuales incrementarán en un 11% **cada año**. Determine el valor presente de todos los costos del proyecto, considerando una tasa de interés del 8% anual.

    $$
    P_G = 1700 \left (\frac{ 1 - \left (\frac{1700(1 + 11\%)}{(1 + 8\%)} \right )^5}{(8\% - 11\%)} \right ) \approx 8319 \\[10 pt]

    P \approx 8000 + 8319 = 16319
    $$