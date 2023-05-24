---
id: 8jg44zgvqpslyz1bf4vu74e
title: 2-Conceptos económicos claves
desc: ''
updated: 1684253456837
created: 1679963055320
---

# Interés

Es la compensación que reciben los individuos, firmas o personas naturales, por el sacrificio en que incurren al ahorrar una suma $P$.

El mercado brinda la posibilidad de invertir o la de recibir un préstamo; lo anterior hace que exista el interés.

El interés ($I$) en la cantidad monetaria es la diferencia entre la cantidad de dinero pagado (recibido) al final ($F$) y la cantidad de dinero recibido (pagado) al inicio ($P$).

$$
\text{Deudor} \\[5 pt]

I = \text{dinero pagado} - \text{dinero recibido} \\[10 pt]

\text{Inversionista} \\[5 pt]

I = \text{dinero recibido} - \text{dinero pagado} \\[10 pt]

\color{Green} {I = F - P}
$$

Este fenómeno económico real se mide con la tasa de interés $i$, la cual, a su vez, se representa por un porcentaje.

Este porcentaje se calcula dividiendo el interés recibido o pagado en dinero $I$ por un **periodo** sobre el monto inicial $P$; de modo que la tasa de interés será:

$$
i = \frac{\text{monto final}}{\text{monto inicial}} = \frac{I}{P}
$$

> Siempre se debe expresar con una referencia de tiempo.


## Tipos

- Simple

    El interés es simple cuando **solo el capital inicial ($P$)** genera intereses. Es decir, el interés de un periodo $t$ no generará intereses en periodos posteriores a $t$.

    $$
    i = \frac{I}{P} \rightarrow I = P * i
    $$

    Pero si el plazo son $n$ periodos, y considerando que en cada periodo el interés generado siempre será respecto a $P$, entonces:

    $$
    I = P * i * n
    $$

    El valor futuro (F) para el interés simple se expresa como:

    $$
    F = P + P * i * n = P(1 + i * n)
    $$

    > Las unidades de tiempo de $i$ deben coincidir con las de $n$.

- Compuesto

    El interés es compuesto si el interés de un periodo $t$ se agrega al capital y por eso **también generará intereses** en periodos posteriores a $t$.

    > La característica esencial del interés compuesto es que el capital al comenzar un periodo cualquiera **será mayor que el que se tenía** al iniciar el periodo anterior.

    $$
    I_t = \left (P + \sum_{j = 1}^{t - 1} I_j \right ) * i
    $$

    > Tomando a $I_1 = 0$, estamos calculando los intereses asociados a un tiempo $t$.

    Equivalencia entre un valor presente $P$ y un valor futuro $F$ usando interés compuesto:

    $$
    F_n = P(1 + i)^n
    $$

# Sistema financiero

Se puede definir como el conjunto de **mercados e instituciones** usados para contraer **acuerdos financieros** e intercambiar activos y riesgos.

![Finance system](./assets/University/Ingenieria%20econ%C3%B3mica/1_2-1%20Finance-system.jpg)

# Nomenclatura

- Presente o pasado ($P_i$)

    Flujo de efectivo que se da en periodos **previos** (pasado) o en el **mismo** periodo (presente) **con respecto al observador**.

- Futuro ($F_i$)

    Flujo de efectivo que se da en periodos **posteriores** (futuro) **con respecto al observador**.

- Anualidad ($A_{n_1 - n_2}$)

    Flujos de efectivo **consecutivos uniformes**. Inicia en el periodo $n_1$ y finaliza en el periodo $n_2$.

    > El primer flujo de la anualidad se da en el periodo posterior a donde inicia la anualidad.

    > $\text{número  de flujos} = n_2 - n_1$

- Gradiente aritmético ($(B,G)_{n_1 - n_2}$)

    Flujos de efectivo **consecutivos que crecen o decrecen** en una misma magnitud $G$ cada periodo. Inicia en el periodo $n_1$ y finaliza en el periodo $n_2$.

    > La base $B$ (primer flujo del gradiente) se da en el periodo posterior a donde inicia.

    > $\text{número  de flujos} = n_2 - n_1$

- Gradiente geométrico ($(T,S)_{n_1 - n_2}$)

    Flujos de efectivo **consecutivos que crecen o decrecen** en un mismo porcentaje $s$ cada periodo. Inicia en el periodo $n_1$ y finaliza en el periodo $n_2$.

    > La base $T$ (primer flujo del gradiente) se da en el periodo posterior a donde inicia.

    > $\text{número  de flujos} = n_2 - n_1$