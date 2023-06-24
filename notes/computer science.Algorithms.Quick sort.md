---
id: jrg14boj8uye0i8617w2f6c
title: Quick sort
desc: ''
updated: 1685735153864
created: 1680902169493
---

## Pseudocódigo

```
     partition(A, p, r)

1  -     x <- A[p]
2  -     i <- p - 1
3  -     j <- r + 1

4  -     while TRUE
5  -        repeat i <- i + 1
6  -        until A[i] >= x

7  -        repeat j <- j - 1
8  -        until A[j] <= x

9  -        if i < j
10 -            exchange A[i] <-> A[j]
11 -        else return j


    quick_sort(A, p, r)
1 -     if p < r

2 -         q <- partition(A, p, r)

3 -     quick_sort(A, p, q)
4 -     quick_sort(A, q + 1, r)
```

> La indexación comienza en 1.

## Descripción

1. Elegir un elemento del conjunto de elementos a ordenar, al que llamaremos **pivote**.

2. Resituar los demás elementos de la lista a cada lado del pivote, de manera que a un lado queden todos los menores que él, y al otro los mayores. Los elementos iguales al pivote pueden ser colocados tanto a su derecha como a su izquierda, dependiendo de la implementación deseada. En este momento, el pivote ocupa exactamente el lugar que le corresponderá en la lista ordenada.

3. La lista queda separada en dos sublistas, una formada por los elementos a la izquierda del pivote, y otra por los elementos a su derecha.

4. Repetir este proceso de forma recursiva para cada sublista mientras estas contengan más de un elemento. Una vez terminado este proceso todos los elementos estarán ordenados.

**Como se puede suponer, la eficiencia del algoritmo depende de la posición en la que termine el pivote elegido**.

- En el mejor caso, el pivote termina en el centro de la lista, dividiéndola en dos sublistas de igual tamaño. En este caso, el orden de complejidad del algoritmo es $O(n\log n)$.

- En el peor caso, el pivote termina en un extremo de la lista. El orden de complejidad del algoritmo es entonces de $O(n^2)$. El peor caso dependerá de la implementación del algoritmo, aunque habitualmente ocurre en listas que se encuentran ordenadas, o casi ordenadas. Pero principalmente depende del pivote, si por ejemplo el algoritmo implementado toma como pivote siempre el primer elemento del array, y el array que le pasamos está ordenado, siempre va a generar a su izquierda un array vacío, lo que es ineficiente.

- En el caso promedio, el orden es $O(n\log n)$.

> No es extraño, pues, que la mayoría de optimizaciones que se aplican al algoritmo se centren en la elección del pivote.

> En la implementación mostrada con el pseudocódigo, nuestro pivote siempre es el primer elemento de la lista.

### Técnicas de elección del pivote

- Tomar un elemento cualquiera como pivote tiene la ventaja de no requerir ningún cálculo adicional, lo cual lo hace bastante rápido. Sin embargo, esta elección "a ciegas" siempre provoca que el algoritmo tenga un orden de $O(n^2)$ para ciertas permutaciones de los elementos en la lista.

- Recorrer la lista para saber de antemano qué elemento ocupará la posición central de la lista, para elegirlo como pivote. Esto puede hacerse en $O(n)$ y asegura que hasta en el peor de los casos, el algoritmo sea $O(n\log n)$. No obstante, el cálculo adicional rebaja bastante la eficiencia del algoritmo en el caso promedio.

- La opción a medio camino es tomar tres elementos de la lista - por ejemplo, el primero, el segundo, y el último - y compararlos, eligiendo el valor del medio como pivote.
