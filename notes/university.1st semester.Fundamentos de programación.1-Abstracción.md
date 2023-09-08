---
id: uwo3wvsh780nw0zjxoj8ngp
title: 1-Abstracción
desc: ''
updated: 1692329568147
created: 1690291566268
---

## Similitud en funciones

### Ejercicio 49

Abstraer las siguientes dos funciones en, una:

1. `max`.

	```JS
	/**
	* Recursively finds the maximum value in a list.
	*
	* @param list - A list of numbers or any objects with order.
	* @returns the maximum value from the given list.
	*/

	function max(list) {
		if (length(list) == 1) return first(list)
		else {
			if (first(list) < max(rest(list))) return first(list)
			else return max(rest(list))
		}
	}
	```

2. `min`.

	```JS
	/**
	* Recursively finds the minimum value in a list.
	*
	* @param list - A list of numbers or any objects with order.
	* @returns the minimum value from the given list.
	*/

	function min(list) {
		if (length(list) == 1) return first(list)
		else {
			if (first(list) < min(rest(list))) return first(list)
			else return min(rest(list))
		}
	}
	```

```JS
/**
 * Recursively compares elements in a list using a comparator function and
 * returns the element that satisfies the comparator condition.
 *
 * @param list - A list of numbers or any objects that can be compared.
 * @param comparator - A function that takes in two elements and returns
 * a boolean value. It is used to compare two elements and determine their order.
 * @returns the element from the list that satisfies the given comparator function.
 */

function getElement(list, comparator) {
	if (length(list) == 1) return first(list)
	else {
		const firstElement = first(list)
		const anotherElement = getElement(rest(list), comparator)

		if (comparator(firstElement, anotherElement)) return first(list)
		else return anotherElement
	}
}
```

- `getElement(list, (a, b) => a > b)`: hallar el número mayor.

- `getElement(list, (a, b) => a < b)`: hallar el número menor.

Como es normal en las funciones recursivas, tenemos un gran costo espacial relacionado con la longitud (cantidad de elementos) de la lista ingresada.

## Similitud en definiciones de datos

### Problema 1

1. Implemente una función que eleva al cuadrado cada uno de los elementos de una lista: `map(list, x => x * x)`.

2. Implemente una función que convierte a negativo cada uno de los elementos de una lista: `map(list, x => -1 * x)`.

3. Implemente una función que retorne la longitud de cada uno de los elementos de una lista: `map(list, x => length(x))`.

	> `length` siendo una implementación genérica.

### Problema 2

1. Implemente una función que retorne el producto de los elementos de la lista: `reduce(list, (accumulated, element) => accumulated * element, 1)`.
