---
id: z0oziq4zobi1dqiekvh4m4y
title: 6-Criterios de decisión
desc: ''
updated: 1684885594181
created: 1684093157228
---

# ¿Qué son?

Son utilizados para determinar si un proyecto o alternativa de inversión es o no **económicamente factible**.

> Hay otros aspectos que se deben analizar (como el ambiental) en un proyecto real.

- Valores neto

    - Presente
    - Anual
    - Futuro

- Tasa interna de retorno

# Valor Presente Neto (VPN)

Es un valor presente equivalente a todos los flujos de efectivo del proyecto, el cual se calcula usando la **tasa mínima de retorno** (TMR) o **tasa del inversionista**.

![VPN definition](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-1%20VPN_definition.jpg)

$$
\text{VPN} = \text{valor presente de los ingresos} - \text{valor presente de los egresos}
$$

El VPN es la **utilidad económica** en el presente.

> Si el $\text{VPN} \geq 0$, el proyecto es **económicamente factible**.

# Valor Anual Neto (VAN)

Es una serie de flujos uniformes equivalente a todos los flujos de efectivo del proyecto, la cual se calcula usando la **tasa mínima de retorno** (TMR) o **tasa del inversionista**.

![VAN definition](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-2%20VAN_definition.jpg)

$$
\text{VAN} = \text{valor anual de los ingresos} - \text{valor anual de los egresos}
$$

El VAN es la **utilidad económica** representada en una serie de flujos uniformes.

> Si el $\text{VAN} \geq 0$, el proyecto es **económicamente factible**.

# Valor Futuro Neto (VFN)

Es un valor futuro equivalente a todos los flujos de efectivo del proyecto, el cual se calcula usando la **tasa mínima de retorno** (TMR) o **tasa del inversionista**.

![VFN definition](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-3%20VFN_definition.jpg)

$$
\text{VAN} = \text{valor futuro de los ingresos} - \text{valor futuro de los egresos}
$$

El VFN es la **utilidad económica** en el futuro o periodo final del proyecto.

> Si el $\text{VFN} \geq 0$, el proyecto es **económicamente factible**.

# Ejemplo

- Suponga que un inversionista está evaluando la posibilidad de invertir en la adquisición de un bus de servicio público que tiene un costo de $150000000, la cual producirá $50000000 anuales después de gastos de operación y mantenimiento y su valor de mercado en 5 años se estima en $15000000.

    Si la tasa mínima de retorno es del 20% anual, determine si este negocio sería económicamente factible o no.

    ![Example of decision criteria](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-4%20Example_decision_criteria.jpg)


    | $n$ | Flujo |
    |:---:|:-----:|
    |  0  | -150  |
    |  1  |  50   |
    |  2  |  50   |
    |  3  |  50   |
    |  4  |  50   |
    |  5  |  65   |

    - $P/A_{(0 - 5)}$

        $$
        P = 50 \left (\frac{(1 + 20\%)^5 - 1}{20\%(1 + 20\%)^5} \right ) \approx 149 * 10^6
        $$

    - $P/F$

        $$
        P = \frac{15}{(1 + 20\%)^5} \approx 6 * 10^6
        $$

    $$
    VPN = (149 + 6 - 150) * 10^6 = (5) * 10^6
    $$

    Dado que el $\text{VPN} \geq 0$, el proyecto es **económicamente factible**.

# Valor presente de flujos no periódicos

Algunos proyectos pueden tener flujos de dinero que no tienen un comportamiento periódico, sino que su ocurrencia está asociada a fechas específicas.

![VPN of non-periodic flows definition](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-5%20VPN_non-periodic_flows_definition.jpg)

> En estos casos se debe dejar todo en **términos anuales**.

$$
\text{VPN}_{i\%} = \frac{F_1}{(1 + i\%)^{\frac{n_1}{365}}} + \frac{F_2}{(1 + i\%)^{\frac{n_1 + n_2}{365}}} + \frac{F_3}{(1 + i\%)^{\frac{n_1 + n_2 + n_3}{365}}} - \text{inversion}
$$

> $i\%$ se expresa sobre base efectiva anual.

# Tasa Interna de Retorno (TIR)

Tasa de interés que hace que el **VPN (VAN o VFN)** de una serie de flujos de efectivo sea exactamente igual a **cero (0)**.

## Ejemplos

- Con el mismo ejemplo del bus. ¿Cuál sería el **retorno anual sobre la inversión no amortizada** al invertir en esta opción?

    - $P/A_{(0 - 5)}$

        $$
        P = 50 \left (\frac{(1 + i)^5 - 1}{i(1 + i)^5} \right )
        $$

     - $P/F$

        $$
        P = \frac{15}{(1 + i)^5}
        $$

    $$
    50 \left (\frac{(1 + i)^5 - 1}{i(1 + i)^5} \right ) + \frac{15}{(1 + i)^5} = 150 \quad \frac{50(1 + i)^5 - 50 + 15i}{i(1 + i)^5} = 150 \\[10 pt]

    i = 21.61\%
    $$

    > Siendo problema sencillo, la expresión es bastante engorrosa, por esta razón usaremos Excel.

> Si la $\text{TIR} \geq \text{TMR}$, el proyecto es **económicamente factible**

- La organización XYZ, adquiere una máquina cortadora por $200000 y con ella logra reducir sus costos anuales en $50000 durante los 5 años de vida útil de la máquina.

    Calcule el rendimiento o tasa interna de retorno (TIR) de esta inversión. Suponga que el valor de mercado de la máquina pasados los 5 años es nulo.


    - $P/A$

        $$
        P = 50 \left (\frac{(1 + i)^5 - 1}{i(1 + i)^5} \right )
        $$

    $$
    50 \left (\frac{(1 + i)^5 - 1}{i(1 + i)^5} \right ) = 200 \\[10 pt]

    i = 7.93\%
    $$

- Determine la rentabilidad de un negocio que presenta los siguientes flujos de dinero en los 3 años de duración del ejercicio.

    | $n$ | Flujo |
    |:---:|:-----:|
    |  0  | -2000 |
    |  1  |  500  |
    |  2  | 8100  |
    |  3  | -6800 |

    > Dado que no es posible identificar estructuras, debemos para todos los flujos manualmente.

    - $P/F_3$

        $$
        P = -\frac{6800}{(1 + i)^3}
        $$

    - $P/F_2$

        $$
        P = \frac{8100}{(1 + i)^2}
        $$

    - $P/F_1$

        $$
        P = \frac{500}{(1 + i)}
        $$

    $$
    \frac{-500}{(1 + i)} + \frac{-8100}{(1 + i)^2} - \frac{6800}{(1 + i)^3} = 2000 \\[10 pt]

    i = 7.46\% \quad i = 41.35\%
    $$

    > Como vemos hay dos intereses que hacen que el VPN sea cero.

## Análisis adicional

La principal desventaja de la TIR es que su comportamiento está relacionado con la forma del flujo de efectivo neto del proyecto. Lo aconsejable es emplear este criterio **solo cuando el flujo de efectivo sea convencional**.

![Types of net flows](./assets/University/Ingenieria%20econ%C3%B3mica/1_6-6%20Types_net_flows.jpg)

> Para tratar este problema existe la Tasa Interna de Retorno Modificada (TIRM).
