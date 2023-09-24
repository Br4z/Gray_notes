---
id: x1k2vkm2tom1nbq6y0ccady
title: >-
  3-Relación entre inducción y programación - Especificación recursiva de datos
  y programas
desc: ''
updated: 1694904137444
created: 1693849906052
---

## Especificación recursiva de datos

### Técnicas

#### Especificación inductiva

Se define un conjunto $S$, el cual es el conjunto más pequeño que satisface las siguientes dos propiedades:

1. Algunos valores específicos que deben estar en $S$.

2. Si algunos valores están en $S$, entonces otros valores también
están en $S$.

Dentro de este tipo podemos clasificar las definiciones en:

- Top-Down definition.

	Por ejemplo, la definición de los números múltiplos de 3:

	$$
	n \in S \Leftrightarrow (n = 0 \; \lor \; n -3 \in S)
	$$

	Podemos utilizar esta definición para escribir un procedimiento (predicado) que decida si un número natural $n$ está en $S$:

	```RKT
	(define in-s? (
		lambda (n) (
			if (zero? n)
				#t
				(if (< n 0)
					#f
					(in-s? (- n 3))
				)
		)
	))
	```

- Bottom-up definition.

	Por ejemplo, la definición de los números múltiplos de 3:

	$$
	0 \in S \land (\text{Si } n \in S \Rightarrow n + 3 \in S)
	$$

---

Existen las "rules of inference definition", que no son más que otra forma de expresar especificaciones, y se tienen las siguientes características:

- Cada entrada es una regla.

- Una línea horizontal se lee como "si - entonces"; la parte superior es la hipótesis (o antecedente); la parte inferior es la conclusión (o consecuente).

Por ejemplo, la definición de los números múltiplos de 3:

$$
\frac{ }{ 0 \in S } \\[10 pt]

\frac{ n \in S } { n + 3 \in S}
$$

---

Otros ejemplos de especificación inductiva son:

- Números pares positivos.

	1. Si $n = 2$ entonces $n$ es par.

	2. Si $n$ es par, entonces $n + 2$ también es par.

	$$
	n \in S \Leftrightarrow (n = 2 \; \lor \; n + 2 \in S)
	$$

- Lista de números.

	1. $empty$ es una lista de números.

	2. Si $n$ es un número y $l$ es una lista, entonces $cons(n , l)$ es una lista de números.

- Lista de números pares.

	$$
	\frac{ }{ empty \in S } \\[10 pt]

	\frac{ l \in s , \; n \in \mathbb{ N } }{ cons(2n , l) \in S}
	$$

- Múltiplos de 5.

	$$
	\frac{ }{ 5 \in S } \\[10 pt]

	\frac{ n \in S }{ n + 5 \in S}
	$$

#### Especificacion mediante gramaticas

Las gramáticas se componen de:

- Símbolos no terminales: son aquellos que se componen de otros símbolos, son conocidos como categorías sintácticas.

- Símbolos terminales: corresponden a elementos del alfabeto.

- Reglas de producción.

---

Ejemplos de especificación mediante gramáticas son:

- Lista de números enteros.

	```
	<int_list> ::= ()
	           :: = (<int> <int_list>)

	<int_list> ::= () | (<int> <int_list>)

	<int_list> ::= ({<int>}*)
	```

- Listas de símbolos y listas.

	```
	<s_list> ::= ({s_exp}*)
	<s_exp>  ::= <symbol> | <s_list>
	```

- Árbol binario.

	```
	<binary_tree> ::= <int>
	              ::= (<symbol> <binary_tree> <binary_tree>)
	```

- Expresión cálculo $\lambda$.

	```
	<lambda_exp> ::= <identifier>
	             ::= (lambda (<identifier>) <lambda_exp>)
	             ::= (<lambda_exp> <lambda_exp>)
	```

- Listas en Scheme.

	```
	<list> ::= ()
	       ::= (<Scheme-value> <list>)
	```

---

La definición inductiva o mediante gramáticas de los conjuntos de datos sirve de guía para desarrollar procedimientos que operan sobre dichos datos.

---

1. Función que recibe una lista "list" y retorna la longitud de "list".

	```RKT
	(define list-lenght (
		lambda (list) (
			if (empty? list)
				0
				(+ 1 (list-lenght (cdr list)))
		)
	))
	```

2. Función que recibe una lista "list" y un número "n" y retorna el elemento en la posición "n" de la lista "list".

	```RKT
	(define nth-element (
		lambda (list n) (
			cond
				[(null? list) (report-error n)]
				[(zero? n) (car list)]
				[else (nth-element (cdr list) (- n 1))]
		)
	))

	(define report-error (
		lambda (n) (
			format "List too short by ~s elements" (+ n 1)
		)
	))
	```

