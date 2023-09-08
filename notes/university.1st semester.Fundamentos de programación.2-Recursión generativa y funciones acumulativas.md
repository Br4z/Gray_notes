---
id: p9ktxmn85vu4726zo4pbg2n
title: 2-Recursión generativa y funciones acumulativas
desc: ''
updated: 1692328351612
created: 1690591326104
---

## Recursión estructural vs. generativa

Para un observador (comúnmente el usuario), las funciones son completamente equivalentes; una función tanto en su versión estructural y generativa producen la misma salida, entonces ¿cuándo deberíamos desarrollar una u otra?. La respuesta sencilla es que no lo sabemos, pero comúnmente el desarrollo de una función generativa es más complejo que su versión estructural, pues se es necesario apoyarse en un teorema matemático referente a números. O, una serie de resultados matemáticos de sistemas de ecuaciones (conocimiento que "desbloquea" una nueva perspectiva).

La experiencia muestra que la mayor parte de las funciones en un programa emplean recursión estructural; solamente unas pocas explotan la recursión generativa. Cuando se encuentra con una situación en la que el diseño puede usar tanto recursión estructural como generativa, el mejor enfoque es comenzar con la versión estructural. Si esta es muy lenta, el diseño alternativo usando recursión generativa deberá ser explorado.

### Ordenamiento

- Estructural.

	```JS
	/**
	 * Recursively sorts a list of elements in ascending order.
	 *
	 * @param list - A list of elements with order.
	 * @returns a sorted version of the input list.
	 */

	function structuralSorting(list) {
		/**
		 * Inserts a number "n" into a sorted list in ascending order.
		 *
		 * @param n - The value to be inserted into the list.
		 * @param list - A list sorted in ascending order.
		 * @returns a new list with the element "n" inserted in the correct position.
		 */

		function insert(n, list) {
			if (isEmpty(list)) {
				return cons(n, list)
			} else if (n <= first(list)) {
				return cons(n, list)
			} else {
				return cons(first(list), insert(n, rest(list)))
			}
		}


		if (isEmpty(list)) {
			return list
		} else {
			return insert(first(list), structuralSorting(rest(list)))
		}
	}
	```

- Generativo ([[Quick sort | computer science.Algorithms.Quick sort]]).

	```JS
	/**
	 * Sorts a list of numbers in ascending order using the quick sort algorithm.
	 *
	 * @param list - A list of elements with order.
	 * @returns a sorted version of the input list using the quick sort algorithm.
	 */

	function quickSort(list) {
		/**
		 * Takes a list and a condition, and returns a new list containing only the
		 * elements that satisfy the condition.
		 *
		 * @param list - A list.
		 * @param condition - A function that takes an element from the list as
		 * input and returns a boolean value.
		 * @returns a filtered list based on the given condition.
		 */

		function filter(list, condition) {
			if (isEmpty(list)) {
				return list
			} else if (condition(first(list))) {
				return cons(first(list), filter(rest(list), condition))
			} else {
				return filter(rest(list), condition)
			}
		}


		if (isEmpty(list)) return list
		else {
			const pivot = first(list)
			const smaller = filter(rest(list), x => x <= pivot)
			const greater = filter(rest(list), x => x > pivot)
			return concat(quickSort(smaller), cons(pivot, quickSort(greater)))
		}
	}
	```

### Máximo común divisor

- Estructural.

 ```JS
	/**
	 * Calculates the greatest common divisor (GCD) of two numbers using a structural approach.
	 *
	 * @param a - A number lesser than "b".
	 * @param b - A number greater than "a".
	 * @returns the greatest common divisor (GCD) of the two input numbers "a" and "b".
	 */

	function structuralGCD(a, b) {
		function firstDivisor(divisor) {
			if (i == 1) return 1
			else if (a % i == 0 && b % i == 0) return i
			else return firstDivisor(i - 1)
		}

		return firstDivisor(Math.min(a, b))
	}
 ```

- Generativa.

	```JS
	/**
	 * Calculates the greatest common divisor (GCD) of two numbers using a recursive approach.
	 *
	 * @param a - A number lesser than "b".
	 * @param b - A number greater than "a".
	 * @returns the greatest common divisor (GCD) of the two input numbers "a" and "b".
	 */

	function generativeGCD(a, b) {
		if (b == 0) return a
		else return generativeGCD(b, a % b)
	}
	```

## Acumuladores

