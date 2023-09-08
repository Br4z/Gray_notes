---
id: g6maib7q814fiy1m5jv017h
title: 11-Árboles rojinegros
desc: ''
updated: 1688506694653
created: 1684259551958
---

Un árbol rojinegro es un árbol de búsqueda binario en el que cada nodo tiene un bit extra para almacenar su color.

![Red and black tree example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_11-1%20Red_black_tree_example.jpg)

---

En los árboles rojinegros se colocan las referencias a nil como nodos de color negro.

![Red and black tree property](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_11-2%20Red_black_tree_property.jpg)

## Propiedades

1. Todo nodo es rojo o negro (tiene color).

2. Toda hoja (nil) es negra.

3. La raíz es negra.

4. Si un nodo es rojo, entonces sus hijos son negros.

5. Cada camino de un nodo a sus hojas descendiente contiene el mismo numero de nodos negros.

## `black_height(x)`

La altura negra de un nodo `x`, es el numero de nodos negros de cualquier camino desde el nodo `x` (no incluido) hasta una hoja.

Un árbol rojinegro con $n$ nodos internos tiene altura, a lo más, de $2\lg (n + 1)$

> Esto en el caso de que haya nodos rojos y negros intercalados.

> La regla 5 es la que asegura una mayor uniformidad (comparado al árbol binario) en el árbol.

## Operaciones

Antes de definir las convencionales, es necesario definir algunas nuevas para no violar las reglas después de aplicar alguna operación básica.

### `left_rotate(T, y)`

![Left rotate](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_11-3%20Left_rotate.jpg)

```
y <- x.right
x.right <- y.left
y.left.p <- x
y.p <- x.p

if x.p = NIL
	T.root <- y
else if x = x.p.left
	x.p.left <- y
else x.p.right <- y

y.left <- x
x.p <- y
```

La complejidad es $O(1)$.

#### Ejemplo (`left_rotate`)

- `left_rotate(T,4)` con el siguiente árbol:

	![Left rotate example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_11-5%20Left_rotate_example.jpg)

### `right_rotate(T, x)`

![Right rotate](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_11-4%20Right_rotate.jpg)

```
y <- x.left
x.left <- y.right
y.left.p <- x
y.p <- x.p

if x.p = NIL
	T.root <- y
else if x = x.p.left
	x.p.left <- y
else x.p.right <- y

y.right <- x
x.p <- y
```

### `RB_insert(T, x)`

Se usa el procedimiento `tree_insert` y se colorea `x` de rojo. Luego se modifica el árbol recoloreando nodos y haciendo rotaciones.

### Casos

1. El padre de `x` y su tío (`x.granparent.left`) son rojos.

	- Se pintan de negro tanto el padre como el tío

	- El abuelo de `x` queda entonces de rojo.

2. El padre de `x` es rojo, pero su tío (`x.grandparent.left`) es negro y `x` es hijo derecho de su padre (`x.parent.right = x`).

	- Se rota a la izquierda `x.parent` (`left_rotate(T, x.parent)`).

3. El padre de `x` es rojo, pero su tío `x.granparent.right` es negro y `x` es hijo izquierdo de su padre (`x.parent.left = x`).

	- Se cambian los colores de `x.parent` y `x.granparent`.

	- Se rota a la derecha `x.granparent` (`left_rotate(T, x.granparent)`).

4. El padre de `x` y su tío (`x.granparent.right`) son rojos.

	- Se pintan de negro tanto el padre como el tío

	- El abuelo de `x` queda entonces de rojo.
