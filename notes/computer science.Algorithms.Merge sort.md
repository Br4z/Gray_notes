---
id: 8wmvime0b1ivgv6zrscdt2q
title: Merge sort
desc: ''
updated: 1682984457275
created: 1680827802827
---

# Pseudocódigo

```
// A: array to sort    p: position of the first element (to sort)    r: position of the last element (to sort)
    merge_sort(A, p, r)
1 -     if p < r
2 -         q = floor((p + r) / 2)
3 -         merge_sort(A, p, q)
4 -         merge_sort(A, q + 1, r)
5 -         merge(A, p, q, r)


// q: half position of the array
     merge(A, p, q, r)
1  -     n_1 = q - p + 1 // First half + 1
2  -     n_2 = r - q // second half


         // Auxiliar arrays with an extra position
3  -     L = [1,..., n_1 + 1]
4  -     R = [1,..., n_2 + 1]

5  -     for i = 1 to n_1
6  -         L[i] = A[p + i - 1]

7  -     for j = 1 to n_2
8  -         R[j] = A[q + j]

9  -     L[n_1 + 1] = infinity
10 -     R[n_2 + 1] = infinity

11 -     i = 1
12 -     j = 1

13 -     for k = p to r
14 -         if L[i] <= R[j]
15 -             A[k] = L[i]
16 -             i = i + 1
17 -         else
18 -             A[k] = R[j]
19 -             j = j + 1
```

> El primer llamado sobre un arreglo `A` sería `merge_sor(A, 1, length(A))`.

> La indexación comienza en 1.

# Descripción

Conceptualmente, el ordenamiento por mezcla funciona de la siguiente manera:

1. Si la longitud de la lista es 0 o 1, entonces ya está ordenada. En otro caso:
   1. Dividir la lista desordenada en dos sublistas de aproximadamente la mitad del tamaño.
   2. Ordenar cada sublista **recursivamente** aplicando el ordenamiento por mezcla.
   3. **Mezclar** las dos sublistas en una sola lista ordenada.

![Merge sort demonstration](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_2-1%20Merge_sort_demonstration.gif)