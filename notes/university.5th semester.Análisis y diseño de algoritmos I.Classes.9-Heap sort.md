---
id: u4zzmhdvl43qiwo398qy3il
title: 9-Heap sort
desc: ''
updated: 1688423972568
created: 1682989241597
---

## Idea (heap)

Utilizar las fortalezas del merge sort y del insertion sort.

Utiliza una representación lógica, conocida como heap, de un arreglo que permite ordenar los datos del arreglo **in-place**.

## Heaps

Es un arreglo que puede ser visto como un árbol binario que cumple dos propiedades:

- Orden: la raíz de cada subárbol es mayor o igual que cualquier de sus nodos restantes.

- Forma: la longitud de toda rama es $h$ o $h - 1$, donde $h$ es la altura del árbol. Además, no puede existir una rama de longitud $h$ a la derecha de una rama de longitud $h - 1$.

	> Si existiera una rama de longitud $h$ a la derecha de una de longitud $h - 1$ significaría que el elemento que hace 1 más que $h - 1$ esta en un lugar que no le corresponde.
	>
	> Podríamos decir que se rellenan de "izquierda a derecha".

	![Heap property example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_9-1%20Heap_property_example.jpg)

> La altura de un heap de $n$ elementos es $\Theta(\lg n)$.

### Representación

Los datos se almacenan en un arreglo `A[1,..., heap_size(A)]`

![Heap example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_9-2%20Heap_example.jpg)

`[8, 5, 7, 4, 3, 1, 2]`

En general tenemos que:

- Raíz del árbol: $A_1$

- Padre ($i$): $\left \lfloor \frac{i}{2} \right \rfloor$

- Izquierda ($i$): $A_{2i}$

- Derecha ($i$): $A_{2i + 1}$

> Podemos decir que toda lista ordenada de manera descendente es un heap, pero no en el sentido contrario.

### Operaciones

#### `heapify(A, i)`

```
// Positions
l <- left(i)
r <- right(i)

if l <= heap_size(A) and A[l] > A[i]
	largest <- l
else largest <- i

if r <= heap_size(A) and A[r] > A[largest]
	largest <- r

if largest != i
	exchange A[i] <-> A[largest]
	heapify(A, largest)
```

> La función `heap_size` se encarga de verificar que las posiciones `l` y `r` realmente estén en el heap, es decir, verifica que si no se cumplen las dos condiciones, el nodo que queremos reubicar es una hoja.

- Precondición: subárbol con raíz `izq(i)` y subárbol con raíz `der(i)` son heaps.

- Precondición: subárbol con raíz es un heap.

##### Complejidad (`heapify(A, i)`)

$$
T(n) \leq T \left (2\frac{n}{3} \right ) + \Theta(1) \\[10 pt]

T(n) = O(\lg n)
$$

> $n$ es la altura del árbol.

- $\Theta(1)$: calculo del mayor.
- $T \left (2\frac{n}{3} \right )$: elementos restantes.

##### Ejemplo (`heapify(A, i)`)

- `A = [4, 14, 7, 2, 8, 1]`

	```
	hapify(A, 1) \\ 4

	[14, 4, 7, 2, 8, 1]

	hapify(A, 2) \\ 4

	[14, 8, 7, 2, 4, 1]

	hapify(A, 5) \\ 4

	l = 10 <= heap_size(A)

	[14, 8, 7, 2, 4, 1]
	```

#### `build_heap(A)`

```
heap_size(A) <- length(A)

for i <- floor(length(A) / 2) down to 1
	heapify(A, i)
```

> Todas las hojas son heaps.

> `floor(length(A) / 2)` corresponde al número de nodos internos. Es así porque descartamos los nodos que no pueden tener hijos (tanto izquierdos como derechos).

- Precondición: `A` es un arreglo de elementos.

- Precondición: `A` es un heap.

##### Ejemplo (`build_heap(A)`)

- `A = [5, 7, 10, 1, 4, 6, 8, 2, 9, 12]`

	```
	heapify(A, 5) // 4

	[5, 7, 10, 1, 12, 6, 8, 2, 9, 4]

	heapify(A, 4) // 1

	[5, 7, 10, 9, 12, 6, 8, 2, 1, 4]

	heapify(A, 3) // 10

	[5, 7, 10, 9, 12, 6, 8, 2, 1, 4]

	heapify(A, 2) // 7

	[5, 12, 10, 9, 7, 6, 8, 2, 1, 4]

	heapify(A, 1) // 10

	[12, 9, 10, 5, 7, 6, 8, 2, 1, 4]
	```

##### Complejidad (`build_heap(A)`)

Cada llamado a **heapify** cuesta $O(\lg n)$ y se hacen $O(n)$ llamados, por lo que una estimación sería $O(n\lg n)$.

Aunque lo anterior es lo que nos dice la intuición, podemos demostrar que su verdadera complejidad es $O(n)$, con la ayuda de la siguiente propiedad

$$
\text{En cualquier nivel $h$, el número máximo de nodos es } \left \lceil \frac{n}{2^{h + 1}} \right \rceil
$$

