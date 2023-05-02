---
id: u4zzmhdvl43qiwo398qy3il
title: 9-Heap sort
desc: ''
updated: 1682995051575
created: 1682989241597
---

# Idea

Utilizar las fortalezas del merge sort y del insertion sort.

Utiliza una representación lógica, conocida como heap, de un arreglo que permite ordenar los datos del arreglo **in-place**.

# Heaps

Es un arreglo que puede ser visto como un árbol binario que cumple dos propiedades:

- Orden: la raíz de cada subárbol es mayor o igual que cualquier de sus nodos restantes.

- Forma: la longitud de toda rama es $h$ o $h - 1$, donde $h$ es la altura del árbol. Además, no puede existir una rama de longitud $h$ a la derecha de una rama de longitud $h - 1$.

    > Si existiera una rama de longitud $h$ a la derecha de una de longitud $h - 1$ significaría que el elemento que hace 1 mas que $h - 1$ esta en un lugar que no le corresponde.

    ![ejemplo de cuando se incumple]

> La altura de un heap de $n$ elementos es $\Theta(\lg n)$.

## Representación

Los datos se almacenas en un arreglo `A[1,..., heap_size(A)]`

![arbol de ejemplo pag 17]


`[8, 5, 7, 4, 3, 1, 2]`

En general tenemos que:

- Raíz del árbol: $A_1$
- Padre ($i$): $\left \lfloor \frac{i}{2} \right \rfloor$
- Izquierda ($i$): $A_{2i}$
- Derecha ($i$): $A_{2i + 1}$

## Operaciones

### Heapify

```
heapify(A, i)

    l <- left(i)
    r <- right(i)

    if l <= heap_size(A) and A[l] > A[i]
        largest <- l
    else largest <- i

    if r <= heap_size(A) and A[r] > A[largest]
        largest <- r

    if largest != i
        exchange A[i] <-> A[r] > A[largest]
        heapify(A, largest)
```

- Precondición: subárbol con raíz `izq(i)` y subárbol con raíz `der(i)` son heaps.

- Precondición: subárbol con raíz es un heap.

#### Complejidad

$$
T(n) \leq T \left (2\frac{n}{3} \right ) + \Theta(1) \\[10 pt]

T(n) = O(\lg n)
$$

- $\Theta(1)$: calculo del mayor.
- $T \left (2\frac{n}{3} \right )$:
