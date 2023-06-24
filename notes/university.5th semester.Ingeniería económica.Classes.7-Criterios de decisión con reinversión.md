---
id: waoq0hppmg6gvo6ntr456zt
title: 7-Criterios de decisión con reinversión
desc: ''
updated: 1685329986653
created: 1685297721352
---

## Tasa Interna de Retorno Modificada (TIRM)

Es un indicador que **relaciona** la tasa de interés de la empresa con la tasa de retorno del proyecto (ambas características propia del proyecto).

Como resultado de la TIRM, siempre se obtiene un **valor intermedio** entre la tasa de interés de la empresa (TMR) y la tasa interna de retorno del proyecto (TIR).

$$
\text{TMR} \leq \text{TIRM} \leq \text{TIR} \\[10 pt]

\text{TIR} \leq \text{TIRM} \leq {TMR}
$$

### Calculo

1. Los egresos netos se trasladan al periodo cero (0) usando la tasa de financiamiento. Es decir, se encuentra el valor presente de los egresos (VPE) usando dicha tasa.

2. Los ingresos netos se trasladan al periodo final del proyecto usando la tasa de reinversión. Es decir, se encuentra el valor futuro de los ingresos (VFI) usando dicha tasa.

3. Al nuevo proyecto obtenido con los pasos anteriores se le debe calcular la TIR, la cual se denomina **Tasa Interna de Retorno Modificada (TIRM)**.

> Vamos a asumir que la tasa de financiamiento y la tasa de reinversión son iguales a la TMR.

### Ejemplo

Determine la rentabilidad de un negocio que presenta los siguientes flujos de dinero en los 3 años de duración del ejercicio. Asuma una TMR igual al 20%.

| $n$ | Flujo |
|:---:|:-----:|
|  0  | -2000 |
|  1  |  500  |
|  2  | 8100  |
|  3  | -6800 |

1. VPE

    - $P/F_3$

        $$
        P = -\frac{6800}{(1 + 20\%)^3} \approx -3935
        $$

    $$
    VPE \approx -2000 + (-3935) = 5935
    $$

2. VFI

    - $F/P_1$

        $$
        F = 500(1 + 20\%)^2 = 720
        $$

    - $F/P_2$

        $$
        F = 8100(1 + 20\%)^1 = 9720
        $$

    $$
    VFI = 720 + 9720 = 10440
    $$

3. TIR

    $$
    5935(1 + i)^3 = 10440 \quad i = 19.23\%
    $$

Como $\text{TIRM} \leq \text{TMR}$ el proyecto **NO** es economicamente factible.

## Valor Futuro de los Flujos de Caja (VFFC)

Calcula la riqueza futura al final del ciclo económico asumiendo que los producidos **se reinvierten a una tasa de reinversión**.

> Vamos a asumir que la tasa de **reinversión** es igual a la **TMR**.

$$
\text{VFFC}_{X,\text{TMR},M} = \sum_{j = 0}^{n} FC_{X_j}(F/P;\text{TMR};M - j) + \sum_{j = 0}^{n} \text{DNU}_{X_j}(F/P;\text{TMR};M - j)
$$

- $M$: periodo de analisis.
- $n$: numero de periodos de la alternativa $X$.
- $FC_{X_j}$: producidos de la alternativa X durante el periodo $j$.
- $DNU_{X-j}$: dinero no utilizado por la alternativa $X$ en el periodo $j$.

$$
\text{DNU}_{X_j} = \text{DISP}_j - \text{INV}_{X_j}
$$

- $\text{DISP}_j$: dinero total disponible en el periodo $j$.
- $\text{INV}_{X_j}$: inversión requerida para el proyecto $X$ en el periodo $j$.

---

Ahora calculamos el VFFC de la alternativa nula.

$$
\text{VFFC}_{\text{nula},\text{TMR},M} = \sum_{j = 0}^{n} \text{DNU}_{X_j}(F/P;\text{TMR};M - j)
$$

Si el $\text{VFFC}_{X,\text{TMR},M \geq \text{VFFC}}_{\text{nula},\text{TMR},M}$ la inversion es **economicamente factible**.

### Ejemplo (VFFC)

Una compañía productora está considerando invertir en una máquina empacadora INDIVIDUAL.

La compañía tiene un presupuesto de $6,000,000. La inversión inicial requerida es de $3.000.000, lo cual resultaría en ingresos anuales netos por $1.200.000 y un valor de mercado al final del año 6 de $1.200.000.

Asumiendo que los ingresos obtenidos se pueden reinvertir a una tasa del 20% anual (TMR de la compañía), determine la factibilidad del proyecto usando el criterio del VFFC.

- $\text{VFFC}_{\text{nula}}$ =
    - $F/P$

        $$
        F = 6000(1 + 20\%)^6 \approx 17916 * 10^3
        $$

- $\text{VFFC}_{\text{maquina}}$

    - $F/P$

        $$
        F = 3000(1 + 20\%)^6 \approx 17916 * 10^3
        $$

    - $F/A$

        $$
        F =
        $$

    $$
    \text{VFFC}_{\text{maquina}} \approx 17916 + =
    $$