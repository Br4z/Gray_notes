---
id: 48f28ruxezzyagu9n9cmzij
title: 2-Insertion sort
desc: ''
updated: 1680827955838
created: 1679698672454
---

![[root.Computer science.Algorithms.Insertion sort]]

# ¿Que es hacer análisis de algoritmos?

- **Calcular tiempo de computación**

- Espacio (memoria)

- Analizar las estructuras de datos utilizadas

- Identificar el tipo y número de datos de entrada al algoritmo

El tiempo de cómputo T de un algoritmo depende del tamaño de la entrada, $T(n) = f(n)$donde $n$ es el tamaño de la entrada.

> Dado que el tiempo dependerá de la máquina en la que sea ejecutada nuestro algoritmo, nos referiremos al tiempo como las instrucciones necesarias para que nuestro algoritmo acabe.

## Saberes previos

- Repeticiones de un `for`

    `for i <- i_0 to n = for (i <- i_0, i <= n, i <- i + 1)`

    $\text{Repeticiones} = n - i_0 + 1$

    > El 1 es por la última comprobación de la condición que hace.

- Repeticiones de un `while`

    `while (condition)`

    $\text{Repeticiones} = n + 1$

    > $n$ es el número de veces que entra al `while`, y el 1 es por la última comprobación que hace.

|            **Código**            |              **Repeticiones**               |
|:--------------------------------:|:-------------------------------------------:|
| `for j <- 2 to length[A]`        | $n$                                         |
| `    do key <- A[j]`             | $n - 1$                                     |
| `    i <- j - 1`                 | $n - 1$                                     |
| `    while i > 0 and A[i] > key` | $t_2 + t_3 + \dots + t_n$                   |
| `        do A[i + 1] <- A[i]`    | $(t_2 - 1) + (t_3 - 1) + \dots + (t_n - 1)$ |
| `        i <- i - 1`             | $(t_2 - 1) + (t_3 - 1) + \dots + (t_n - 1)$ |
| `    A[i + 1] <- key`            | $n - 1$                                     |

> NOTA: los índices comienzan en 1.

> Cada línea también tiene asociado su costo computacional (refiriéndonos al tiempo), puede depender del hardware y software.

No referimos a $t_j$ como a la cantidad de comparaciones que se hacen en el `while` para cada valor de `j`. Hacemos esto porque **para cada `j`, se puede repetir una cantidad diferente de veces** (pues depende de qué tan ordenados se encuentran los datos en `A`). Expresando algunas expresiones como sumatorias tenemos que

|            **Código**            |       **Repeticiones**       |
|:--------------------------------:|:----------------------------:|
| `    while i > 0 and A[i] > key` | $\sum_{j = 2}^{n} t_j$       |
| `        do A[i + 1] <- A[i]`    | $\sum_{j = 2}^{n} (t_j - 1)$ |
| `        i <- i - 1`             | $\sum_{j = 2}^{n} (t_j - 1)$ |


## Mejor caso

En el mejor de los casos, $t_j = 1$. Esto ocurre cuando el arreglo de entrada está ordenado ascendentemente. Caso en el que el `while` solo se ejecuta una vez por
cada iteración en `j` ($\sum_{j = 2}^{n} 1$). Dejando la tabla de la siguiente forma

|            **Código**            |   **Repeticiones**   |
|:--------------------------------:|:--------------------:|
| `for j <- 2 to length[A]`        | $n$                  |
| `    do key <- A[j]`             | $n - 1$              |
| `    i <- j - 1`                 | $n - 1$              |
| `    while i > 0 and A[i] > key` | $\sum_{j = 2}^{n} 1$ |
| `        do A[i + 1] <- A[i]`    | $0$                  |
| `        i <- i - 1`             | $0$                  |
| `    A[i + 1] <- key`            | $n - 1$              |


Viendo por encima, este algoritmo tiene una complejidad lineal ($O(n)$), podemos asegurar esto porque al sumar las repeticiones no podemos aumentar el grado de la mayor que ya hay, es decir, $Grad(A + B) = Max(Grad(A),Grad(B))$.

## Peor caso

En el peor de los casos, $t_j = j$. Ocurre cuando el arreglo inicialmente está ordenado descendentemente, porque el `while` se ejecutará para todos los valores de `i` desde 0 hasta `j - 1`. Dejando la tabla de la siguiente forma