3. Función que recibe un árbol binario "tree" y retorna la suma de los elementos de "tree".

	```RKT
	(define sum-tree (
		lambda (tree) (
			if (number? tree)
				tree
				(+
					(sum-tree (cadr tree))
					(sum-tree (caddr tree))
				)
		)
	))
	```

4. Función que recibe un árbol binario "tree" y retorna la cantidad de números enteros (hojas) en "tree".

	```RKT
	(define leaves (
		lambda (tree) (
			if (number? tree)
				1
				(+
					(leaves (cadr tree))
					(leaves (caddr tree))
				)
		)
	))
	```

5. Función que recibe un árbol binario "tree" y retorna la cantidad de símbolos (nodos) en "tree".

	```RKT
	(define interior-nodes (
		lambda (tree) (
			if (number? tree)
				0
				(+
					1
					(interior-nodes (cadr tree))
					(interior-nodes (caddr tree))
				)
		)
	))
	```

6. Función que recibe un árbol binario "tree" y retorna la lista con los símbolos (nodos) de "tree".

	```RKT
	(define list-interior-nodes (
		lambda (tree) (
			if (number? tree)
				empty
				(cons (car tree)
					(cons (list-interior-nodes (cadr tree)) (list-interior-nodes (caddr tree)))
				)
		)
	))
	```

	Debido a que usamos `cons` la lista que retorna tendrá algunas listas vacías que indican que el símbolo (nodo) no tiene más símbolos (nodos) hijos, para solucionar este detalle podemos usar `concat` de la siguiente forma:

	```RKT
	(define concat (
		lambda (list1 list2) (
			if (empty? list1)
				list2
				(cons (car list1) (concat (cdr list1) list2))
		)
	))

	(define list-interior-nodes (
		lambda (tree) (
			if (number? tree)
				empty
				(concat (cons (car tree) empty)
					(concat (list-interior-nodes (cadr tree)) (list-interior-nodes (caddr tree)))
				)
		)
	))
	```

7. Función que recibe un árbol binario "tree" y retorna la lista con los números (hojas) de "tree".

	```RKT
	(define list-leaves (
		lambda (tree) (
			if (number? tree)
				(cons tree empty)
				(concat (list-leaves (cadr tree))
					(list-leaves (caddr tree))
				)
		)
	))
	```

8. Función que recibe un árbol binario "tree" y un predicado "p" y retorna la lista con los números (hojas) de "tree" que satisfaga el predicado "p".

	```RKT
	(define filter-leaves (
		lambda (tree p) (
			if (number? tree)
				(if (p tree) (list tree) empty)
				(concat (filter-leaves (cadr tree) p)
					(filter-leaves (caddr tree) p)
				)
		)
	))
	```

9. Función que recibe una lista "list" y retorna la suma de los elementos de "list".

	```RKT
	(define sum (
		lambda (list) (
			if (empty? list)
				0
				(+ (car list) (sum (cdr list)))
		)
	))
	```

## Alcance y ligadura de una variable

- Una variable está ligada al lugar donde se declara.

- Dependiendo del momento de aplicación de las reglas (antes o durante la ejecución), los lenguajes se denominan de alcance estático o alcance dinámico.

- Una variable "x" ocurre libre en una expresión "E" si y solo si existe algún uso de "x" en E el cual no está ligado a ninguna declaración de "x" en "E".

---

La gramática de una expresión $lambda$ es:

```
<lambda-exp> ::= <identifier>
             ::= (lambda (<identifier>) <lambda-exp>)
             ::= (<lambda-exp> <lambda-exp>)
```

Así mismo podemos definir el siguiente procedimiento para determinar si una variable ocurre libre:

```RKT
(define occurs-free? (
	lambda (var exp) (
		cond
			[(symbol? exp) (eqv? var exp)]
			[(eqv? (car exp) 'lambda)
				(and (not (eqv? (caadr exp) var))
					(occurs-free? var (caddr exp)))]
			[else (or (occurs-free? var (car exp))
				(occurs-free? var (cadr exp)))]
		)
))
```

---

¿Cuál es el valor de la siguiente expresión?

```RKT
(let ((x 6)(y 7))
	(*
		(let ((y 8))
			(+
				(let ((x 6) (y x))
					(+
						x
						(let ((y 3) (x y)) (+ x (+ 2 y))) ; 11
					)
				) ; 17
				y ; 17 + 8 = 25
			)
		)
		(let ((x 4)) (- y x)) ; 3
	) ; 25 * 3 = 75
)
```
