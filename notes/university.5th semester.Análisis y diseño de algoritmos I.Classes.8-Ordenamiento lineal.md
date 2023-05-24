---
id: uv8rxw7v5gswqeos0h0k9lt
title: 8-Ordenamiento lineal
desc: ''
updated: 1684890755947
created: 1682124306055
---

La cota mínima de cualquier algoritmo por comparaciones
es $\Omega(n\lg n)$.

> No es posible bajar esa cota si se utilizan comparaciones.

---

Otras estrategias:

- Counting sort
- Radix sort
- Bucket sort

---

![Sorting ways example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_8-1%20Sorting_ways_example.jpg)

- Para ordenar 3 elementos, se tienen 3! posibles caminos.

- La ejecución de un algoritmo de ordenamiento corresponde
a encontrar un camino desde la raíz hasta una hoja.

- Las comparaciones que se deben realizar depende de la altura del árbol, que a su vez dependen del número de elementos que se comparan.

- El peor caso para un algoritmo que se basa en comparaciones está representado por el camino más largo de la raíz a la hoja.

# Demostración

- Teorema: Cualquier árbol de decisión que ordene $n$ elementos
tiene altura $\Omega(n\lg n)$.

    - $n!$ permutaciones $\rightarrow n!$ hojas

    Además, un árbol binario de altura $h$ no tiene más de $2^h$ hojas.

    $$
    n! \leq 2^h \\[10 pt]

    h \geq \lg n! \quad \text{sabemos que } n! \geq \left ( \frac{n}{e} \right )^n\\[10 pt]

    h \geq \lg \left ( \frac{n}{e} \right )^n = n\lg n - n\lg e = \Omega(n\lg n)
    $$

# [[computer science.Algorithms.Counting sort]]

Asume que cada uno de los $n$ elementos a ordenar es un
número entero entre 1 y $k$ ($k$ siendo $O(n)$).

- Idea: contar para cada elemento $x$, los elementos que son
menores que el.

---

Se utilizan tres arreglos

- `A[1,..., n]`: datos de entrada
- `B[1,..., n]`: mantiene la salida
- `C[1,..., k]`: mantiene los conteos

## Ejemplo

- `counting_sort([3, 6, 4, 1, 3, 4, 1, 4], [1,..., 8], 6)`

    ```
    B = [x, x, x, x, x, x, x, x]
    C = [2, 0, 2, 3, 0, 1] -> [2, 2, 4, 7, 7, 8]

    // 8

    B = [x, x, x, x, x, x, 4, x]
    C = [2, 2, 4, 6, 7, 8]

    // 7

    B = [x, 1, x, x, x, x, 4, x]
    C = [1, 2, 4, 6, 7, 8]

    // 6

    B = [x, 1, x, x, x, 4, 4, x]
    C = [1, 2, 4, 5, 7, 8]

    // 5

    B = [x, 1, x, 3, x, 4, 4, x]
    C = [1, 2, 3, 5, 7, 8]

    // 4

    B = [1, 1, x, 3, x, 4, 4, x]
    C = [0, 2, 3, 5, 7, 8]

    // 3

    B = [1, 1, x, 3, 4, 4, 4, x]
    C = [0, 2, 3, 4, 7, 8]

    // 2

    B = [1, 1, x, 3, 4, 4, 4, 6]
    C = [0, 2, 3, 4, 7, 7]

    // 1

    B = [1, 1, 3, 3, 4, 4, 4, 6]
    C = [0, 2, 2, 4, 7, 7]
    ```

## Complejidad

- Línea 1 - 2: $O(k)$
- Línea 3 - 4: $O(n)$
- Línea 5 - 6: $O(k)$
- Línea 7 - 8: O(n)

$$
T(n) = O(2n + 2k) \quad k = O(n) \quad T = O(n)
$$

## Estabilidad

Este algoritmo es estable, números con el mismo valor, aparecen en el mismo orden en el arreglo de salida.

# `radix_sort(A, d)`

```
for i <- 1 to d
    sort array A on digit i
```

> El ordenamiento lo hace con el counting sort.

![Radix sort example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_8-2%20Radix_sort_example.jpg)

Se asume que los $n$ elementos del arreglo tienen `d` dígitos donde el dígito 1 es el menos significativo.

## Complejidad

$$
T(n) = O(d * (n + k)) = O(n)
$$

# `bucket_sort(A)`

```
n <- length(A)

for i <- 1 to n
    insert A[i] into list B[floor(n * A[i])]

for i <- to n - 1
    sort list B[i] with insertion sort

concatenate(B[0], B[1],...,B[n - 1])
```

Se asume que la entrada es un conjunto de $n$ números reales en el intervalo $[0,1)$, es decir:

- Entrada: `A[1,...,n]` $0 \leq A[i] < 1$

    > Se necesitan además un arreglo `B[0,..., n - 1]` de listas enlazadas.

## Idea

- Dividir el intervalo, en $n$ subintervalos de igual tamaño (buckets) y distribuir los $n$ números de entrada en los buckets.

- Ordenar cada bucket con insertion sort y luego concatenar los resultados en cada bucket.

---

Como la distribución es uniforme, se espera que los buckets tengan aproximadamente la misma cantidad de elementos.

![Bucket sort example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_8-3%20Bucket_sort_example.jpg)