---
id: jhnvwja7ajs8cpo65902x4m
title: Insertion sort
desc: ''
updated: 1682186097068
created: 1680827617976
---

# Pseudocódigo

```
    insertion_sort(A)
1 -     for j <- 2 to length[A]
2 -         key <- A[j]
3 -         i <- j - 1

4 -     while i > 0 and A[i] > key
5 -         A[i + 1] <- A[i]
6 -         i <- i - 1

7 -     A[i + 1] <- key
```

# Descripción

Inicialmente, se tiene un solo elemento, que obviamente es un conjunto ordenado. Después, cuando hay $k$ elementos ordenados de menor a mayor, se toma el elemento $k + 1$ y se compara con todos los elementos ya ordenados, deteniéndose cuando se encuentra un elemento menor (todos los elementos mayores han sido desplazados una posición a la derecha) o cuando ya no se encuentran elementos (todos los elementos fueron desplazados y este es el más pequeño). En este punto se inserta el elemento $k + 1$ debiendo desplazarse los demás elementos.