|            **Código**            |      **Repeticiones**      |
|:--------------------------------:|:--------------------------:|
| `for j <- 2 to length[A]`        | $n$                        |
| `    do key <- A[j]`             | $n - 1$                    |
| `    i <- j - 1`                 | $n - 1$                    |
| `    while i > 0 and A[i] > key` | $\sum_{j = 2}^{n} j$       |
| `        do A[i + 1] <- A[i]`    | $\sum_{j = 2}^{n} (j - 1)$ |
| `        i <- i - 1`             | $\sum_{j = 2}^{n} (j - 1)$ |
| `    A[i + 1] <- key`            | $n - 1$                    |

Para hallar la complejidad resolvamos la sumatoria

$$
\sum_{j = 2}^{n} j = \frac{(n + 1)n}{2} - 1 = \frac{n^2 + n}{2} - 1 \\[10 pt]

\frac{n^2}{2} + \frac{n}{2} - 1 \quad O(n^2)
$$

## Caso intermedio

Caso que ocurre cuando el arreglo `A` no está tan ordenado y desordenado (de la forma que el algoritmo quiere hacerlo). En tal caso $t_j = \frac{j}{2}$

|            **Código**            |           **Repeticiones**           |
|:--------------------------------:|:------------------------------------:|
| `for j <- 2 to length[A]`        | $n$                                  |
| `    do key <- A[j]`             | $n - 1$                              |
| `    i <- j - 1`                 | $n - 1$                              |
| `    while i > 0 and A[i] > key` | $\sum_{j = 2}^{n} \frac{j}{2}$       |
| `        do A[i + 1] <- A[i]`    | $\sum_{j = 2}^{n} (\frac{j}{2} - 1)$ |
| `        i <- i - 1`             | $\sum_{j = 2}^{n} (\frac{j}{2} - 1)$ |
| `    A[i + 1] <- key`            | $n - 1$                              |

Para hallar la complejidad resolvamos la sumatoria

$$
\sum_{j = 2}^{n} \frac{j}{2} = \frac{1}{2}\sum_{j = 2}^{n} j = \frac{1}{2} \left (\frac{n^2}{2} + \frac{n}{2} - 1 \right) \\[10 pt]

\frac{n^2}{4} + \frac{n}{4} - \frac{1}{2} \quad O(n^2)


$$

Al igual que la anterior, su complejidad es cuadrática. Ahora resolvamos las expresiones que están dentro del `while`

$$
\sum_{j = 2}^{n} \left (\frac{j}{2} - 1 \right) = \sum_{j = 2}^{n} \frac{j}{2} - \sum_{j = 2}^{n} 1 \\[10 pt]

\left (\frac{n^2}{4} + \frac{n}{4} - \frac{1}{2} \right ) - (n - 1) = \frac{n^2}{4} - \frac{3n}{4} \quad O(n^2)
$$

Como era de esperarse, también tiene complejidad cuadrática.

## Familias de funciones según su crecimiento

Suponga que tenemos las funciones $f(n)$ y $g(n)$, si $f(n)$ pertenece a una familia de funciones de menor tasa de crecimiento que
$g(n)$ o en otras palabras si $Grad(f(n)) < Grad(g(n))$ entonces se cumple que:

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0 \\[10 pt]

\lim_{n \to \infty} \frac{g(n)}{f(n)} = \infty
$$

## Ejercicios

Calcule el tiempo de cómputo para los siguientes algoritmos

1. `def programa1(mat1, mat2) # Suponga que len(mat1) = len(mat2) = n`

> Supongamos que se empieza a indexar desde el 1.

|                    **Código**                   | **Repeticiones** |
|:-----------------------------------------------:|:----------------:|
| `i <- 1`                                        | $1$              |
| `while i <= len(mat1)`                          | $n + 1$          |
| `    j <- 1`                                    | $n$              |
| `    while j <= len(mat2)`                      | $n + 1$          |
| `        mat3[i][j] <- mat1[i][j] + mat2[i][j]` | $n$              |
| `        j <- j + 1`                            | $n$              |
| `    i <- i + 1`                                | $n - 1$          |

> Analizando el código vemos que este programa suma dos matrices.


Para calcular el tiempo de cómputo, tenemos que multiplicar las repeticiones de cada línea por su costo asociado.

2. `def programa2(n)`

