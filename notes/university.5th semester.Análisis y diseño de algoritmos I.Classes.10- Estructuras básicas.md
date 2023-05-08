---
id: jnvgzkqvk42m7jpr6uoec8u
title: 10- Estructuras básicas
desc: ''
updated: 1683484702582
created: 1683484669391
---

# Pila

Es una estructura de datos tipo LIFO (Last In First Out), por lo que el último elemento insertado será el primero en ser borrado.

Sus operaciones básicas son:

- `is_empty(S)`
- `push(S, x)`
- `pop(S)`

---

Una forma de implementar la pila es por medio de un arreglo unidimensional.

Esto supone varios aspectos:

- La pila tiene una capacidad limitada.

- Se cuenta con un atributo adicional, llamado `top`, que almacena el índice en el arreglo que guarda el último valor, esto es, el tope de la pila.

- Cuando la pila esté vacía, `top = 0`.

## Operaciones

### `is_empty(S)`

```
if S.top == 0
    return true
else return false
```

Su complejidad es $O(1)$.

### `push(S, x)`

```
if S.top = S.size
    throw error "overflow"

S.top = S.top + 1
S[S.top] = x
```

Su complejidad es $O(1)$.

### `pop(S)`

```
if is_empty(S)
    throw error "underflow"
else
    S.top = S.top - 1
    return S[S.top + 1]
```

Su complejidad es $O(1)$.

# Cola

Es una estructura de datos tipo LIFO (Last In First Out), por lo que el último elemento insertado será el primero en ser borrado.

Sus operaciones básicas son:

- `enqueue(Q, x)`
- `dequeue(Q)`

---

Una forma de implementar la cola es por medio de un arreglo unidimensional.

Esto supone varios aspectos:

- La cola tiene una capacidad limitada.

- Se cuenta con dos atributos adicionales, `head` que guarda el índice de la cabeza y `tail` que apunta al siguiente lugar en el cual será insertado un elemento.

---

- Sabemos que la cola está llena cuando `tail + 1 = head`.

- Inicialmente `tail = head = 1`.

## Operaciones

### `enqueue(Q, x)`

```
1 - Q[Q.tail] <- x

2 - if Q.tail = Q.length
3 -     Q.tail = 1
4 - else Q.tail <- Q.tail + 1
```

La línea 4 es por si nos quedamos sin espacio al final de arreglo, pero si tenemos espacio al principio, entonces, los elementos que sean "encolados" se ubicaran al principio del arreglo.

> Recordemos que la implementación de todas estas estructuras pueden verse como objetos con sus atributos e interfaces.

### `dequeue(Q)`

```
1 - x <- Q[Q.head]

2 - if Q.head = Q.length
3 -     Q.head = 1
4 - else Q.head = Q.head + 1

5 - return x
```

La línea 2 es por si vamos a desencolar al último de la lista, lo que dejaría la cabeza al comienzo.

> Note no estamos borrando el contenido de lo que era la cabeza (el elemento asociado a esa posición), solo se cambia el valor de `head` (lo que deja la posibilidad de que dicho elemento anterior se sobrescriba).