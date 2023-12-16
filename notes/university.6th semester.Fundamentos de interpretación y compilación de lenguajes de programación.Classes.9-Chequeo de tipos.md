---
id: g6uuuvc1jixwe69seobhenf
title: 9-Chequeo de tipos
desc: ''
updated: 1698872928260
created: 1698370233292
---

Para el nuevo interpretador que vamos a crear, partiremos del creado para el paradigma funcional, pero con una primitiva nueva:

```RKT
(define grammar '(
	...
	(primitive ("zero?") zero-test-prim)
	...
))

(define apply-primitive (
	lambda (prim args) (
		cases primitive prim
			...
			(zero-test-prim () (zero? (car args)))
	)
))
```

---

Los tipos definen las estructuras de almacenamiento disponibles para representar información; además, el tipo determina cómo interpreta el compilador el contenido de la memoria. Un error de tipo se produce cuando se aplica una operacion a un dato con caracteristicas diferentes a las esperadas.

El análisis de tipos es un paso del procesamiento de un lenguaje de programación. Se realiza para evitar que se presenten errores de tipos en tiempo de ejecución.

Para realizar el análisis de tipos se tienen en cuenta los siguientes aspectos:

1. Se define un conjunto de tipos para el lenguaje y lo que significa "un valor expresado $v$ es de tipo $t$".

2. El analizador asigna un tipo para cada expresión en el programa.

	> Si a una expresión $e$ se asigna un tipo $t$, entonces siempre que $e$ es interpretada, su valor sera de tipo $t$.

3. El analizador debe inspeccionar también cada invocación de una operación en el programa, con el fin de verificar que los operandos sean del tipo adecuado.

4. Si se detectan errores de tipo, el analizador puede tomar algunas acciones, las cuales son, normalmente, parte del diseño del lenguaje:

	- Rehusarse a ejecutar el programa.

	- Aplicar medidas correctivas.

---

Los tipos para el lenguaje que se está implementando tienen una la siguiente estructura:

```
<type-expression> := int
                  := bool
                  := ({ <type-expression> }* -> <type-expression>)
```

---

El lenguaje que se está diseñando, será **fuerte** y **estáticamente** tipado, lo que significa que ningún programa que pasa el chequeo de tipos tendrá un error de tipos. Un error de tipo será un intento de:

- aplicar un entero o un booleano a un argumento.

- aplicar un procedimiento o primitiva a un número errado de argumentos.

- un intento de aplicar una primitiva que espera un entero a un no-entero.

- usar un no-booleano como la prueba de una expresión condicional.

> Los errores como una división por cero, no serán considerados como errores de tipo.

---

En un lenguaje con chequeo de tipos, se requiere que el programador incluya los tipos de todas las variables ligadas. Para hacer chequeo de tipos en el lenguaje del curso, se necesita cambiar la forma en que se escriben procedimientos (proc-exp) y recursion (letrec-exp).

```
<expression> := proc ({ <type-expression> <identifier> }*) <expression>
             := letrec { <type-expression> <identifier> ({ <type-expression> <identifier> }*) = <expression> }* in <expression>
```

Como cambiamos nuestra gramática, debemos extender las reglas de producción agregando las de type-expression.

```RKT
(define grammar '(
	...
	(type-expression ("int") int-type-exp)
	(type-expression ("bool") bool-type-exp)
	(type-expression ("(" (separated-list type-expression ",") "->" type-expression ")") proc-type-exp)
	...
	(expression ("letrec"
		(arbno type-expression identifier "(" (separated-list type-expression identifier ",") ")" "=" expression) "in" expression)
		letrec-exp)
	(expression ("proc" "(" (separated-list type-expression identifier ",") ")" expression) proc-exp)
	...
))
```

---

Al cambiar la gramática, también debemos cambiar `eval-expression` (específicamente el número de argumentos que reciben estos casos).

```RKT
(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(proc-exp (type-expressions identifiers body)
				...
			)
			(letrec-exp (result-texps proc-names texpss idss bodies letrec-body)
				...
			)
	)
))
```

---

Ahora se definirán los valores (tipos) que pueden denotar las expresiones de tipo.

```RKT
(define-datatype type type?
	(atomic-type (name symbol?))
	(procedure-type (parameters-types (list-of type?)) (result-type type?))
)

(define int-type (atomic-type 'int))

(define bool-type (atomic-type 'bool))
```

