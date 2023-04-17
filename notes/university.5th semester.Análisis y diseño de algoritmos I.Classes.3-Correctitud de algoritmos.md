---
id: nquhd7z3t530dq0ng797vvo
title: 3-Correctitud de algoritmos
desc: ''
updated: 1680836041511
created: 1679699392356
---

# Corrección en computación iterativa

Una **computación iterativa** se caracteriza por comenzar en un estado inicial $S_0$ y transformar ese estado en otro pasando por una secuencia de estados intermedios hasta llegar a un estado final $S_f$

$$
S_0 \rightarrow S_1 \rightarrow S_2 \rightarrow \dots \rightarrow S_f
$$

Todo estado se debe caracterizar por cumplir una condición llamada **invariante de ciclo**.

## Especificación

Se define como la descripción de los siguientes parámetros:

- Entrada: indica las precondiciones

- Salida: indica las poscondiciones

- Idea iterativa: muestra cómo deberían cambiar los estados, comenzando desde el inicial hasta llegar al final

- Estados: especifica la forma de cada estado en forma de tupla, además, se muestra cuál es el invariante de estado

- Estado inicial: muestra los valores que forman el estado inicial

- Estado final: muestra los valores que forman el estado final

- Transformación de estados: de manera formal especifica cómo se realizan, en términos generales, los cambios de un estado al siguiente

> Podríamos decir que es la definición de un problema en términos de su precondición $Q$ y poscondición $R$.

## Demostración

> Para el caso específico de algoritmos iterativos, se cuenta con un método formal de probar la correctitud.

Un algoritmo $A$ es correcto con respecto a una especificación si para cada conjunto de valores que cumplen $Q$, los valores de salida cumplen $R$.

> Se denota como $\{Q\}$ A $\{R\}$. “$A$ es correcto con respecto a la precondición $Q$ y a la poscondición $R$”.

Para comprobar esto debemos fijarnos en los siguientes aspectos

- Inicialización: Pruebe que el estado inicial $S_0$ cumple el invariante

- Mantenimiento de invariante: Prueba que la transformación conserva el invariante

- Éxito: Si $S$ es un estado final y se cumple que el invariante $P \rightarrow R$

- Terminación: $A$ termina

Ejemplos

- Cálculo de factorial

    ```Java
    factorial(int n) { // Entrada
        int i = 0, r = 1; // Estado inicial
        while !(i == n) { // Estado final (i == n)
            // Transformación de estados
            i = i + 1;
            r = resultado * indice;
        }
        System.out.println(r); // Salida
    }
    ```

    - Especificación

        - Entrada: $n \geq 0$

        - Salida: $n!$

        - Idea iterativa: $(0,1) \rightarrow (1,1) \rightarrow (2,2) \rightarrow (3,6) \rightarrow \dots \rightarrow (n, n!)$

        - Estados: $(i,r)$ donde $r = i!$

        - Estado inicial: $(0,1)$

        - Estadio final: $(n,n!)$

        - Transformación de estados: $(i,r) \rightarrow (i + 1,r * (i + 1))$

    - Correctitud

        - Inicialización: $(0,1) \; \land \; 0! = 1$

        - Mantenimiento de invariante

            Se considera antes de entrar al ciclo un $i = k$

            $$
            (k,r) \; \text{donde} \; r = k!
            $$

            Al ejecutar la iteración $i = k + 1$

            $$
            (k + 1, r * (k + 1)) \; donde \; r * (k + 1) = k! * (k + 1) = (k + 1)!
            $$

        - Éxito: $(n,n!)$ retorna $n!$ que es lo que se espera.

        - Terminación: En cada transformación $i$ se incrementa en 1 lo que asegura que en algún momento sea igual a $n$ y la condición `!(i == n)` se deje de cumplir.

