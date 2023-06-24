---
id: a7g0m20nphyy8j7dsccct60
title: 3-Ejercicios - Árboles binarios de búsqueda
desc: ''
updated: 1687303421401
created: 1687223901970
---

1. Argumente que, si un nodo en un árbol binario de búsqueda tiene dos hijos, entonces su sucesor no tiene hijo izquierdo y su predecesor no tiene hijo derecho.

	El sucesor de un nodo es el siguiente nodo (al nodo que le estamos hallando el sucesor) siguiendo un recorrido **in-order**. La única diferencia en la definición con el antecesor es que para este, nos referiremos al nodo anterior del recorrido **in-order**.

  Entonces, partiendo de la suposición de la existencia de un $A$ y $B$ (sucesor y predecesor, respectivamente) de nodos arbitrarios, si $A$ tuviera hijo izquierdo significaría que existe un elemento menor que el, por lo que no podría ser el sucesor, y, por lo tanto, no es compatible con esta primera suposición. Lo mismo sucede en el caso del antecesor, si $B$ tuviera hijo derecho significaría que existe un elemento mayor que el, por lo que no podría ser el antecesor, y en consecuencia no es compatible con esta segunda parte de la suposición. Queda demostrado que ambos casos no son posibles en nuestras suposiciones, por lo que lo enunciado es verdadero.