También se debe definir el procedimiento `expand-type-expression` que calcula el tipo denotado por una expresión de tipo (type-expression).

```RKT
(define expand-type-expression (
	lambda (type-exp) (
		cases type-expression type-exp
			(int-type-exp () int-type)
			(bool-type-exp () bool-type)
			(proc-type-exp (parameters-types result-type)
				(procedure-type (expand-type-expressions parameters-types) (expand-type-expression result-type))
			)
	)
))

(define expand-type-expressions (
	lambda (type-expressions) (map expand-type-expression type-expressions)
))
```

---

Crearemos ambientes de tipos para guardar toda la información relacionada con los tipos de nuestro programa.

```RKT
(define-datatype type-environment type-environment?
	(empty-type-environment)
	(extended-type-environment
		(symbols (list-of symbol?))
		(types (list-of type?))
		(env type-environment?))
)

(define apply-type-env (
	lambda (type-env var) (
		cases type-environment type-env
			(empty-type-environment () (eopl:error 'apply-type-env "No binding for ~s" var))
			(extended-type-environment (symbols types old-env) (
					let (
						(index (index-of var symbols))
					)
					(if index
						(nth-element types index)
						(apply-type-env old-env var)
					)
				)
			)
	)
))
```

---

El revisor (checker) se implementará como un procedimiento que recibe una expresión y un ambiente de tipos y retorna el tipo correspondiente a ella o un error.

```RKT
(define type-of-expression (
	lambda (exp type-env) (
		cases expression exp
			(lit-exp (number) int-type)
			(true-exp () bool-type)
			(false-exp () bool-type)
			(var-exp (identifier) (apply-type-env type-env identifier))
			(if-exp (test-exp true-exp false-exp) (
				let (
					(test-type (type-of-expression test-exp type-env))
					(false-type (type-of-expression false-exp type-env))
					(true-type (type-of-expression true-exp type-env))
				)
				(check-equal-type! test-type bool-type test-exp)
				(check-equal-type! true-type false-type exp)
				true-type
			))
			...
	)
))
```

Se utiliza el procedimiento `check-equal-type!` para verificar que en los dos casos (verdadero y falso) el condicional retorne datos del mismo tipo.

```RKT
(define check-equal-type! (
	lambda (t1 t2 exp) (
		if (not (equal? t1 t2))
			(eopl:error 'check-equal-type!
				"Types didn't match: ~s != ~s in~%~s" (type-to-external-form t1) (type-to-external-form t2)
				exp)
			#t
	)
))
```

Este procedimiento a su vez utiliza el procedimiento `type-to-external-form`.

```RKT
(define type-to-external-form (
	lambda (t) (
		cases type t
			(atomic-type (name) name)
			(procedure-type (parameters-types result-type)
					(append
						(parameters-types-to-external-form parameters-types)
						'(->)
						(list (type-to-external-form result-type))
					)
			)
	)
))
```

Que a su vez utiliza el procedimiento `parameters-types-to-external-form` para mostrar un error más legible.

```RKT
(define parameters-types-to-external-form (
	lambda (types) (
		if (null? types)
			'()
			(if (null? (cdr types))
				(list (type-to-external-form (car types)))
				(cons (type-to-external-form (car types))
					(cons ', (parameters-types-to-external-form (cdr types))))
			)
	)
))
```

---

Para el caso de los procedimientos en `type-of-expression`, implementaremos el procedimiento `type-of-proc-exp`.

```RKT
(define type-of-proc-exp (
	lambda (types-expressions identifiers body tenv) (
		let* (
			(parameters-types (expand-type-expressions types-expressions))
			(result-type
				(type-of-expression body (extended-type-environment identifiers parameters-types tenv))
			)
		)
		(procedure-type parameters-types result-type)
	)
))
```

---

Vamos a implementar procedimiento `type-of-application` que primero revisa si el tipo del operador es un tipo procedimiento. Luego revisa si el número de argumentos esperados por el procedimiento es igual al número dado y después, en el ciclo `for-each`, revisa si el tipo de cada argumento esperado es igual al tipo del operando correspondiente. Si la revisión tiene éxito, entonces el tipo de la aplicación es el tipo resultado del procedimiento.

