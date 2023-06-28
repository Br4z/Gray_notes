---
id: tqh0um80a9ojnx88ygag2cd
title: 5-Equivalencias - Intereses
desc: ''
updated: 1687786411259
created: 1682217143766
---

# Tasas efectivas

Son las tasas que se aplican por **periodo de tiempo**, es decir, son las que se utilizan para calcular los intereses generados. Se denotan con la letra $i$.

$$
i =  X\% \text{ periodo de tiempo}
$$

> Las tasas efectivas son las que se aplican en las formulas de la ingeniería económica, teniendo presente que el **periodo de análisis ($n$) debe estar en términos del periodo de composición de la tasa**.

# Tasas nominales

Son tasas usadas para expresar las tasas efectivas en relación con un **periodo de referencia**. Y al ser una tasa de referencia, no explica la generación de intereses y, por tanto, **NO** debe aplicarse en las fórmulas de la ingeniería económica.

> Se denota como $r$ y siempre tienen dos periodos de tiempo asociados.

$$
r = X\% \text{ periodo de referencia } \text{ periodo de composición} \\[10 pt]

r = i * m
$$

- Periodo de referencia: periodo base en el que se expresa la tasa efectiva implícita.

- Periodo de composición: frecuencia de aplicación de
la tasa efectiva implícita.

- $i$: tasa efectiva implícita.

- $m$: número de periodos de composición en el periodo de referencia.

## Ejemplo

- Expresar una tasa de interés efectiva del 5% mensual a un año como una tasa nominal semestral.

    - Tasa efectiva: 5%.
    - Periodo de composición de la tasa efectiva: mensual.
    - Periodo de referencia de la tasa nominal: 1 semestre.

    $$
    r = 5\% * 6 \\[10 pt]

    r = 30\% \text{ semestral compuesto mensualmente}
    $$

## Conversion a tasa efectiva

Para pasar de una tasa nominal ($r$) a una efectiva ($i$), se tiene que:

$$
i = \frac{r}{m} \text{ interés periódico}
$$

### Ejemplos

- 9% anual compuesto trimestralmente.

    $$
    r = 9\% \quad m = \frac{12}{3} = 4 \\[10 pt]

    i = \frac{9\%}{4} = 2.25\%
    $$

> La conversion es obligatoria para poder comparar tasas.

# Equivalencias

## Entre tasas efectivas

Dos tasas efectivas con distintos periodos de composición son **equivalentes**, si partiendo de un mismo valor presente llegan al mismo valor futuro en el mismo horizonte de tiempo.

Sea la tasa $i_1$, con el periodo de composición ${Pe}_1$. Se desea convertir esa tasa a una tasa $i_2$ con periodo de composición ${Pe}_2$. Sea $m$ la cantidad de periodos ${Pe}_1$ en ${Pe}_2$.

> Por sentido común entenderemos que ${Pe}_2$ es mas grande.

$$
F = P(1 + i_2) = P(1 + i_1)^m \\[10 pt]

i_1 = (1 + i_2)^{\frac{1}{m}} - 1 \quad i_2 = (1 + i_1)^m - 1 \\[10 pt]

\text{En general tendremos lo siguiente:} \\[5 pt]

i_{pl} = (1 + i_{pc})^m - 1 \\[10 pt]

i_{pc} = (1 + i_{pl})^{\frac{1}{m}} - 1
$$

### Ejemplo

- Encontrar la tasa mensual equivalente a una tasa de 9% anual.

    $$
    i_m = (1 + 9\%)^{\frac{1}{12}} - 1 = 0.72\%
    $$

    > Como curiosidad, esta tasa es menor a la que hubiéramos encontrado haciendo la división del interés sobre 12 (0.75\%), es decir, con una tasa menor producimos lo mismo.

## Entre tasas vencidas y anticipadas

### Momento de aplicación

- Puede ser vencido (final del periodo) o anticipado (inicio del periodo).

- Es necesario transformar anticipado en vencido

