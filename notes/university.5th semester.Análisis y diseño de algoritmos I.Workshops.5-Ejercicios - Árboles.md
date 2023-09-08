---
id: scpsmktilawrax7yv3xmbxh
title: 5-Ejercicios - Árboles
desc: ''
updated: 1688504862656
created: 1688495186919
---

- Árboles binarios de búsqueda

	1. Determine si la operación de inserción es conmutativa o no.

		No, lo podemos refutar con un contraejemplo:

		Partiendo de un árbol vacío se insertan los elementos

		- 2 y 1.

		- 1 y 2.

	2. Determine si la [[operación de eliminación | university.5th semester.Análisis y diseño de algoritmos I.Classes.12-Árboles binarios de búsqueda#tree_deleteT-z]] es conmutativa.

		No, lo podemos refutar con un contraejemplo:

		Partiendo del siguiente árbol:

		8 left: (14 left:9) right : 7

		- 7 y 8.

		- 8 y 7.

- Árboles rojinegros.

	1. ¿Cuál es el número mínimo y máximo de nodos internos de un árbol rojinegro con bh igual a $k$?

		> Un nodo interno es aquel nodo que no es hoja ni raíz.

		- Mínimo: todos los nodos son de color negro y  su número está dado por la expresión $2^{k - 1} - 1$.

		- Maximo: los nodos están intercalados y  su número está dado por la expresion $2^{2k - 1} - 1$.

			> Por cada nivel negro hay uno rojo (que no cuenta para el **bh**).

	2. ¿Considere un árbol rojinegro con $n$ nodos, cuál es el radio mínimo y máximo ente nodos internos rojos y nodos internos negros?

		> El radio hace referencia a la diferencia entre los dos.

		- Mínimo = el árbol no tiene nodos rojos, por lo que su proporción o radio es $1 : 0$ (por cada nodo negro no hay ninguno rojo).

		- Máximo = el árbol es intercalado, por lo que su proporción o radio es $1 : 2$ (por cada nodo negro hay dos nodos rojos) sin considerar la raíz.

			> Un arbol rojinegro intercalado puede terminar en un nivel rojo.

	3. Muestre el árbol rojinegro resultante después de insertar sucesivamente los siguientes elementos partiendo de un árbol vacío: 41, 38, 31, 12, 19, 8.

		Usando el procedimiento [[`RB_insert` | university.5th semester.Análisis y diseño de algoritmos I.Classes.11-Árboles rojinegros#rb_insertT-x]]

		- 41.

		- 38.

		- 31.

		- 12.

		- 19.

		- 8.

- Órdenes estadísticos dinámicos

	1. Considere un árbol para ordenes estadísticos dinámicos, escriba un procedimiento que a partir del árbol y una llave retorne su orden estadístico en el árbol. (Asuma que todas las llaves son diferentes).

	2. Dado un árbol (para órdenes estadísticos dinámicos), un elemento $x$ y un entero $i$, diseñe un algoritmo que determine el i-ésimo sucesor de $x$ en el árbol. ¿Cuál sería su complejidad?