---
id: a7g0m20nphyy8j7dsccct60
title: 3-Ejercicios - Árboles binarios de búsqueda
desc: ''
updated: 1688437763718
created: 1687223901970
---

1. Argumente que, si un nodo en un árbol binario de búsqueda tiene dos hijos, entonces su sucesor no tiene hijo izquierdo y su predecesor no tiene hijo derecho.

	El sucesor de un nodo es el siguiente nodo (al nodo que le estamos hallando el sucesor) siguiendo un recorrido **in-order**. La única diferencia en la definición con el antecesor es que para este, nos referiremos al nodo anterior del recorrido **in-order**.

	Entonces, partiendo de la suposición de la existencia de un $A$ y $B$ (sucesor y predecesor, respectivamente) de nodos arbitrarios, si $A$ tuviera hijo izquierdo significaría que existe un elemento menor que el, por lo que no podría ser el sucesor, y, por lo tanto, no es compatible con esta primera suposición. Lo mismo sucede en el caso del antecesor, si $B$ tuviera hijo derecho significaría que existe un elemento mayor que el, por lo que no podría ser el antecesor, y en consecuencia no es compatible con esta segunda parte de la suposición. Queda demostrado que ambos casos no son posibles en nuestras suposiciones, por lo que lo enunciado es verdadero.

2. Así como es posible generar el listado con los elementos ordenados a partir de un árbol binario de búsqueda con costo lineal, ¿Es posible a partir de un heap generar el listado con los elementos ordenados con costo lineal? ¿Sí esto fuera posible, cómo afectaría esto al costo de ordenar usando montículos?

	La primera afirmacion se justifica en el recorrido **in-order** de una ABB. Enunciar una mejor [[complejidad | university.5th semester.Análisis y diseño de algoritmos I.Classes.9-Heap sort#Complejidad-heap_sortA]] a la que ya enuncia el procedimiento `heap_sort` podría considerarse justificación suficiente.

3. Es posible ordenar un conjunto de $n$ números construyendo un árbol binario de búsqueda aplicando la función insert repetidamente y entonces generando el listado in-order (lo anterior como fue visto en clase).

	- ¿Cuál sería el pseudocódigo de este algoritmo?

		Aplicaríamos el procedimiento [[`tree_insert` | university.5th semester.Análisis y diseño de algoritmos I.Classes.12-Árboles binarios de búsqueda#tree_insertT-z]] a todos los elementos partiendo de un árbol vacío, para posteriormente retornar el recorrido **in-roder** (lista ordenada).

		```
		sort(n)
			tree = NIL

			for i = 1 to n
				insert(tree, n[i])

			return inorder_walk(tree)
		```

	- ¿Cuál sería el orden de complejidad?

		Tanto en el mejor como en el peor caso la complejidad es $O(n) * n + O(n) = O(n^2)$ (la suma de la complejidad del ciclo y la del `inorder_walk` respectivamente).

4. Muestre que cualquier árbol binario de búsqueda con $n$ nodos puede ser transformado en cualquier otro árbol binario de búsqueda con los mismos $n$ nodos usando $O(n)$ rotaciones.

	> Ayuda: Primero se puede demostrar que con máximo $n - 1$ rotaciones hacia la derecha se pueden transformar cualquier árbol binario de búsqueda con $n$ nodos en un árbol binario de búsqueda que corresponde a una cadena extendida hacia la derecha.

	Partiendo de la ayuda como verdadera, podemos decir que un ABB arbitrario $B$ tras máximo $n - 1$ rotaciones hacia la derecha puede terminar como una cadena extendida hacia la derecha, lo que implica a su vez que con $n - 1$ rotaciones hacia la izquierda se puede volver al ABB original (un ABB arbitrario).