- Multiplicación

    ```Java
    Multiplication(int a, int b){ // Entrada
        // Estado inicial
        int i = 1, r = 0;
        while (i <= b){ // Estado final (i = b + 1)
            // Transformación de estados
            i = i + 1;
            r = r + A;
        }
        System.out.println(r); // Salida
    }
    ```

    - Especificación

        - Entrada: $a \in \mathbb{Z},\; b \in \mathbb{N} \; \land \; b > 0$

        - Salida: $a * b$

        - Idea iterativa: $(1,0) \rightarrow (2,a) \rightarrow (3,a + a) \rightarrow \dots \rightarrow (b + 1, \sum_{p = 0}^{i - 1} a)$

        - Estados: $(i,r)$ donde $r = (i - 1) * a$

        - Estado inicial: $(0,1)$

        - Estadio final: $(b + 1, b * a)$

        - Transformación de estados: $(i,r) \rightarrow (i + 1, r + r)$

    - Correctitud

        - Inicialización: $(1,0) \; \land \; 0 = \sum_{p = 0}^{1 - 1} a = 0$

        - Mantenimiento de invariante

            Se considera antes de entrar al ciclo un $i = k$

            $$
            (k,r) \; \text{donde} \; r = \sum_{p = 1}^{k - 1} a
            $$

            Al ejecutar la iteración $i = k + 1$

            $$
            (k + 1, r) \; \text{donde} \; r = \sum_{p = 1}^{k - 1} a + a = \sum_{p = 1}^{(k + 1) - 1} a
            $$

        - Éxito: $invariante \; \land \; estado final \rightarrow R$

            El ciclo finaliza con $i = b + 1$

            $$
            r = \sum_{p = 1}^{i - 1} a = \sum_{p = 1}^{(b + 1) - 1} a = \sum_{p = 1}^{b} a = a * b
            $$

        - Terminación: En cada iteración `i` aumenta, por lo que en algún momento tendrá que alcanzar el valor de `b` y el algoritmo terminará

## Corrección de ciclos usando invariantes

Entendiendo que muchos algoritmos incorporan estructuras iterativas; es importante poder verificar la corrección de los ciclos a lo largo de los algoritmos. Con el fin de simplificar y aplicar el concepto de invariante de ciclo para la corrección, consideramos, en particular, el cumplimiento de la invariante en tres momentos:

- Inicialización: verificar que la propiedad (invariante) se cumple antes de la primera iteración del ciclo.

- Mantenimiento: verificar que si la propiedad se cumple antes de una iteración, también se cumpla después de esa iteración (es decir, antes de la siguiente iteración).

- Terminación: verificar que al terminar el ciclo, el cumplimiento de la invariante lleve al cumplimiento del propósito (resultado esperado) del ciclo.

- Ejemplos

    - [[computer science.Algorithms.Insertion sort]]

        - Invariante del ciclo: al inicio de cada iteración (iteración `j`) el subarreglo `A[1,..., j - 1]` corresponde a los primeros `j - 1` del arreglo original ordenados ascendentemente.

        - Inicialización: antes de iterar por primera vez (cuando `j` se inicializa en 2) el subarreglo `A[1]` ya está ordenado (caso trivial)

        - Mantenimiento: dado que durante la iteración `j` el elemento `A[j]` es reubicado en el subarreglo ordenado `A[1,..., j - 1]` de tal forma que al terminar dicha iteración todo el subarreglo `A[1,..., j]` está ordenado, cumpliendo así la invariante para el inicio de la siguiente iteración (iteración `j + 1`).

        - Terminación: al llevar a cabo la última iteración (`j == n`) el elemento `A[n]` es reubicado dentro del arreglo ordenado `A[1,..., n - 1]`, por lo que el arreglo `A[1,..., n]` queda ordenado. Es decir, se cumple con el propósito del ciclo y del algoritmo.

    - [[computer science.Algorithms.Binary search]]

        - Invariante: Si `x` corresponde a un elemento de `A` (sea `A[i]`), entonces $left \leq i \leq right$

        - Inicializacion: antes de iterar por primera vez, `left` vale 1 y `right` vale `n`, por lo que si `x` hace parte de `A` debe estar en una posición entre `left` y `right`.

        - Mantenimiento

            Si el elemento es encontrado en dicha iteración significa que `i = mid` (`A[mid] == x`) donde `mid` claramente está entre `left` y `right`.

            En caso de que no ocurra lo anterior, hay dos posibilidades

            - `x < A[mid]`: si `x` está en `A` debe estar en una posición inferior a `mid` (`i < mid`), por lo que `i` estaría entre `left` y `mid - 1`, dado que `mid - 1` sería el nuevo valor de `right` significa que `x` está entre `left` y `right`.

            - `x > A[mid]`: si `x` está en `A` debe estar en una posición superior a `mid` (`i > mid`), por lo que `i` estaría entre `mid + 1` y `right`, dado que `mid + 1` sería el nuevo valor de `left` significa que `x` está entre `left` y `right`.

        - Terminación: Al llevar a cabo la última iteración (asumiendo que `x` no ha sido encontrado) la condición del ciclo no se cumple mas por lo que `left` es mayor que `right` lo cual implica que no puede existir una posición `i` en `A` tal que `left <= i <= right` y por ende `x` no puede estar en `A`. Es decir, al no ser encontrado X en A en el ciclo, implica que `x` no hace parte de `A`. Cumpliendo con el propósito del ciclo.