```RKT
(define type-of-application (
	lambda (rator-type rands-types rator rands exp) (
		cases type rator-type
			(procedure-type (parameters-types result-type)
				(if (= (my-length parameters-types) (my-length rands-types))
					(begin
						(for-each check-equal-type!
							rands-types parameters-types rands)
						result-type
					)
					(eopl:error 'type-of-expression
						(string-append
						"Wrong number of arguments in expression ~s:"
						"~%expected ~s~%received ~s")
						exp
						(map type-to-external-form parameters-types)
						(map type-to-external-form rands-types)
					)
			))
			(else (
				eopl:error 'type-of-expression
						"Rator not a proc type:~%~s~%had rator type ~s"
						rator (type-to-external-form rator-type)
			))
	)
))
```

---

Para determinar el tipo del operador cuando se trata de aplicación de primitivas implementamos el procedimiento `type-of-primitive`.

```RKT
(define type-of-primitive (
	lambda (prim) (
	cases primitive prim
		(add-prim () (procedure-type (list int-type int-type) int-type))
		(substract-prim () (procedure-type (list int-type int-type) int-type))
		(mult-prim () (procedure-type (list int-type int-type) int-type))
		(incr-prim () (procedure-type (list int-type) int-type))
		(decr-prim () (procedure-type (list int-type) int-type))
		(zero-test-prim () (procedure-type (list int-type) bool-type))
	)
))
```

Ahora, se añaden las cláusulas correspondientes al procedimiento `type-of-expression`.

```RKT
(define type-of-expression (
	lambda (exp type-env) (
		cases expression exp
			...
			(primapp-exp (prim rands)
				(type-of-application
					(type-of-primitive prim)
					(types-of-expressions rands type-env)
					prim rands exp
				)
			)
			(app-exp (rator rands)
				(type-of-application
						(type-of-expression rator type-env)
						(types-of-expressions rands type-env)
						rator rands exp
				)
			)
			...
	)
))
```

El procedimiento `types-of-expressions` es definido de la siguiente forma:

```RKT
(define types-of-expressions (
	lambda (rands tenv) (map (lambda (exp) (type-of-expression exp tenv)) rands)
))
```

---

Se añade la cláusula respectiva a la definición del procedimiento `type-of-expression` para hallar el tipo de una let-exp.

```RKT
(define type-of-expression (
	lambda (exp type-env) (
		cases expression exp
			...
			(let-exp (identifiers rands body) (type-of-let-exp identifiers rands body type-env))
			...
	)
))
```

La implementación del procedimiento `type-of-let-exp` es la siguiente:

```RKT
(define type-of-let-exp (
	lambda (identifiers rands body tenv) (
		let (
			(tenv-for-body (
				extended-type-environment
					identifiers
					(types-of-expressions rands tenv)
					tenv
			))
		)
		(type-of-expression body tenv-for-body)
	)
))
```

---

Finalmente, para hallar el tipo de una letrec-exp, implementamos el procedimiento `type-of-letrec-exp`.

```RKT
(define type-of-letrec-exp (
	lambda (result-texps proc-names texpss identifiers bodies letrec-body tenv) (
		let* (
			(parameters-types (
					map (lambda (texps) (expand-type-expressions texps)) texpss
				)
			)
			(results-types (expand-type-expressions result-texps))
			(proc-types (map procedure-type parameters-types results-types))
			(tenv-for-body (extended-type-environment proc-names proc-types tenv))
		)
		(for-each (lambda (identifiers parameters-types body result-type) (
				check-equal-type!
					(type-of-expression
						body
						(extended-type-environment identifiers parameters-types tenv-for-body)
					)
					result-type
					body
			))
			identifiers parameters-types bodies results-types
		)
		(type-of-expression letrec-body tenv-for-body)
	)
))
```

Añadimos la respectiva cláusula a `type-of-expression`.

```RKT
(define type-of-expression (
	lambda (exp type-env) (
		cases expression exp
			...
			(letrec-exp (result-texps proc-names texpss idss bodies letrec-body)
				(type-of-letrec-exp result-texps proc-names texpss idss bodies letrec-body type-env)
			)
	)
))
```

---

Una vez hemos implementado nuestro checker, es hora de cambiar nuestro procedimiento `eval-program`. Ahora antes de ejecutar el programa se hará toda la comprobación de tipos, si esta pasa entonces se ejecutará el programa, de otra forma retornará un mensaje de error.

```RKT
(define eval-program (
	lambda (pgm) (
		cases program pgm
			(a-program (body) (
				let (
					(program-type (type-of-expression body (empty-type-environment)))
				)
				(if (type? program-type)
						(eval-expression body (init-env))
						'error
				)
			))
	)
))
```
