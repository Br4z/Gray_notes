---
id: 60xevl6oc2v4izqarnbrg3t
title: Binary search
desc: ''
updated: 1680988070008
created: 1680828023752
---

La búsqueda binaria funciona en arreglos ordenados. La búsqueda binaria comienza por comparar el elemento del medio del arreglo con el valor buscado. Si el valor buscado es igual al elemento del medio, su posición en el arreglo es retornada. Si el valor buscado es menor o mayor que el elemento del medio, la búsqueda continua en la primera o segunda mitad, respectivamente, dejando la otra mitad fuera de consideración.


# Pseudocódigo

> Se asume que `A` es un arreglo ordena ascendentemente.

```
binary_search(A, x)
    n <- length(A)
    if (x < A[1] or x > A[n])
        return None
        else
            // 1
            left = 1
            right = n
            while (left ≤ right)
                mid <- (left + right) / 2 // 3
                if A[mid] = x // 5
                    return mid
                else if x > A[mid] // 4
                    left <- mid + 1
                else // 5
                    right <-- mid - 1
    return None // 2
```

# Descripción

1. Asignar 0 a `left` y `n` a `right`.
2. Si $\text{left} > \text{right}$, la búsqueda termina sin encontrar el valor.
3. Sea $m$ (la posición del elemento del medio) igual a la parte entera de $\frac{\text{left} + \text{right}}{2}$.
4. Si $A_m < x$, igualar `left` a $m + 1$ e ir al paso 2.
5. Si $A_m > x$, igualar `right` a $m – 1$ e ir al paso 2.
6. Si $A_m = x$, la búsqueda terminó, retornar $m$.