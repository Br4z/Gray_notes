---
id: j8rc6g2iu2hjtnqzmlhl4nd
title: 5-Primer interpretador simple
desc: ''
updated: 1695426675272
created: 1695345812525
---

## Interpretación

- El texto de un programa es escrito en un lenguaje llamado el lenguaje **fuente** o el lenguaje **definido**.

- Los programas son pasados a través de un **front end** que los analiza y construye el árbol de sintaxis abstracta.

- El árbol de sintaxis abstracta es pasado a un interpretador, que examina su estructura y desarrolla algunas acciones que dependen de esa estructura.

- Un interpretador está escrito en algún lenguaje. Este lenguaje es llamado el lenguaje de **implementación** o el lenguaje de **definición**.

!!!!![interpreter image]

## Compilación

- Un compilador traduce el árbol de sintaxis abstracta en otro lenguaje para ser ejecutado. Este lenguaje es llamado el lenguaje **destino**.

- El lenguaje generado puede ser ejecutado por un interpretador o puede ser traducido en un lenguaje de bajo nivel para su ejecución.

	> Los lenguajes generados (mas simples que el original) que posteriormente son interpretados son llamados lenguajes a **bytecode** y sus interpretadores **maquinas virtuales**.

!!!!![compiler image]

- Un compilador está dividido en dos partes: un **analizador** y un **traductor**.

## Interpretación y compilación

Sin importar, la estrategia que se utilice, es necesario definir un front end que convierta programas en árboles de sintaxis abstracta. Dado que los programas son solo cadenas de caracteres, el front end debe agrupar estos caracteres en unidades significativas. La agrupación de estas unidades es llevada en las etapas **scanning** y **parsing**.

### Scanning

Es el nombre que se le da al proceso de dividir la secuencia de caracteres en palabras, números, puntuación, comentarios, etc. Estas unidades son conocidas como unidades **léxicas**, **lexemas** o **tokens**. La especificación **léxica** de un lenguaje se refiere a la forma en la cual un programa debe ser dividido en unidades **léxicas**.

El scanner recibe una secuencia de caracteres y produce una secuencia de unidades léxicas (tokens).

---

Cuando el scanner encuentra un token, retorna una estructura de datos que consiste de al menos los siguientes datos:

- Una **clase**, la cual describe qué clase de token se encontró.

- Un dato que describe el token particular.

- Un dato que describe la ubicación del token en la entrada.

El conjunto de clases y la descripción de los tokens hacen parte de la especificación léxica.

### Parsing

Es el nombre que se le da al proceso de organizar una secuencia de tokens en estructuras sintácticas jerárquicas como expresiones, estamentos y bloques. La estructura **sintáctica** o **gramatical** de un lenguaje se refiere a la forma en la cual se deben organizar las unidades léxicas.

El parser recibe una secuencia de tokens del scanner y produce un árbol de sintaxis abstracta.

## SLLGEN

Es un generador de parsers que toma como entrada una especificación léxica y una gramática, y produce como salida, un scanner y un parser en Scheme. La especificación léxica en SLLGEN es una lista que satisface la siguiente gramática:

```
<scanner_spec>      := ( {<regexp_and_action>}* )
<regexp_and_action> := ( <name> ( {<regexp>}* ) <output> )
<name>              := <symbol>
<regexp>            := <string> | letter | digit | whitespace | any
                        ( not <character> ) | ( or {<regexp>}* )
                    := ( arbno <regexp> ) | ( concat {<regexp>}* )
<output>            := skip | symbol | number | string
```

Una gramática en SLLGEN es una lista descrita por la siguiente gramática:

```
<grammar>         := ( {<production>}* )
<production>      := ( <lhs> ( {rhs}* ) <production-name> )
<lhs>             := <symbol>
<rhs>             := <symbol> | <string>
                     ( arbno {<rhs>}* )
                     ( separated-list {<rhs>}* <string> )
<production-name> := <symbol>
```

La gramática debe permitir al parser determinar cuál producción usar conociendo solo:

- El símbolo no terminal se está buscando.

- El primer símbolo (token) de la cadena a ser analizada.

> Las gramáticas en esta forma son denominadas gramáticas LL (de allí el nombre SLLGEN - Scheme LL GENerator).

### Ejemplo (SLLGEN)

