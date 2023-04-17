---
id: qt7lx14y933fibq5raumjc0
title: 6-Quick sort
desc: ''
updated: 1680988843936
created: 1680979597729
---

# [[computer science.Algorithms.Quick sort]]

- En el peor caso tiene un tiempo de $\Theta(n^2)$.

- Es una de las mejores opciones en la práctica, debido a que su tiempo promedio es de $\Theta(n\lg n)$.

- Los factores constantes en $\Theta(n\lg n)$ son pequeños comparados con los de los otros algoritmos.

- Es ordenación **in-place**.

- Utiliza la técnica **divide, conquistar y combinar**.

    Dado un arreglo `A[p..r]`

    - Dividir: `A[p..r]` es particionado en dos subarreglos no vacíos `A[p,...q]` y `A[q + 1,...r]` tal que cada elemento en el primero sea menor o igual que los del segundo.

    - Conquistar: Ordenar los dos subarreglos (`A[p,...q]` y `A[q + 1,...r]`) recursivamente.

    - Combinar: Ya que los subarreglos son ordenados **in-place**, no es necesario llevar a cabo la tarea de combinar.

---

Basa su funcionamiento en un procedimiento llamado **`PARTITION`**.

## `PARTITION(A, p, r)`

- Precondición: `p` y `r` son índices válidos en el arreglo `A`.

- Poscondicion: `x = A[p]`, se intercambian de posición los datos en `A`, de tal forma que al final los elementos con índice menor a cierto $j$, son menores o iguales que `x`, y aquellos con índice mayor a $j$, son mayores o iguales que `x`.


### Ejemplos

- `PARTITION(A, 1 ,8)` donde `A = [1, 10, 9, 3, 2, 8, 3, 9]`

    ```
    x <- 1
    i <- 0
    j <- 9

    // 1

    i = 1
    j = 1

    // [1, 10, 9, 3, 2, 8, 3, 9] 1 (position 1) <-> 1 (position 1)

    // 2

    i = 2
    j = 0

    // return 0
    ```

- `PARTITION(A, 1 ,8)` donde `A = [5, 5, 5, 5, 5, 5, 5, 5]`

    ```
    x <- 5
    i <- 0
    j <- 9

    // 1

    i = 1
    j = 8

    // [5, 5, 5, 5, 5, 5, 5, 5] 5 (position 1) <-> 5 (position 8)

    .
    .
    .

    // 4

    i <- 4
    j <- 5

    // [5, 5, 5, 5, 5, 5, 5, 5] 5 (position 4) <-> 5 (position 5)

    // 5

    i <- 5
    j <- 4

    // return 4
    ```

- `PARTITION(A, 1 ,8)` donde `A = [10, 1, 9, 3, 2, 8, 3, 7]`

    ```
    x <- 10
    i <- 0
    j <- 9

    // 1

    i <- 1
    j <- 8

    //  [7, 1, 9, 3, 2, 8, 3, 10] 10 (position 1) <-> 7 (position 8)

    // 2

    i <- 8
    j <- 7

    // return 7
    ```

- `PARTITION(A, 1 ,8)` donde `A = [6, 1, 5, 8, 9, 4, 7, 7]`

    ```
    x <- 6
    i <- 0
    j <- 9

    // 1

    i <- 1
    j <- 6

    // [4, 1, 5, 8, 9, 6, 7, 7] 6 (position 1) <-> 4 (position 6)

    // 2

    i <- 4
    j <- 3

    // return 3
    ```

---

## `QUICKSORT(A, p, r)`

- Idea: realizar particiones sucesivas de `A` hasta llegar a particiones triviales que en conjunto dejen ordenado al arreglo `A`.

### Ejemplo

