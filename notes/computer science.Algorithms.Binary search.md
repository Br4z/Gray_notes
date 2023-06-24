---
id: 60xevl6oc2v4izqarnbrg3t
title: Binary search
desc: ''
updated: 1685735127998
created: 1680828023752
---

La búsqueda binaria funciona en arreglos ordenados. La búsqueda binaria comienza por comparar el elemento del medio del arreglo con el valor buscado. Si el valor buscado es igual al elemento del medio, su posición en el arreglo es retornada. Si el valor buscado es menor o mayor que el elemento del medio, la búsqueda continua en la primera o segunda mitad, respectivamente, dejando la otra mitad fuera de consideración.

## Pseudocódigo

> Se asume que `A` es un arreglo ordena ascendentemente.

```
     binary_search(A, x)
1  -     n <- length(A)
2  -     if (x < A[1] or x > A[n])
3  -          return None
4  -     else
             // 1 step
5  -         left = 1
6  -         right = n
7  -         while (left ≤ right)
8  -             mid <- (left + right) / 2 // 3 step
9  -             if A[mid] = x // 5 step
10 -                 return mid
11 -             else if x > A[mid] // 4 step
12 -                 left <- mid + 1
13 -             else // 5 step
14 -                 right <-- mid - 1
15 -     return None // 2 step
```

## Descripción

1. Asignar 0 a `left` y `n` a `right`.
2. Si $\text{left} > \text{right}$, la búsqueda termina sin encontrar el valor.
3. Sea $m$ (la posición del elemento del medio) igual a la parte entera de $\frac{\text{left} + \text{right}}{2}$.
4. Si $A_m < x$, igualar `left` a $m + 1$ e ir al paso 2.
5. Si $A_m > x$, igualar `right` a $m – 1$ e ir al paso 2.
6. Si $A_m = x$, la búsqueda terminó, retornar $m$.