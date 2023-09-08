---
id: 39vk3u5jb8n7two0vb6ejk5
title: 12-Árboles binarios de búsqueda
desc: ''
updated: 1688521624172
created: 1685237582370
---

Es un árbol binario en el cual se cumple que, para cada nodo $x$, los nodos del subárbol izquierdo son menores o iguales a $x$ y que, los nodos del subárbol derecho son mayores o iguales a $x$.

![Binary search tree example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_12-1%20Binary_search_tree_example.jpg)

## Propiedad

Sea $x$ un nodo del árbol. Si $y$ es un nodo en el subárbol izquierdo de $x$, entonces `y.key <= x.key`. Si y es un nodo en el subárbol derecho de x, entonces `y.key >= x.key`.

---

Si son recorridos en **inorden**, producen una lista de las llaves ordenada ascendentemente.

```
inorder_walk(x)
	if x != NIL
		inorder_walk(x.left)
		print x.key
		inorder_walk(x.right)
```

La complejidad del algoritmo es $\Theta(n)$.

> Hace una impresión por cada uno de los nodos en el árbol.

## Consultas

En un árbol binario (y en general en los árboles) podemos consultar los siguientes datos:

- Llave.
- Mínimo.
- Máximo.
- Sucesor de un nodo.
- Predecesor de un nodo.

Cada una de estas operaciones se puede hacer en $O(h)$.

> $h$ es la altura del árbol.

### `tree_search(x)`

Buscar un nodo con llave $k$ dado un árbol con apuntador a la raíz $x$.

```
if x = nil or k = x.key
	return x
if k < x.key
	return tree_search(x.left, k)
else return tree_search(x.right, k)
```

Un código para la versión iterativa podría ser el siguiente:

```
while x = NIL or k = x.key
	if k < x.key
		x <- x.left
	else x <- x.right
```

### `tree_minimun(x)`

La idea es seguir los apuntadores al hijo izquierdo desde la raíz hasta que se encuentre con `NIL`.

```
if x.left = NIL
    return x
else tree_minimun(x.left)
```

Su complejidad es $O(h)$ que en ABB es equivalente a $O(h)$.

### `tree_maximum(x)`

La idea es seguir los apuntadores al hijo derecho desde la raíz hasta que se encuentre `NIL`.

```
if x.right = NIL
	return x
else tree_minimun(x.right)
```

Su complejidad es $O(h)$ que en ABB es equivalente a $O(h)$.

### `tree_successor(x)`

Dado un nodo $x$ donde `x.key = k`, el sucesor de `x` es el nodo $y$ tal que `y.key` es la llave más pequeña, mayor que $k$ (considerando que todos los elementos fueran diferentes).

> En general, considerando que haya valores repetidos, el sucesor sería el siguiente nodo ubicado a su derecha usando **inorden**.

```
if x.right != NIL
	return tree_minimum(x.right)

y <- x.parent

while y != NIL and x = y.right
	x <- y
	y <- y.parent

return y
```

En el código consideramos los siguientes casos:

- El sucesor de $x$ (si existe) es el nodo más izquierdo del subárbol derecho de $x$; este nodo es el mínimo en el subárbol enraizado en $x$.

- Si el subárbol derecho no existe, el sucesor de $x$ (si existe) es el ancestro más bajo de $x$ cuyo hijo izquierdo también sea ancestro de $x$.

Su complejidad es $O(h)$ que en ABB es equivalente a $O(n)$.

### `tree_insert(T, z)`

```
y <- NIL
x <- T.root

while x != NIL
	y <- x // Save the previous node

	if z.key < x.key
		x <- x.left
	else x <- x.right

z.parent <- y

if y = nil
	T.root <- z
else if z.key < y.key
	y.left <- z
else y.right <- z
```

Empezando un recorrido desde la raiz, vamos a llegar a el nodo hoja que le corresponde ser el padre de nuestro nodo insertado.

Su complejidad es $O(h)$ que en ABB es equivalente a $O(n)$.

### `tree_delete(T, z)`

```
if z.left = NIL or z.right = NIL
	y <- z
else y <- tree_sucessor(z) // Have two childs

if y.left != NIL
	x <- y.left
else x <- y.right

if x != NIL
	x.parent <- y.parent

if y.parent = NIL
	T.root <- x
else if y = y.parent.left
	y.parent.left <- x
else y.parent.right <- x

if y != z
	z.key <- y.key

return y
```

- Casos.

	- 1: el nodo a borrar no tiene hijos.

		Por diferencia, el caso más fácil, puesto que nos referimos a una hoja y lo único que tenemos que hacer es que el apuntador al padre de `z` sea `NIL`.

	- 2: el nodo a borrar tiene un solo hijo.

		Se reemplaza el nodo con su hijo.

	- 3: el nodo a borrar tiene dos hijos.

		Se "reemplaza" el nodo con su sucesor.

		> Es la única forma en conservar las propiedades del ABB.
