---
id: agwjzjjlqqa0vvefcuewoms
title: 4-Ejercicios - Arreglos
desc: ''
updated: 1688495368920
created: 1688437923408
---

1. El k-ésimo elemento.

	- Entrada: Un entero positivo $k$ y dos arre

	- Salida: el k-ésimo elemento más pequeño entre todos los elementos que hay en `a` como en `b`.

	Podriamos usar el procedimiento `merge` del [[`merge_sort` | computer science.Algorithms.Merge sort]], pero con modificaciones:

	```
	k_element(n, a, b)
		merge(a, b)
			n = a.length
			r = [1, ..., 2 * n]

			a[n + 1] = infinity
			b[n + 1] = infinity

			i = 1
			j = 1

			for i = 1 to (2 * n)
				if a[i] <= b[j]
					r[i] = L[i]
					i = i + 1
				else
					A[i] = b[j]
					j = j + 1
			return r
		return merge(a,b)[n]
	```

	La complejidad de `k_elemet` es `O(n)` (la del procedimiento `merge`).

2. Un elemento mayoría.

	- Entrada: un arreglo `a[1, ..., n]` de valores, donde estos valores no tienen  un orden entre sí, es decir, los valores del arreglo no se pueden ordenar ni se puede decir que un elemento es mayor que otro. Lo que sí se puede hacer es comparar si un elemento es igual a otro ($=$). Asuma que el tamaño del arreglo es potencia de 2.

	- Salida: un valor del arreglo si este valor corresponde al valor de la mayoría de los elementos del arreglo.

	```
	majority_element(a)
		i = 0

		for j = 1 to a.length
			if i = 0 // Initialization
				element = a[j]
				i = 1
			else
				if elemen = a[j]
					i++
				else i--

		return element
	```

	Algoritmo con un costo $O(n)$, pero si se hubiera querido un acercamiento **divide y vencerás**, pudo haberse considerado el siguiente algoritmo:

	```
	majority_element(a)
		n = a.lenght

		if a.lenght = 1
			return a[1]

		left_majority = majority_element(a[1, ..., n/2])
		right_majority = majority_element(a[n/2, ..., n])

		left_majority_count = 0
		right_majority_count = 0

		for i = 1 to n
			if left_majority = a[i]
				left_majority_count++

		for i = 1 to n
			if right_majority = a[i]
				right_majority_count++

		if left_majority_count > n / 2
			return left_majority

		if right_majority_count > n / 2
			return right_majority_count

		return "There isn't a majority element"
	```

	La complejidad de este algoritmo es de $O(n\log_2 n)$.

3. Par complementario de elementos en un arreglo.

	- Entrada: un arreglo de enteros diferentes, cuyos valores pueden ser negativos o positivos, ordenado ascendentemente de tamaño $n$ (el tamaño del arreglo es mayor o igual a 1).

	- Salida: `true`, si en el arreglo de entrada hay al menos un par de elementos cuya suma sea 0. `false`, en cualquier otro caso.

	```
	complementary_pair(a)
		i = 1
		j = a.lenght

		while (i != j)
			if a[j] - a[i] > 0 // a[j] > a[i]
				j--
			else if a[j] - a[i] < 0 // a[i] > a[j]
				i++
			else return true // a[j] - a[i] = 0

		return false
	```

	Recorriendo el arreglo por los extremos y con la ayuda de dos contadores (`i` y `j`), encontraremos esa pareja complementaria si es que existe. La complejidad del algoritmo es $O(n)$.

	> El algoritmo explota el hecho de que la entrada está **ordenada ascendentemente**.
