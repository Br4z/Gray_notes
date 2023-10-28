---
id: g6uuuvc1jixwe69seobhenf
title: 9-Chequeo de tipos
desc: ''
updated: 1698457593690
created: 1698370233292
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
<expression-type> := int
                  := bool
				  := ({ <expression-type> }* -> <expression-type>)
```

---

El lenguaje que se está diseñando, será **fuerte** y **estáticamente** tipado, lo que significa que ningún programa que pasa el chequeo de tipos tendrá un error de tipos. Un error de tipo será un intento de:

- aplicar un entero o un booleano a un argumento.

- aplicar un procedimiento o primitiva a un número errado de argumentos.

- un intento de aplicar una primitiva que espera un entero a un no-entero.

- usar un no-booleano como la prueba de una expresión condicional.

> Los errores como una división por cero, no serán considerados como errores de tipo.

---

En un lenguaje con chequeo de tipos, se requiere que el programador incluya los tipos de todas las variables ligadas. Para hacer chequeo de tipos en el lenguaje del curso, se necesita cambiar la forma en que se escriben procedimientos (`proc-exp`) y recursion (`letrec-exp`).

```
<expression> := proc ( { <expression-type> <identifier> }* ) <expression>
             := letrec { <expression-type> <identifier> ({ <expression-type> <identifier> }*) = <expression> }* in <expression>
```

Antes de modificar las reglas de produccion asociadas a estas expresiones en la gramatica, debemos crear las reglas de produccion de `expression-type`.

```RKT
(define grammar '(
	...
	(type-expression ("int") int-type-exp)
	(type-expression ("bol") bool-type-exp)
	(type-expression ("(" (separated-list type-expression ",") "->" type-expression ")") proc-type-exp)
	...
	(expression ("letrec"
		(arbno type-expression identifier "(" (separated-list type-expression identifier ",") ")" "=" expression) "in" expression)
		letrec-exp)
	(expression ("proc" "(" (separated-list type-expression identifier ",") ")" expression) proc-exp)
	...
))
```

Ahora se definirán los valores (tipos) que pueden denotar las expresiones de tipo.

```RKT
(define-datatype type type? (
	(atomic-type (name symbol?))
	(procedure-type (parameters-types type?) (result-type type?))
))

(define ini-type (atomi-type 'int))

(define bool-type (atomi-type 'bool))
```
