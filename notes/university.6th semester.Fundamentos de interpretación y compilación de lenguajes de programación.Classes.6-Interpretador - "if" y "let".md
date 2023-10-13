---
id: 6k0w3x9kdlrvc4vr96tetur
title: 6-Interpretador - "if" y "let"
desc: ''
updated: 1696616785299
created: 1696098408076
---

Nuestro nuevo lenguaje consistirá de las expresiones especificadas anteriormente y de expresiones para condicionales `if ...  then ... else ...` y para el operador de ligadura local `let`. Para este lenguaje se extiende el conjunto de valores expresados y denotados de la siguiente manera:

$$
\text{ valor expresado } = \text{ número } + \text{ booleano } \\[5 pt]

\text{ valor denotado } = \text{ número } + \text{ booleano }
$$

La gramática será:

```
<program> := <expression>

<expression> := <number>
             := <identifier>
             := <primitive> ( { <expression> }* )
             := if <expression> then <expression> else <expression>
             := let { <identifier> = <expression> }* in <expression>

<primitive>  := + | - | add1 | sub1
```

La especificación léxica será la [[misma | university.6th semester.Fundamentos de interpretación y compilación de lenguajes de programación.Classes.5-Primer interpretador simple#un-interpretador-simple]] del lenguaje anterior.

La especificación de la gramática es la siguiente:

- SLLGEN.

	```RKT
	(define grammar '(
			(program (expression) a-program)
			(expression (number) lit-exp)
			(expression (identifier) var-exp)
			(expression (primitive "(" (separated-list expression ",") ")" ) primapp-exp)
			(expression ("if" expression "then" expression "else" expression) if-exp)
			(expression ("let" (arbno identifier "=" expression) "in" expression) let-exp)
			(primitive ("+") add-prim)
			(primitive ("-") substract-prim)
			(primitive ("*") mult-prim)
			(primitive ("add1") incr-prim)
			(primitive ("sub1") decr-prim)
	))
	```

- `define-datatype`.

	```RKT
	(define-datatype program program?
		(a-program (exp expression?))
	)

	(define-datatype expression expression?
		(lit-exp (value number?))
		(var-exp (identifier symbol?))
		(primeapp-exp (rator primitive?) (rands (list-of expression?)))
		(if-exp
			(test-exp expression?)
			(true-exp expression?)
			(false-exp expression?)
		)
		(let-exp
			(identifiers (list-of symbol?))
			(expressions (list-of expression?))
			(body expression?)
		)
	)

	(define-datatype primitive primitive?
		(add-prim)
		(substract-prim)
		(mult-prim)
		(incr-prim)
		(decr-prim)
	)
	```

## Semantica de los condicionales

Para determinar el valor de una expresión condicional ($\text{ if-exp } \text{ exp }_1 \text{ exp }_2 \text{ exp }_3$) es necesario determinar el valor de la subexpresión $\text{ exp }_1$. Si $\text{ exp }_1$ corresponde al valor booleano $true$, el valor de toda la expresión if-exp debe ser el valor de la subexpresión $\text{ exp }_2$. En caso contrario deberia ser $\text{ exp }_3$.

Para no tener que definir un nuevo tipo de dato que maneje booleanos, falso se representará con cero y cualquier otro valor representará verdadero.

> Como en el lenguaje de programacion C.

```RKT
(define true? (
	lambda (value) (
		not (zero? value)
	)
))
```

## Semántica de la ligadura local

La expresión `let` permite la creación de ligaduras locales a variables nuevas. Tı́picamente, la expresión `let` crea un nuevo ambiente que extiende el ambiente principal (sobre el que se evalúa el `let`) con las variables y valores especificados en el contenido de la expresión.

---

Finalmente, el procedimiento `eval-expression` se define ası́:

```RKT
(define true? (
	lambda (value) (
		not (zero? value)
	)
))

(define eval-program (
	lambda (pgm) (
		cases program pgm
			(a-program (body) (eval-expression body (init-env)))
	)
))

(define eval-expressions (
	lambda (expressions env) (
		map (lambda (expression) (eval-expression expression env)) expressions
	)
))

(define eval-expression (
	lambda (exp env) (
		cases expression exp
			(lit-exp (value) value)
			(var-exp (identifier) (apply-env env identifier))
			(primapp-exp (prim rands) (
					let (
						(args (eval-expressions rands env))
					)
					(apply-primitive prim args)
				)
			)
			(if-exp (test-exp true-exp false-exp)
				(if (true? (eval-expression test-exp env))
					(eval-expression true-exp env)
					(eval-expression false-exp env)
				)
			)
			(let-exp (identifiers expressions body) (
				let (
					(args (eval-expressions expressions env))
				)
				(eval-expression body (extended-environment identifiers args env))
			))
		)
))

(define apply-primitive (
	lambda (prim args) (
		cases primitive prim
		(add-prim () (+ (car args) (cadr args)))
		(substract-prim () (- (car args) (cadr args)))
		(mult-prim () (* (car args) (cadr args)))
		(incr-prim () (+ (car args) 1))
		(decr-prim () (- (car args) 1))
	)
))
```