|      **Código**      |      **Repeticiones**      |
|:--------------------:|:--------------------------:|
| `s <- 0`             | $1$                        |
| `i <- 1`             | $1$                        |
| `while i <= n`       | $n + 1$                    |
| `    t <- 0`         | $n$                        |
| `    j <- 1`         | $n$                        |
| `    while j <= i`   | $\sum_{j = 1}^{i} (j + 1)$ |
| `        t <- t + 1` | $\sum_{j = 1}^{i} j$       |
| `        j <- j + 1` | $\sum_{j = 1}^{i} j$       |
| `    s <- s + t`     | $n$                        |
| `    i <- i + 1`     | $n$                        |


> Analizando el código vemos que este programa calcula la sumatoria aritmética hasta `n` ($\sum_{n = 1}^{n} n$).

3. `def programa3(n)`

|      **Código**      |      **Repeticiones**      |
|:--------------------:|:--------------------------:|
| `i <- 1`             | $1$                        |
| `while i <= n`       | $n + 1$                    |
| `    k <- i`         | $n$                        |
| `    while k <= n`   | $\sum_{j = 1}^{n} (j + 1)$ |
| `        k <- k + 1` | $\sum_{j = 1}^{n} j$       |
| `    k <- 1`         | $n$                        |
| `    while k <= i`   | $\sum_{j = 1}^{i} (j + 1)$ |
| `        k <- k + 1` | $\sum_{j = 1}^{i} j$       |
| `    i <- i + 1`     | $n$                        |

Esta vez el programa no tiene un propósito, se puede notar que lo que hace en el `while k <= n`, se deshace con `k <- 1`, en general hay muchas asignaciones sin sentido.

> Lo anterior no nos impide calcular las veces que se repite cada línea.

### Anotaciones

- La sentencia `return` es bastante descriptiva en una función, pues su intención suele estar en lo que retorna.

    - En el `programa1` su utilidad está más en sus efectos secundarios que en retornar algo (`mat3` termina siendo la suma de la matriz `mat1` y `mat2`).

    - Lo más probable es que retorne `s`, que como dije es la sumatoria aritmética hasta `n`.

    - Nada


Otras alternativas para el diseño de algoritmos son:

- Aproximación incremental

- **Dividir y conquistar**

- Programación dinámica

- Técnicas voraces

## Dividir y conquistar

- Considera recursividad

- **Dividir** el problema en subproblemas

- **Conquistar** los subproblemas (solucionarlos recursivamente)

- **Combinar** las soluciones de los subproblemas para crear la solución al problema original

### Merge sort

![[root.Computer science.Algorithms.Merge sort]]

$$
T(n) \left \{
    \begin{array}{cl}
        1                                        & si & n = 1 \\
        dividir(n) + conquistar(n) + combinar(n) & si & n \geq 1
    \end{array} \right . \\[10 pt]

T(n) \left \{
    \begin{array}{cl}
        1                       & si & n = 1 \\
        1 + 2T(\frac{n}{2}) + n & si & n \geq 1
    \end{array} \right . \\[10 pt]
$$

- $1$: partición de la lista

- $2T(\frac{n}{2})$: ordenamiento de las sublistas

- $n$: comparaciones de los elementos de la lista actual (para que quede ordenada)

    > Es $n$ y no $n - 1$, porque se tiene que hacer una comprobación cuando ya no quedan elementos por ordenar.

Cuando resolvemos la relación de recurrencia $T(n) = n \log n$

## Análisis de algoritmos Insertion sort y Merge sort

| **Computador** | **instrucciones/seg** |
|:--------------:|:---------------------:|
| 1              | $10^8$                |
| 2              | $10^6$                |

|  **Algoritmo de ordenamiento**  |  **$T(n)$** |
|:-------------------------------:|:-----------:|
| Insertion                       | $2n^2$      |
| Merge                           | $50n\log n$ |

> Vemos que cada expresión para el $T(n)$ tiene asociada una constante, está relacionada con las expresiones que no consideramos al hallar su complejidad.


Consideremos ordenar un arreglo de $10^6$ números

- $Insertion \rightarrow \frac{2(10^6)^2}{10^8} = 20000 \; seg = 5.56 \; horas$

- $Merge \rightarrow \frac{50(10^6\log 10^6)}{10^6} = 1000 \; seg = 16.57 \; minutos$

> La potencia del **computador 2** no compensa la complejidad del algoritmo.