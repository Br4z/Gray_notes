---
id: rzsp41ci9mvldwguws0651l
title: 7-Interpretador - proc y letrec
desc: ''
updated: 1696616777055
created: 1696459593901
---

El lenguaje consistirá de las expresiones especificadas anteriormente y de expresiones para creación de procedimientos `proc( ... ) ...` y de aplicación de procedimientos `(... ...)`.

$$
\text{ valor expresado } = \text{ número } + \text{ booleano } + \text{ procedimiento } \\[5 pt]

\text{ valor denotado } = \text{ número } + \text{ booleano } + \text{ procedimiento }
$$

La gramática será:

```
<program> := <expression>

<expression> := <number>
             := <identifier>
             := <primitive> ( { <expression> }* )
             := if <expression> then <expression> else <expression>
             := let { <identifier> = <expression> }* in <expression>
             := proc ( { <identifier> }* ) <expression>
             := ( <expression> { <expression> }*)

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
			(expression ("proc" "(" (separated-list identifier ",") ")" expression) proc-exp)
			(expression ("(" expression (arbno expression) ")") app-exp)
			(primitive ("+") add-prim)
			(primitive ("-") substract-prim)
			(primitive ("*") mult-prim)
			(primitive ("add1") incr-prim)
			(primitive ("sub1") decr-prim)
	))
	```

## Semántica de los procedimientos

El valor de las expresiones que contemplan procedimientos depende en gran medida del ambiente en el cual son evaluadas. Por esta razón, un procedimiento debe empaquetar los parámetros de la función, la expresión correspondiente al cuerpo de la función y el ambiente en el que es creado el procedimiento. Este paquete es denominado **clausura**.

La interfaz del tipo de dato `closure` consiste de un procedimiento constructor y del procedimiento observador `apply-procedure` que determina como aplicar un valor de tipo procedimiento.

```RKT
(define-datatype procedure procedure? (
	(closure
		(identifiers (list-of symbol?))
		(body expression?)
		(env environment?)
	)
))

(define apply-procedure (
	lambda (proc arguments) (
		cases procedure proc
			(closure (identifiers body env)
				eval-expression body (extended-environment identifiers arguments env))
	)
))
```

También debemos agregar los casos de las dos nuevas expresiones (`proc-exp` y `apply-exp`) a `eval-expression`.

```RKT
(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(proc-exp (identifiers body) (closure identifiers body env))
			(app-exp (rator rands) (
				let (
					(proc (eval-expression rator env))
					(args (eval-expressions rands env))
				)
				(if (procedure? proc)
					(apply-procedure proc args)
					(eopl:error "exp ~s is not a procedure" proc)
				)
			))
		)
))
```

---

Un ejemplo de la evaluación de un procedimiento podría ser el siguiente:

```RKT
(eval-program (scan&parse "
let
	g = proc(x) +(y, (f x)) // +(2, (f x))
	m = 6
in
	let
		g = proc(x,y) *(x, (g y)) // proc(x,y) *(x, (proc(x) +(2, (f x)))(y))
		h = proc() (g m) // proc() +(2, (f 6)) = 32
		q = 7
	in
		-((h), q) // 32 - 7 = 25
"))
```

---

Hasta este punto, los procedimientos que pueden ser definidos en nuestro lenguaje **solo** pueden tener invocaciones a otros procedimientos definidos en ambientes superiores a su propio ambiente, es decir, no pueden ser recursivos (invocarse a sí mismos en su definición). Esta limitación surge de la forma en la que guardamos los ambientes, pues, en el ambiente en el que se "ejecuta" el procedimiento no lo contiene.

Para añadir recursión a nuestro lenguaje, este será extendido con algunas características. El lenguaje consistirá de las expresiones especificadas anteriormente y de un nuevo tipo de expresión `letrec`. Esta expresión permitirá la creación de procedimientos recursivos.

> El tipo de dato ambiente será extendido para contemplar ambientes que faciliten la creación de procedimientos recursivos.

```
...
<expression> := ...
             := letrec { <identifier> ({ <identifier> }*) = <expression> }* in <expression>
...
```

---

La especificación que agregaríamos a la gramática es la siguiente:

- SLLGEN.

	```RKT
	(define grammar '(
			...
		(expression ("letrec"
			(arbno identifier "(" (separated-list identifier ",") ")" "=" expression) "in" expression)
			letrec-exp)
			...
	))
	```

Agregaríamos un nuevo tipo de ambiente (modificando su `datatype`).

```RKT
(define-datatype environment environment?
	...
	(recusively-extended-environment
		(procedures-names (list-of symbol?))
		(procedures-parametes (list-of (list-of scheme-value?)))
		(bodies (list-of expression?))
		(env environment?))
)
```

También debemos agregar un nuevo caso para `apply-env`.

```RKT
(define apply-env (
	lambda (env var) (
		cases environment env
			...
			(recusively-extended-environment (procedures-names procedures-parameters procedures-bodies old-env) (
				let (
					(index (index-of var procedures-names))
				)
				(if index
					(closure
						(nth-element procedures-parameters index)
						(nth-element procedures-bodies index)
						env
					)
					(apply-env old-env var)
				)
			))
	)
))
```

Por último, debemos agregar el caso de `letrec-exp` a `eval-expression`.

```RKT
(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(letrec-exp (procedures-names procedures-parameters procedures-bodies body) (eval-expression body (recusively-extended-environment
					procedures-names
					procedures-parameters
					procedures-bodies
					env
				)
			))
			...
	)
))
```
