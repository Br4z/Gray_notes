---
id: uv8rxw7v5gswqeos0h0k9lt
title: 8-Ordenamiento lineal
desc: ''
updated: 1682125960723
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

- Las comparaciones que se deben realizar depende de la altura del árbol, que a su vez dependen del numero de elementos que se comparan.

- El pero caso para un algoritmo que se basa en comparaciones esta representado por el camino mas largo de la raíz a la hoja.

# Demostración

- Teorema: Cualquier árbol de decisión que ordene $n$ elementos
tiene altura $\Omega(n\lg n)$.


    - $n!$ permutaciones $\rightarrow n!$ hojas

    Además, un árbol binario de altura $h$ no tiene más de $2^h$ hojas.

    $$
    n! \leq 2^h \\[10 pt]

    h \geq \lg n! \quad \text{sabemos que $n! \geq \left ( \frac{n}{e} \right )^n$}\\[10 pt]

    h \geq \lg \left ( \frac{n}{e} \right )^n = n\lg n - n\lg e = \Omega(n\lg n)
    $$

## Counting sort

Asume que cada uno de los $n$ elementos a ordenar es un
número entero entre 1 y $k$ ($k$ siendo $O(n)$).

- Idea: contar para cada elemento $x$, los elementos que son
menores que el.

---

Se utilizan tres arreglos

- `A[1, ..., n]`: datos de entrada
- `B[1, ..., n]`: mantiene la salida
- `C[1, ..., k]`: mantiene los conteos