- `PARTITION(A, 1 ,8)` donde `A = [5, 1, 8, 4, 9, 3, 7, 6]`

    ```
    x <- 5
    i <- 0
    j <- 9

    // 1

    i <- 1
    j <- 6

    // [3, 1, 8, 4, 9, 5, 7, 6] 5 (position 1) <-> 3 (position 6)

    // 2

    i <- 3
    j <- 4

    // [3, 1, 4, 8, 9, 5, 7, 6] 8 (position 3) <-> 4 (position 4)

    // 3

    i <- 4
    j <- 3

    // return 3
    ```

    Ahora se aplica `PARTITION` sobre cada arreglo resultante

    > Haciendo la separación a partir del `j` retornado.

    - `PARTITION(A, 1, 3)` donde `A = [3, 1, 4, 8, 9, 5, 7, 6]`

        ```
        x <- 3
        i <- 0
        j <- 4

        // 1

        i <- 1
        j <- 2

        // [1, 3, 4, 8, 9, 5, 7, 6] 3 (position 1) <-> 1 (position 2)

        // 2

        i <- 2
        j <- 1

        // return 1
        ```

        - `PARTITION(A, 1, 1)` donde `A = [1, 3, 4, 8, 9, 5, 7, 6]`

            > Está trivialmente ordenado.

        - `PARTITION(A, 2, 3)` donde `A = [1, 3, 4, 8, 9, 5, 7, 6]`

            ```
            x <- 3
            i <- 1
            j <- 4

            // 1

            i <- 3
            j <- 2

            // return 2
            ```

            - `PARTITION(A, 2, 2)` donde `A = [1, 3, 4, 8, 9, 5, 7, 6]`

                > Está trivialmente ordenado.

            - `PARTITION(A, 3, 3)` donde `A = [1, 3, 4, 8, 9, 5, 7, 6]`

                > Está trivialmente ordenado.

    - `PARTITION(A, 4, 8)` donde `A = [1, 3, 4, 8, 9, 5, 7, 6]`

        ```
        x <- 8
        i <- 3
        j <- 9

        // 1

        i <- 4
        j <- 8

        // [1, 3, 4, 6, 9, 5, 7, 8] 8 (position 4) <-> 6 (position 8)

        // 2

        i <- 5
        j <- 7

        // [1, 3, 4, 6, 7, 5, 9, 8] 9 (position 5) <-> 7 (position 7)

        // 3

        i <- 7
        j <- 6

        // return 6
        ```

        - `PARTITION(A, 4, 6)` donde `A = [1, 3, 4, 6, 7, 5, 9, 8]`

            ```
            x <- 6
            i <- 3
            j <- 7

            // 1

            i <- 4
            j <- 6

            // [1, 3, 4, 5, 7, 6, 9, 8] 6 (position 4) <-> 5 (position 6)

            // 2

            i <- 5
            j <- 4

            // return 4
            ```

            - `PARTITION(A, 4, 4)` donde `A = [1, 3, 4, 5, 7, 6, 9, 8]`

                > Está trivialmente ordenado.

            - `PARTITION(A, 5, 6)` donde `A = [1, 3, 4, 5, 7, 6, 9, 8]`

                ```
                x <- 7
                i <- 4
                j <- 7

                // 1

                i <- 5
                j <- 6

                // [1, 3, 4, 5, 6, 7, 9, 8] 7 (position 5) <-> 6 (position 6)

                // 2

                i <- 6
                j <- 5

                // return 5
                ```

        - `PARTITION(A, 7, 8)` donde `A = [1, 3, 4, 5, 6, 7, 9, 8]`

            ```
            x <- 9
            i <- 6
            j <- 9

            // 1

            i <- 7
            j <- 8

            // [1, 3, 4, 5, 6, 7, 8, 9] 9 (position 7) <-> 8 (position 8)

            // 2

            i <- 8
            j <- 7

            // return 7
            ```

            - `PARTITION(A, 7, 7)` donde `A = [1, 3, 4, 5, 6, 7, 8, 9]`

                > Está trivialmente ordenado.

            - `PARTITION(A, 8, 8)` donde `A = [1, 3, 4, 5, 6, 7, 8, 9]`

                 > Está trivialmente ordenado.

    Terminando con el arreglo `A = [1, 3, 4, 5, 6, 7, 8, 9]`.