En general, agregar un acumulador, es decir, un parámetro que acumula conocimiento, es algo que se agrega a una función después de haberse diseñado, no antes. Las claves para el desarrollo de una función estilo-acumulador son:

1. Reconocer que la función se beneficia de, o requiere, un acumulador.

2. Comprender qué representa el acumulador.

### Ejemplos (acumuladores)

1. Conversión de distancias relativas a absolutas.

	- Sin acumulador.

		1. .

			```JS
			/**
			 * Calculates the absolute distance by summing consecutive elements in a list.
			 *
			 * @param list - A list of numbers.
			 * @returns A modified list, where each distance (element) is the absolute distance of the original distance.
			*/

			function absoluteDistance(list) {
				if (isEmpty(list)) return list
				else if (isEmpty(rest(list))) return [first(list)]
				else {
					const firstElement = first(list)
					const secondElement = first(rest(list))
					const listWithoutTwoFirstElements = rest(rest(list))

					return cons(firstElement, absoluteDistance(cons(firstElement + secondElement, listWithoutTwoFirstElements)))
				}
			}
			```

		2. .

			```JS
			/**
			 * Calculates the absolute distance by summing consecutive elements in a list.
			 *
			 * @param list - A list of numbers.
			 * @returns A modified list where each distance (element) is the absolute distance of the original distance.
			*/

			function absoluteDistance(list) {
				/**
				 * Adds a given number to each element in a list.
				 *
				 * @param number - A number
				 * @param list - A list of distances (numbers).
				 * @returns a new list, where each element is the sum of the corresponding element in the original list
				 * and the given number.
				*/

				function addNumber(number, list) {
					if (isEmpty(list)) {
						return list
					} else {
						return cons(first(list) + number, addNumber(number, rest(list)))
					}
				}


				if (isEmpty(list)) return list
				else return cons(first(list), addNumber(first(list), absoluteDistance(rest(list))))
			}
			```

	- Con acumulador.

		```JS
		/**
		 * Calculates the absolute distance by summing consecutive elements in a list.
		 *
		 * @param list - A list of distances (numbers).
		 * @returns A modified list, where each distance (element) is the absolute distance of the original distance.
		*/

		function absoluteDistance(list, accumulatedDistance = 0) {
			if (isEmpty(list)) return list
			else {
				return cons(first(list) + accumulatedDistance, absoluteDistance(rest(list), accumulatedDistance + first(list)))
			}
		}
		```

2. Función Fibonacci.

	- Sin acumulador.

		```JS
		/**
		 * Calculates the Fibonacci number at a given position using recursion.
		 *
		 * @param position - The position of the Fibonacci number that we want to find.
		 * @returns the Fibonacci number at the given position.
		*/

		function fibonnaci(position) {
			if (position == 1) return 0
			else if (position == 2) return 1
			else return fibonnaci(position - 2) + fibonnaci(position - 1)
		}
		```

	- Con acumulador.

		```JS
		/**
		 * Calculates the Fibonacci number at a given position using recursion.
		 *
		 * @param position - The position of the Fibonacci number that we want to find.
		 * @param [firstElement=0] - The first element of the Fibonacci sequence. By default, it is set to 0.
		 * @param [secondElement=1] - The second element of the Fibonacci sequence. By default, it is set to 1.
		 * @returns the Fibonacci number at the given position.
		*/

		function fibonacci(position, firstElement = 0, secondElement = 1) {
			if (position == 1) return firstElement
			else if (position == 2) return secondElement
			else return fibonacci(position - 1, secondElement, firstElement + secondElement)
		}
		```

3. Función producto de una lista.

	- Sin acumulador.

		```JS
		/**
		 * Calculates the product of all the numbers in a given list.
		 *
		 * @param list - A list of numbers.
		 * @returns the product of all the elements in the given list.
		*/

		function productList(list) {
			if (isEmpty(list)) return 0
			else if (isEmpty(rest(list))) return first(list)
			else return first(list) * productList(rest(list))
		}
		```

	- Con acumulador.

		```JS
		/**
		 * Calculates the product of all the numbers in a given list.
		 *
		 * @param list - A list of numbers.
		 * @param [result=1] - Is used to keep track of the product of the elements in
		 * the list. It is initialized to 1 by default.
		 * @returns the product of all the elements in the given list.
		*/

		function productList(list, result = 1) {
			if (isEmpty(list)) return 0
			else if (isEmpty(rest(list))) return result * first(list)
			else return productList(rest(list), result * first(list))
		}
		```