> $n$ es el número total de nodos del árbol.

$$
T(h) = \left \lceil \frac{n}{2^{h + 1}} \right \rceil * O(h)
$$

> Instrucciones asociadas a un nivel del árbol.

$$
T(n) = \sum_{h = 0}^{\lg n} \left \lceil \frac{n}{2^{h + 1}} \right \rceil * O(h)
$$

> Podemos empezar la sumatoria en 1, porque el costo en el nivel 0 es 0, puesto que las hojas ya son heaps.

$$
\sum_{h = 0}^{\lg n} \left \lceil \frac{n}{2^h * 2} \right \rceil (ch) \quad O(h) = ch \\[10 pt]

\frac{cn}{2}\sum_{h = 0}^{\lg n} \frac{h}{2^k} < O \left (\frac{cn}{2}\sum_{h = 0}^{\infty} \frac{h}{2^k} \right ) \quad \sum_{h = 0}^{\infty} \frac{h}{2^k} = 2 \\[10 pt]

T(n) = O \left (\frac{cn}{2} * 2 \right ) = O(cn) = O(n)
$$

#### `heap_sort(A)`

```
build_heap(A)

for i <- length(A) down to 2
	exchange A[1] <-> A[i]
	heap_size(A) <- heap_size(A) - 1
	heapify(A, 1)
```

##### Idea (`heap_sort(A)`)

Aprovechando que el elemento más grande de un heap siempre será la raíz, vamos a:

1. intercambiar el valor de `A[1]` con el valor de `A[heap_size(A)]`.
2. decrementar el valor de `heap_size(A)` en 1.
3. repetir el proceso hasta que `heap_size(A)` sea 1.

##### Ejemplo

- `A = [1, 8, 6, 3, 7, 9, 10, 2, 4]`

	```
	build_heap(A)

	[10, 8, 9, 4, 7, 1, 6, 2, 3]

	// i = 9

	[3, 8, 9, 4, 7, 1, 6, 2, 10]

	heapify(A, 1)

	[9, 8, 6, 4, 7, 1, 3, 2, 10]

	// i = 8

	[2, 8, 6, 4, 7, 1, 3, 9, 10]

	heapify(A, 1)

	[8, 7, 6, 4, 2, 1, 3, 9, 10]

	// i = 7

	[3, 7, 6, 4, 2, 1, 8, 9, 10]

	heapify(A, 1)

	[7, 4, 6, 3, 2, 1, 8, 9, 10]

	// i = 6

	[1, 4, 6, 3, 2, 7, 8, 9, 10]

	heapify(A, 1)

	[6, 4, 1, 3, 2, 7, 8, 9, 10]

	// i = 5

	[2, 4, 1, 3, 6, 7, 8, 9, 10]

	heapify(A, 1)

	[4, 3, 1, 2, 6, 7, 8, 9, 10]

	// i = 4

	[2, 3, 1, 4, 6, 7, 8, 9, 10]

	heapify(A, 1)

	[3, 2, 1, 4, 6, 7, 8, 9, 10]

	// i = 3

	[1, 2, 3, 4, 6, 7, 8, 9, 10]

	heapify(A, 1)

	[2, 1, 3, 4, 6, 7, 8, 9, 10]

	// i = 2

	[1, 2, 3, 4, 6, 7, 8, 9, 10]

	heapify(A, 1)

	[1, 2, 3, 4, 6, 7, 8, 9, 10]
	```

##### Complejidad (`heap_sort(A)`)

- **Build heap** es $O(n)$.
- Llama $n - 1$ veces a **heapify** ($O(\lg n)$).

Su complejidad es $O(n\lg n)$.

### Colas de prioridad

- Es una estructura de datos con servicios de inserción y retiro de elementos con base en una prioridad (valor numérico almacenado en el árbol).

- Se retira (atiende) al elemento con mayor prioridad

#### `heap_maximum(C)`

```
return A[i]
```

> Su complejidad es $\Theta(1)$.

#### `heap_extract_max(C)`

```
if heap_size(C) < 1
    return "heap underflow"

max <- A[1]

A[1] <- A[heap_size(C)]

heap_size(C) <- heap_size(C) - 1

heapify(A, 1)

return max
```

> Su complejidad es $O(\lg n)$ asociado a la ejecución de **heapify**.

#### `heap_increase_key(C, i, key)`

```
if key < A[i]
    throw error "key error"

A[i] <- key

while i > 1 and A[parent(i)] < A[i]
    exchange A[i] <-> A[parent(i)]
    i <- parent(i)
```

> Su complejidad es $O(\lg n)$.

#### `max_heap_insert(C, key)`

```
heap_size(C) <- heap_size(C) + 1
i <- heap_size(C)

while i > 1 and A[parent(i)] < key
    exchange A[i] <-> A[parent(i)]
    i <- parent(i)

A[i] <- key
```

> Hasta ahora no habíamos hecho distinción entre **max** y **min** heap, pero todo lo enunciado anteriormente está hecho para **max heaps**.