![Equivalence between due and anticipated rates](./assets/University/Ingenieria%20econ%C3%B3mica/1_5-1%20Equivalence_between_due_and_anticipated_rates.jpg)

$$
F = P(1 + i_v)^n \quad F = (P^* - P^* * i_a)(1 + i_v)^1 = P^*(1 - i_a)(1 + i_v)^1 \\[10 pt]

P^* = P^*(1 - i_a)(1 + i_v)^1 \quad (1 - i_a)(1 + i_v)^1 = 1 \\[10 pt]

i_v = \frac{i_a}{1 - i_a} \quad i_a = \frac{i_v}{1 + i_v}
$$

> Vemos que la tasa anticipada es mas grande que la vencida.

# Intereses múltiples

- Situaciones en las que ocurre la aplicación de **más de una tasa de interés** sobre los mismos flujos de dinero.

    > Tasa de interés en dólares y revaluación del dólar o tasa de interés en pesos y devaluación del peso.

- Deben estar en la **misma unidad temporal**.

## Revaluación y devaluación

> No confundir con la inflación.

- Devaluación moneda local: cuando la cantidad de la moneda local para comprar **una unidad** de moneda extranjera **aumenta**.

    > Revaluación moneda extranjera.

- Revaluación moneda local: Cuando la cantidad de la moneda local para comprar **una unidad** de moneda extranjera **disminuye**.

    > Devaluación moneda extranjera.

### Ejemplo

- Si se pasa de pagar $2000 por un dólar a $3000 por un dólar, ¿cuál es el valor de la devaluación del peso y la revaluación del dólar?

    $$
    \frac{\text{peso}}{\text{dólar}} \quad 2000 + (1 + t) = 3000 \rightarrow t = 0.5 \text{ (revaluación del dólar)} \\[10 pt]


    \frac{\text{dólar}}{\text{peso}} \quad \frac{1}{2000} + (1 + t) = \frac{1}{3000} \rightarrow t = -0.33 \text{ (devaluación del peso)}
    $$

    > Recuerde validar el signo de la tasa de variación ($t$) y la moneda del denominador.

---

![Multiple interests](./assets/University/Ingenieria%20econ%C3%B3mica/1_5-2%20Multiple_interests.jpg)

$$
F_\$ = P_\$(1 + i_\$)^1 \quad F_{TC} = P_{TC}(1 + Rev_\$)^1 \quad F_P = P_P(1 + i_{COP})^1 \\[10 pt]

F_\$ * F_{TC} = P_\$(1 + i_\$)^1 * P_{TC}(1 + Rev_\$)^1 \\[10 pt]

P_P = P_\$ * P_{TC} \\[20 pt]

P_\$(1 + i_\$)^1 * P_{TC}(1 + Rev_\$)^1 = P_\$ * P_{TC}(1 + i_{COP})^1 \quad (1 + i_\$)(1 + Rev_\$) = (1 + i_{COP}) \\[10 pt]

i_{COP} = (1 + i_\$)(1 + Rev_\$) - 1 \quad i_\$ = \frac{1 + i_{COP}}{1 + Rev_\$} - 1 \\[10 pt]

i_{COP} = (1 + i_\$) \left (1 + Rev_{\frac{\text{peso}}{\text{dólar}}} \right ) - 1 \\[10 pt]

i_\$ = (1 + i_{COP}) \left (1 + Dev_{\frac{\text{dólar}}{\text{peso}}} \right ) - 1
$$

> Todas las tasas deben estar en el mismo periodo de tiempo.

### Ejemplo

- Calcule la tasa de interés efectivo anual en pesos de una tasa de interés del 2% mensual en dólares con una revaluación del dólar del 24% anual.

    $$
    i_a = (1 + 2\%)^{12} - 1 = 26.82\% \\[10 pt]

    i_{\text{COP}} = (1 + 26.82\%)(1 + 24\%) - 1 = 57.26\%
    $$