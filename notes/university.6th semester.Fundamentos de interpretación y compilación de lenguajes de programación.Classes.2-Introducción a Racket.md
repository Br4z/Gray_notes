---
id: oikr2i51opts4v58p3ds96k
title: 2-Introducción a Racket
desc: ''
updated: 1694135986316
created: 1693684417335
---

Las expresiones en Racket son en notación prefija, por ejemplo `+ 5 2` es equivalente a `5 + 2` en notación infija.

---

Escriba en el Racket utilizando notación prefija:

- $2 * 2 + 3 * 5 + \left (\frac{ 2 }{ 4 } \right )^2$.

	```RKT
	(+ (* 2 2) (* 3 5) (expt (/ 1 4) 2))
	```

- $2 * \left (1 + 3^2 + \frac{ 4 }{ 4 } \right ) + 3 * (5 - 3) + \frac{ 12 }{ 4 } - 3 + 4 * 5^3$.

	```RKT
	(+ (* 2 (+ 1 (expt 3 2) (/ 4 4))) (* 3 (- 5 3)) (/ 12 4) -3 (* 4 (expt 5 3)))
	```

## Condicionales

Diseñe una función que recibe un número y un símbolo que:

1. Si el número es menor o igual que 0 retorna el símbolo `’error`.

2. Si no, Si el número es mayor o igual 0 retorna:

	- `'hombre`: si el símbolo es `'m`.

	- `'mujer`: si el símbolo es `'f`.

	- `'error`: en otro caso retorna.

```RKT
(define verify (
	lambda (number symbol) (
		cond
			[(<= number 0) 'error]
			[(eqv? symbol 'm) 'male]
			[(eqv? symbol 'f) 'female]
			[else 'error]
	)
))
```

## Definiciones locales

En algunos casos requerimos realizar definiciones dentro de funciones, en esos casos usamos sentencia `let`.

- `let`: si las definiciones no son recursivas y tampoco dependientes.

	```RKT
	(define f1 (
		lambda (n) (
			let (
				(p 2)
				(f (lambda (a b) (* a b)))
			)
			(f n p)
		)
	))
	```

	Retorna la multiplicación de `n` y `p`.

- `letrec`: si las definiciones son recursivas y no dependientes.

	```RKT
	(define f2 (
			lambda (n) (
				letrec (
					(p 2)
					(sum (
						lambda (a b) (
							if (= b 0) 0 (+ a (sum a (- b 1))))
					))
				)
				(sum n p)
			)
	))
	```

	Retorna la multiplicación de `n` y `p`.

- `let*`: si las definiciones son dependientes, pero no recursivas.

	```RKT
	(define f3 (
		lambda (n) (
			let* (
				(p 2)
				(q 3)
				(r (+ p q n))
			)
			r
		)
	))
	```

### Listas

Las listas son una estructura recursiva, la cual consta de dos partes:

1. Un valor (cualquiera representado por scheme).

2. Una lista (la cual puede ser vacía).

```RKT
(cons 1 (cons 2 (cons 3 empty)))
```

Racket, provee la función `list`, la cual permite construir listas sin pensar en la recursividad.

```RKT
(list 1 2 3)
```

> También podemos declarar listas con la siguiente notación `'( <elements> )`.

---

Para acceder a los elementos se tiene. `car` accede al primer elemento y `cdr` al resto (que es una lista).

---

Diseñe una función que almacene los factoriales (en una lista) desde $0$ hasta un valor $n$ ingresado por el usuario.

```RKT
(define factorial-list (
	lambda (n) (
		letrec (
				(makeList (
					lambda (counter factorial) (
						if (= (+ counter 1) n)
							(list (* factorial counter))
							(cons (* factorial counter) (makeList (+ counter 1) (* factorial counter)))
					)
				))
		)
		(cons 1 (makeList 1 1))
	)
))
```

---

En Racket las funciones son **ciudadanos de primera clase**, lo que quiere decir que no hay distinción, las funciones son simples valores, por ejemplo:

```RKT
(define greater? (
	lambda (a b) (
		cond
			[(> a b) #T]
			[else #F]
	)
))

(define my-filter (
	lambda (list p n) (
		cond
			[(eqv? list '()) empty]
			[(p (car list) n) (cons (car list) (my-filter (cdr list) p n))]
			[else (my-filter (cdr list) p n)]
	)
))
```

---

1. Diseñe una función, que reciba un número "a" y una función "f". La función "f" recibe un número y retorna un booleano. Se hace el llamado `(f a)` y si el resultado es verdadero se retorna `'ok`, en otro caso `'false`.

	```RKT
	(define my-function (
		lambda (f a) (
			cond
				[(f a) 'ok]
				[else 'false]
		)
	))
	```

2. Diseñe una función que reciba dos números "a" y "b" y retorna una función "t" la cual espera un argumento numérico "s". "t" evalúa si "a" es mayor que "b" si es así retorna $2s$ en otro caso $-2s$.

	```RKT
	(define my-function (
		lambda (a b) (
			lambda (s) (
				cond
					[(> a b) (* 2 s)]
					[else (* -2 s)]
				)
			)
	))
	```

## Asignación y secuenciación

Podemos incluir la noción de **estado** con la instrucción `set!`, lo que significaría desplazarnos al paradigma imperativo.

```RKT
(define value 1)
(set! value 2)
```

Otra característica de un paradigma imperativo es la secuenciación, es decir, la ejecución de más de una instrucción en un paso dado, ya que el declarativo solo permite uno.

```RKT
(define my-function (
	lambda (a b) (
		begin
			(set! a (* a b))
			(set! b (- a b))
			(+ a b)
	)
))
```

> Si no lo especificamos, el compilador infiere que las expresiones se ejecutarán secuencialmente de todas formas.

## Ejercicios

1. Diseñe una función que reciba una lista "list", una posición "n", un elemento "x" y retorne una lista con el elemento "x" en la posición "n" de la lista "list".

	```RKT
	(define replace (
		lambda (list n x) (
			if (= n 0)
				(cons x (cdr list))
				(cons (car list) (replace (cdr list) (- n 1) x))
		)
	))
	```

2. Diseñe una función que reciba una lista "list", una elemento "x", un elemento "y" y retorne la lista "list", con todas las ocurrencias de "x" remplazadas con "y".

	```RKT
	(define replace (
		lambda (list x y) (
			cond
				[(eqv? list empty) list]
				[(eqv? (car list) x) (cons y (replace (cdr list) x y))]
				[else (cons (car list) (replace (cdr list) x y))]
		)
	))
	```

3. Diseñe una función que reciba una lista "list1", una list "list1", un elemento "y" y retorne el producto cartesiano entre las dos listas.

```RKT
(define cartesian-product (
	lambda (list1 list2) (
		letrec (
				(combine-with-all (
					lambda (element list) (
						if (null? list)
							empty
							(cons (cons element (cons (car list) empty)) (combine-with-all element (cdr list)))
					)
				))
			)
			(if (null? list1)
				empty
				(append (combine-with-all (car list1) list2) (cartesian-product (cdr list1) list2)))
	)
))
```
