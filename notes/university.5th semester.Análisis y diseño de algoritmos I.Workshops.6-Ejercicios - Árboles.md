---
id: 9bcjuzmsv5lefq2n9vhpjvi
title: 6-Ejercicios - Árboles
desc: ''
updated: 1688527053970
created: 1688507009179
---

1. Indique cuál de las siguientes secuencias que representan las inserciones de números, en ese orden, en un árbol binario de búsqueda inicialmente vacío daría el árbol más balanceado.

	- 8, 10, 4, 9, 12, 1 y 6.

		Es un arbol completamente balanceado.

2. Una y sólo una de las siguientes afirmaciones es verdadera, indique cuál es:

	- El costo de construir un árbol binario de búsqueda a partir de una lista de $n$ números tal que todos los elementos queden en el árbol es $O(n)$.

		Falso, sabiendo que el costo del procedimiento [[`insert` | university.5th semester.Análisis y diseño de algoritmos I.Classes.12-Árboles binarios de búsqueda#tree_insertT-z]] es $O(h) = O(n)$, estaríamos hablando de un costo total $O(n^2)$ si se hace este procedimiento sobre cada elemento.

	- El costo de determinar si un valor está o no en un árbol binario de búsqueda es $O(\lg n)$.

		Falso, el costo de buscar en un ABB es $O(n)$.

	- El costo de determinar si un valor está o no en un árbol rojinegro es $O(n)$.

		Verdadero, si el costo de buscar un elemento en un ABB es $O(n)$, entonces la el costo de la busqueda en un arbol rojinegro esta acotado por esa complejidad (al ser una especializacion de un ABB).

		Una complejidad más cercana es $O(\lg n)$, gracias la altura (con relación al número de elementos) que garantiza esta estructura de datos.

	- El costo de insertar un elemento en un árbol binario de búsqueda es $O(log n)$.

		Falso, el costo asociado a esta operación en los ABB es $O(n)$.

		> De cierta forma, al insertar, estamos **buscando** donde debe ir el elemento.

3. Si se está buscando el número 370 en un árbol binario de búsqueda que contiene números de 1 a 1000. Indique cuáles dos de las siguientes secuencias no pueden ser una secuencia de nodos examinada en dicha búsqueda. (La secuencia inicia con el elemento raíz hasta llegar al elemento buscado).

	- 2, 252, 401, 398, 330, 344, 397, 370.

	- 924, 220, 911, 244, 898, 258, 362 y 370.

	- 925, 202, 911, 240, 912, 245 y 370.

		Como se enuncia la cadena, el 912 estaría a la derecha del 240, pero debería estar a la derecha del 911.

	- 2, 399, 387, 219, 266, 382, 381, 278 y 370.

	- 935, 278, 347, 621, 299, 392, 358 y 370.

		En la secuencia, al pasar del 347 al 621, implica pasar al subárbol derecho del 347, lo que significa que el resto de elementos debe ser mayo a este, pero el 299 incumple esto, por lo tanto, no es una secuencia válida.

4. Determine si la inserción es conmutativa o no en un árbol rojinegro. Justifique su
respuesta

	Se puede demostrar que es falso con el siguiente contraejemplo:

	- 1 y 4.

	- 4 y 1.

5. Determine si la inserción es conmutativa o no en un b-tree.

6. Redefina el procedimiento [[`tree_successor` | university.5th semester.Análisis y diseño de algoritmos I.Classes.12-Árboles binarios de búsqueda#tree_successorx]] de los árboles binarios de búsqueda sin poder usar el atributo que permite acceder desde un nodo a su nodo padre.

	```
	tree_sucessor(T, x)
		sucessor = T.root

		while sucessor.key != x.key
			if x.key > sucessor.key
				sucessor = sucessor.right
			else if x.key < sucessor.key
				y = sucessor
				sucessor = sucessor.left

			if sucessor.key = x.key
				if sucessor.right != NIL
					return sucessor = tree_minimum(sucessor.right)
				else return y
	```

	Como el algoritmo se aplica sobre sobre un ABB (haciendo un recorrido) su costo es $O(n)$.
