---
id: gzvot14se88xtxpbm60casb
title: Counting sort
desc: ''
updated: 1682183476141
created: 1682126031065
---

# Pseudocódigo

```
function counting_sort(A, B, k)
    // Initialization
    for i <- 1 to k
        C[i] <- 0

    // Index counting
    for i <- 1 to length(A)
        C[A[i]] <- C[A[i]] + 1

    // Relative frequency
    for i <- 2 to k
        C[i] <- C[i]  + C[i - 1]

    // Assignation
    for i <- length(A) down to 1
        B[C[A[i]]] <- A[j]

        C[A[i]] <- C[A[i]] - 1
```

# Descripción


1. Crea un vector de números enteros con tantos elementos como valores haya en el intervalo $[0, \text{máximo}]$, y a cada elemento se le da el valor 0 (0 apariciones).

2. Recorrer todos los elementos a ordenar y se cuenta el número de apariciones de cada elemento (usando el vector que hemos creado).

3. Hallar la frecuencia relativa.