---
id: gzvot14se88xtxpbm60casb
title: Counting sort
desc: ''
updated: 1688944564511
created: 1682126031065
---

## Pseudocódigo

```
    counting_sort(A, B, k)
        // Initialization
1 -     for i <- 1 to k
2 -         C[i] <- 0

        // Index counting
3 -     for i <- 1 to A.length
4 -         C[A[i]] <- C[A[i]] + 1

        // Relative frequency
5 -     for i <- 2 to k
6 -         C[i] <- C[i]  + C[i - 1]

        // Assignation
7 -     for i <- A.length down to 1
8 -         B[C[A[i]]] <- A[i]
9 -         C[A[i]] <- C[A[i]] - 1
```

> La indexación comienza en 1.

## Descripción

1. Crea un vector de números enteros con tantos elementos como valores haya en el intervalo $[0, \text{máximo}]$, y a cada elemento se le da el valor 0 (0 apariciones).

2. Recorrer todos los elementos a ordenar y se cuenta el número de apariciones de cada elemento (usando el vector que hemos creado).

3. Hallar la frecuencia relativa.

4. Asignar los valores de `A` al arreglo `B` según su frecuencia relativa y restándole 1 a esa frecuencia en cada iteración.
