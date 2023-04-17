---
id: 8wmvime0b1ivgv6zrscdt2q
title: Merge sort
desc: ''
updated: 1681502746780
created: 1680827802827
---

# Pseudocódigo

```
// A: array to sort    p: position of the first element (to sort)    r: position of the last element (to sort)
function merge_sort(A, p, r)
    if p < r
        q = floor((p + r) / 2)
        merge_sort(A, p, q)
        merge_sort(A, q + 1, r)
        merge(A, p, q, r)


// q: half position of the array
function merge(A, p, q, r)
    n_1 = q - p + 1 // First half + 1
    n_2 = r - q // second half


    // Auxiliar arrays with an extra position
    L = [1,..., n_1 + 1]
    R = [1, ..., n_2 + 1]

    for i = 1 to n_1
        L[i] = A[p + i - 1]

    for j = 1 to n_2
        R[j] = A[q + j]

    L[n_1 + 1] = infinity
    R[n_2 + 1] = infinity

    i = 1
    j = 1

    for k = p to r
        if L[i] <= R[j]
            A[k] = L[i]
            i = i + 1
        else
            A[k] = R[j]
            j = j + 1
```

> El primer llamado sobre un arreglo `A` sería `merge_sor(A, 1, length(A))`.

# Descripción

Conceptualmente, el ordenamiento por mezcla funciona de la siguiente manera:

1. Si la longitud de la lista es 0 o 1, entonces ya está ordenada. En otro caso:
   1. Dividir la lista desordenada en dos sublistas de aproximadamente la mitad del tamaño.
   2. Ordenar cada sublista **recursivamente** aplicando el ordenamiento por mezcla.
   3. **Mezclar** las dos sublistas en una sola lista ordenada.

![Merge sort demonstration](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_2-1%20Merge_sort_demonstration.gif)