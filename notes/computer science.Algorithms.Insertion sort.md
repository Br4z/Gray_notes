---
id: jhnvwja7ajs8cpo65902x4m
title: Insertion sort
desc: ''
updated: 1682186097068
created: 1680827617976
---

# Pseudocódigo

```
1 -    function insertion_sort(A)
2 -        for j <- 2 to length[A]
3 -            do key <- A[j]
4 -            i <- j - 1

5 -            while i > 0 and A[i] > key
6 -                do A[i + 1] <- A[i]
7 -                i <- i - 1

8 -        A[i + 1] <- key
```

# Descripción

Inicialmente, se tiene un solo elemento, que obviamente es un conjunto ordenado. Después, cuando hay $k$ elementos ordenados de menor a mayor, se toma el elemento $k + 1$ y se compara con todos los elementos ya ordenados, deteniéndose cuando se encuentra un elemento menor (todos los elementos mayores han sido desplazados una posición a la derecha) o cuando ya no se encuentran elementos (todos los elementos fueron desplazados y este es el más pequeño). En este punto se inserta el elemento $k + 1$ debiendo desplazarse los demás elementos.