```
<statement> := {<statement> ; <statement>}
              := while <statement> do <statement>
              := <identifier> = <expression>
<expression>  := <identifier>
              := ( <expression> + <expression> )
```

Usando `define-dataype` los tipos de datos para esta gramática pueden ser descritos así:

```RKT
(define-datatype statement statement?
	(compound-statement (first statement?) (second statement?))
	(while-statement (argument expresion?) (body statement?))
	(assignment-statement (identifier symbol?) (expr expresion?))
)

(define-datatype expresion expresion?
	(var (identifier symbol?))
	(sum (adden1 expresion?) (adden2 expresion?))
)
```

> Dado que ya no podemos apoyarnos de la estructura implícita de las listas, hacer un parser y unparses para esta especificación es bastante "difícil", pues tendríamos que hacer procesamiento de string.

En SLLGEN la gramática puede ser descrita así:

```
(define lexica '(
	(white-sp (whitespace) skip)
	(comment ("//" (arbno (not #\newline))) skip)
	(identifier (letter (arbno (or letter digit "?"))) symbol)
	(number (digit (arbno digit)) number)
	(number ("-" digit (arbno digit)) number)
))

(define grammar
	'(
		(statement ("{" statement ";" statement "}") compound-statement)
		(statement ("while" expression "do" statement) while-statement)
		(statement (identifier "=" expression) assignment-statement)
		(expression (identifier) var)
		(expression ("(" expression "+" expression ")") sum)
	)
)
```

---

Necesitaremos las siguientes funciones para hacer uso del SLLGEN:

```RKT
(sllgen:make-define-datatypes lexica grammar)

(define show-the-datatypes (
	sllgen:list-define-datatypes lexica grammar
))

(define scan&parse (
	sllgen:make-string-parser lexica grammar
))

(define just-scan (
	sllgen:make-string-scanner lexica grammar
))
```

## Un interpretador simple

Nuestro primer lenguaje permitirá la evaluación de expresiones aritméticas. El lenguaje consistirá de expresiones para variables, números y aplicación de los operadores "+", "*", "-". "add1" y "sub1".

Cada lenguaje tiene como mínimo dos conjuntos de valores:

- Expresados: posibles valores de expresiones.

- Denotados: valores limitados a las variables.

Para nuestro primer lenguaje se tiene que:

$$
\text{ valor expresado } = \text{ número } \\[5 pt]

\text{ valor denotado } = \text{ número }
$$

La gramática será:

```
<program> := <expression>

<expression> := <number>
             := <identifier>
             := <primitive> ( {<expression>}* )

<primitive>  := + | - | add1 | sub1
```

La especificación léxica para el lenguaje será con la que ya trabajamos anteriormente.

- SLLGEN.

	```RKT
	(define grammar
		'(
			(program (expression) a-program)
			(expression (number) lit-exp)
			(expression (identifier) var-exp)
			(expression (primitive "(" (separated-list expression ",") ")" ) primapp-exp)
			(primitive ("+") add-prim)
			(primitive ("-") substract-prim)
			(primitive ("*") multi-prim)
			(primitive ("add1") incr-prim)
			(primitive ("sub1") decr-prim)
		)
	)
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
	)

	(define-datatype primitive primitive?
		(add-prim)
		(substract-prim)
		(mult-prim)
		(incr-prim)
		(decr-prim)
	)
	```

Con las funciones especificadas más arriba, SLLGEN nos construye el respectivo **parser** y **scanner**.

El interpretador simple constará de tres procedimientos correspondientes a los tres símbolos no terminales de la gramática. El procedimiento principal `eval-program`, toma un árbol de sintaxis abstracta y retorna un valor.

```RKT
(define init-env (
	lambda () (
		extended-environment '(i v x) '(1 5 10) (empty-environment)
	)
))

(define eval-program (
	lambda (pgm) (
		cases program pgm
			(a-program (body) (eval-expression body (init-env)))
	)
))

(define eval-rands (
	lambda (rands env) (
		map (lambda (x) (eval-expression x env)) rands
	)
))

(define eval-expression (
	lambda (exp env) (
		cases expression exp
			(lit-exp (value) value)
			(var-exp (identifier) (apply-env env identifier))
			(primapp-exp (prim rands) (
					let (
						(args (eval-rands rands env))
					)
					(apply-primitive prim args)
				)
			)
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
