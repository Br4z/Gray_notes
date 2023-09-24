---
id: 8u558ml4ielcwb2loe3ijl2
title: 4-Abstracción de datos y sintaxis abstracta
desc: ''
updated: 1695492695541
created: 1694720220951
---

## Abstracción de datos

- En un tipo de dato se define los valores, representaciones y operaciones sobre el mismo.

- La abstracción de datos se divide en dos partes:

	- Interfaz: nos dice lo que representa el tipo de dato, sus operaciones y las propiedades de dichas operaciones.

	- Implementación: proporciona una representación específica y un código para las operaciones que hacen uso de esa representación.

- Un tipo de dato con una interfaz y una implementación es denominado Tipo Abstracto de Dato (TAD).

- El resto del programa fuera del tipo de dato, es llamado el **cliente** del tipo de dato. El cliente manipula el nuevo dato **solamente** mediante las operaciones especificadas en la interfaz.

	> El código cliente es independiente de la implementación del tipo de datos.

- Se utiliza la notación $\lceil v \rceil$ para la representación del dato $v$.

---

Ejemplo de tipo de datos para la representación de números naturales:

$$
(\text{ zero }) = \lceil 0 \rceil \\[10 pt]

(\text{ is-zero? } \lceil n \rceil) =
	\left \{
		\begin{array}{ll}
			true  & n = 0 \\
			false & n \neq 0
		\end{array}
	\right .\\[10 pt]

(\text{ successor } \lceil n \rceil) = \lceil n + 1 \rceil \quad n \geq 0 \\[10 pt]

(\text{ predecessor } \lceil n \rceil) = \lceil n - 1 \rceil \quad n \geq 0
$$

Dentro de esta interfaz podemos identificar constructores (zero, sucessor, predecessor) y un obserador (is-zero?).

- La especificación no indica cómo se representan los números naturales.

- A partir de la especificación se pueden escribir programas para la manipulación de los datos, sin importar su representación.

---

Definición de una función `addition` que suma dos números naturales sin importar su representación:

```RKT
(define addition (
	lambda (number1 number2) (
		cond
			[(is-zero? number1) number2]
			[else (sucessor (addition (predecessor number1) number2))]
	)
))
```

Satisface $(\text{ addition } \lceil x \rceil \lceil y \rceil) = \lceil x + y \rceil$, sin importar la implementación de números naturales que se utilice.

Otras operaciones que podemos representar son:

- Resta.

	```RKT
	(define subtraction (
		lambda (number1 number2) (
			cond
				[(is-zero? number2) number1]
				[else (predecessor (subtraction number1 (predecessor number2)))]
		)
	))
	```

- Multiplicación.

	```RKT
	(define multiplication (
		lambda (number1 number2) (
			cond
				[(is-zero? number2) number2]
				[else (addition number1 (multiplication number1 (predecessor number2)))]
		)
	))
	```

- División.

	```RKT
	(define division (
		lambda (number1 number2) (
			letrec (
				(get-result ( ; Int divisions
					lambda (number1 number2 result) (
						cond
							[(is-zero? number1) result]
							[else (get-result (subtraction number1 number2) number2 (addition result (sucessor (zero))))]
					)
				))
			)
			(get-result number1 number2 (zero))
		)
	))
	```

- Potencia.

	```RKT
	(define pow (
		lambda (number1 number2) (
			cond
				[(is-zero? number2) (sucessor (zero))]
				[else (multiplication number1 (pow number1 (predecessor number2)))]
		)
	))
	```

- Factorial.

	```RKT
	(define factorial (
		lambda (number) (
			cond
				[(is-zero? number) (sucessor (zero))]
				[else (multiplication number (factorial (predecessor number)))]
		)
	))
	```

---

Una posible implementacion de los numeros enteros puede ser:

```RKT
(define zero (
	lambda () 0
))

(define is-zero? (
	lambda (number) (
		eqv? number 0
	)
))

(define sucessor (
	lambda (n) (
		+ n 1
	)
))

(define predecessor (
	lambda (n) (
		- n 1
	)
))
```

### Representacion Bignum

Los números son representados en base $N$, para algún entero grande $N$. Dicha representación es una lista que consiste de números entre 0 y $N − 1$.

$$
\lceil n \rceil =
	\left \{
		\begin{array}{ll}
			() & n = 0 \\
			cons(r , \lceil q \rceil) & n = q N + r \quad 0 \leq 0 < N
		\end{array}
	\right .
$$

- `zero`.

	```RKT
	(define zero (
		lambda () empty
	))
	```

- `is-zero?`.

	```RKT
	(define is-zero? (
		lambda (number) (
			empty? number
		)
	))
	```

- `successor`.

- `predecessor`.

### Ambientes

Un ambiente:

- asocia un valor con cada elemento de un conjunto finito de variables.

- puede ser usado para asociar las variables con sus valores en la implementación de un lenguaje de programación.

- es una función cuyo dominio es un conjunto finito de variables y cuyo rango es el conjunto de todos los valores de Scheme.

	Entonces los ambientes representan todos los conjuntos de la forma:

	$$
	\{ (\text{ var }_1 , \text{ val }_1) , \dots , (\text{ var }_n , \text{ val }_n) \}
	$$

	> Las variables pueden ser representadas de cualquier manera, siempre y cuando sea posible chequear la igualdad entre dos variables.

#### Interfaz

$$
(\text{ empty-env }) = \lceil \emptyset \rceil \\[10 pt]

(\text{ apply-env } \lceil f \rceil \; var) = f(\text{ var }) \\[10 pt]

(\text{ extend-env } var \; val \; \lceil f \rceil) = \lceil g \rceil \\[10 pt]

g(\text{ var }_1) =
	\left \{
		\begin{array}{ll}
			val & \text{ si } val = \text{ var }_1 \\
			f(\text{ var }_1)
		\end{array}
	\right .
$$

empty-env y extend-env son los constructores y apply-env es el único observador.

#### Implementación

Cada ambiente puede ser construido mediante una expresión en la siguiente gramática:

```
<env-exp> ::= (empty-env)
          ::= (extend-env <identifier> <scheme-value> <env-exp>)
```

- `(empty-env)`.

	Debe producir una representación del ambiente vacío.

	```RKT
	(define empty-env (
		lambda () (list 'empty-env)
	))
	```

- `(entend-env var val env)`.

	Produce un nuevo ambiente que se comporta como "env", excepto que su valor en el símbolo "var" es "val".

	```RKT
	(define extend-env (
		lambda (var val env) (
			list 'extend-env var val env
		)
	))
	```

- `(apply-env env var)`.

	Busca una variable (su valor) en el ambiente.

	```RKT
	(define apply-env (
		lambda (env var) (
			cond
				[(eqv? (car env) 'empty-env) (format "No binding for ~s" var)]
				[(eqv? (car env) 'extend-env) (
					let (
						(saved-var (cadr env))
						(saved-val (caddr env))
						(saved-env (cadddr env))
					)
						(if (eqv? var saved-var)
							saved-val
							(apply-env saved-env var))
				)]
				[else (format "Expecting an environment, given ~s" env)]
		)
	))
	```

---

Implementación de una pila usando listas:

```RKT
(define empty-stack (
	lambda () (list 'empty-stack)
))


(define empty-stack? (
	lambda (stack) (eqv? (car stack) 'empty-stack)
))


(define push (
	lambda (element stack) (cons element stack)
))


(define pop (
	lambda (stack) (
		if (not (eqv? (car stack) 'empty-stack))
			(cdr stack)
			"Error: the list is empty"
	)
))


(define top (
	lambda (stack) (
		if (not (eqv? (car stack) 'empty-stack))
			(car stack)
			"Error: the list is empty"
	)
))
```

---

Las implementaciones de los datos propuestos hasta ahora se han hecho en listas, por lo que se establece cierta dependencia entre la interfaz y como el lenguaje de programación maneja las listas. Apoyándonos en los **constructores** y **observadores** (tanto predicados como extractores) podemos solucionar esto.

Para las expresiones del cálculo $lambda$ tenemos la siguiente interfaz:

- Constructores.

	$$
	\begin{array}{ll}
		\text{ var-exp }    &: var \rightarrow \text{ lambda\_calculus-exp } \\
		\text{ lambda-exp } &: var \times \text{ lambda\_calculus-exp } \rightarrow \text{ lambda\_calculus-exp } \\
		\text{ apply-exp }  &: \text{ lambda\_calculus-exp } \times \text{ lambda\_calculus-exp } \rightarrow \text{ lambda\_calculus-exp }
	\end{array}
	$$

	En Racket sería:

	```RKT
	(define var-exp (
		lambda (symbol) symbol
	))

	(define lambda-exp (
		lambda (symbol body) (list 'lambda (list symbol) body)
	))

	(define apply-exp (
		lambda (rator rand) (list rator rand)
	))
	```

	> En este caso estamos trabajando con listas de Racket.

- Predicados.

	$$
	\begin{array}{ll}
		\text{ var-exp? }    &: \text{ lambda\_calculus-exp } \rightarrow bool \\
		\text{ lambda-exp? } &: \text{ lambda\_calculus-exp } \rightarrow bool \\
		\text{ apply-exp? }  &: \text{ lambda\_calculus-exp } \rightarrow bool
	\end{array}
	$$

	En Racket sería:

	```RKT
	(define var-exp? (
		lambda (exp) (symbol? exp)
	))

	(define lambda-exp? (
		lambda (exp) (
			if (and (eqv? (car exp) 'lambda) (= (length exp) 3))
				#t
				#f
		)
	))

	(define apply-exp? (
		lambda (exp) (= (length exp) 2)
	))

	(define is-lambda_calculus? (
		lambda (exp) (
			cond
				[(var-exp? exp) #t]
				[(lambda-exp? exp) (
					and (is-lambda_calculus? (lambda-exp->var exp))
					(is-lambda_calculus? (lambda-exp->body exp))
				)]
				[(apply-exp? exp) (
					and (is-lambda_calculus? (apply-exp->rator exp))
					(is-lambda_calculus? (apply-exp->rand exp))
				)]
		)
	))
	```

- Extractores.

	$$
	\begin{array}{ll}
		\text{ var-exp }               &: \text{ lambda\_calculus-exp } \rightarrow var \\
		\text{ lambda-exp->bound-var } &: \text{ lambda\_calculus-exp } \rightarrow var \\
		\text{ lambda-exp->body }      &: \text{ lambda\_calculus-exp } \rightarrow \text{ lambda\_calculus-exp } \\
		\text{ apply-exp->rator }      &: \text{ lambda\_calculus-exp } \rightarrow \text{ lambda\_calculus-exp } \\
		\text{ apply-exp->rand }       &: \text{ lambda\_calculus-exp } \rightarrow \text{ lambda\_calculus-exp }
	\end{array}
	$$

	En Racket sería:

	```RKT
	(define var-exp->var (
		lambda (exp) exp
	))

	(define lambda-exp->var (
		lambda (exp) (cadr exp)
	))

	(define lambda-exp->body (
		lambda (exp) (caddr exp)
	))

	(define apply-exp->rator (
		lambda (expr) (car expr)
	))

	(define apply-exp->rand (
		lambda (expr) (cadr expr)
	))
	```

Con esta interfaz ahora podemos definir un `occurs-free?` más genérico:

```RKT
(define occurs-free? (
	lambda (var exp) (
		cond
			[(var-exp? exp) (eqv? var (var-exp->var exp))]
			[(lambda-exp? exp)
				(and (not (eqv? var (var-exp->var exp)))
					(occurs-free? var (lamda-exp->body exp)))]
			[else (or (occurs-free? var (app-exp->rator exp))
				(occurs-free? var (app-exp->rand exp)))]
	)
))
```

---

Receta general para el diseño de interfaces de datos recursivos, estas deben incluir un:

1. constructor para cada clase de dato (regla de producción) en el tipo de dato.

2. predicado para cada clase de dato en el tipo de dato.

3. extractor para cada pieza de dato pasada a un constructor del tipo de dato.

---

La interfaz `define-datatype` es una herramienta de Scheme para construir e implementar interfaces para tipos de datos:

```
(define-datatpe <name> <predicate name>
{ (<variant name> { (<field name> <predicate>) }* ) }*)
```

Por ejemplo, la definición del cálculo $lambda$:

```RKT
(define-datatype lambda_calculus-exp lambda_calculus-exp?
	(var-exp (identifier symbol?))
	(lambda-exp (identifier symbol?) (body lambda_calculus-exp?))
	(apply-exp (rator lambda_calculus-exp?) (rand lambda_calculus-exp?))
)
```

---

Para determinar a que objeto de un tipo de dato pertenece una variante y extraer sus componentes, se usan los `cases`:

```
(cases <name> <expression>
	{ (<variant name> (<field name>*) <return sentence>) }*
	(else <default>))
```

> Si no existe una cláusula `else`, entonces tiene que existir una variante para todos los tipos de dato.

Con esta nueva forma de definir tipos de datos podemos representar el `occurs-free?` de la siguiente forma:

``` RKT
(define occurs-free? (
	lambda (var exp) (
		cases lambda_calculus-exp exp
			(var-exp (saved-var)
				(eqv? var saved-var))
			(lambda-exp (bound-var body)
				(and (not (eqv? var bound-var))
					(occurs-free? var body)))
			(apply-exp (rator rand)
				(or (occurs-free? var rator)
					(occurs-free? var rand)))
	)
))
```

---

La implementación para [[s_list | university.6th semester.Fundamentos de interpretación y compilación de lenguajes de programación.Classes.3-Relación entre inducción y programación - Especificación recursiva de datos y programas#especificacion-mediante-gramaticas]] podría con `define-datatype` ser:

```RKT
(define-datatype s_list s_list?
	(empty-s_list)
	(non-empty-s_list (first s_exp?) (rest s_list?))
)

(define-datatype s_exp s_exp?
	(symbol-s_exp (symbol symbol?))
	(s_list-s_exp (list s_list?))
)
```

---

La implementación de árboles binarios con `define-datatype` podría ser:

```RKT
(define-datatype binary_tree binary_tree?
	(leaf-node (value number?))
	(interior-node
		(value symbol?)
		(left binary_tree?)
		(right binary_tree?))
)
```

Sobre esta estructura generada podemos crear procedimientos para operar sobre ellas usando `cases`. Por ejemplo:

```RKT
(define leaves-sum (
	lambda (tree) (
		cases binary_tree tree
			(leaf-node (value) value)
			(interior-node (value left right)
				(+ (leaves-sum left) (leaves-sum right)))
	)
))
```

---

La implementación de ambientes con `define-datatype` podría ser:

```RKT
(define-datatype environment environment?
	(empty-environment)
	(extended-environment
		(symbols (list-of symbol?))
		(values (list-of scheme-value?))
		(env environment?))
)

(define scheme-value? (lambda (anything) #t))
```

Una forma de implementar `apply-env` podría ser:

```RKT
(define nth-element (
	lambda (list n) (
		cond
			[(zero? n) (car list)]
			[else (nth-element (cdr list) (- n 1))]
	)
))

(define index-of (
	lambda (element list) (
		letrec (
			(get-index (
				lambda (element list index) (
					cond
						[(empty? list) #f]
						[(eqv? (car list) element) index]
						[else (get-index element (cdr list) (+ index 1))]
				)
			))
		)
		(get-index element list 0)
	)
))

(define apply-env (
	lambda (env var) (
		cases environment env
			(empty-environment () (format "No binding for ~s" var))
			(extended-environment (symbols values saved-env) (
					let (
						(position (index-of var symbols))
					)
					(if position
						(nth-element values position)
						(apply-env saved-env var)
					)
				)
			)
	)
))
```

### Sintaxis abstracta

Para crear una sintaxis abstracta a partir de una sintaxis concreta, se debe nombrar cada regla de producción de la sintaxis concreta y cada ocurrencia de un símbolo no terminal. Por ejemplo, el cálculo [[lambda_calculus | university.6th semester.Fundamentos de interpretación y compilación de lenguajes de programación.Classes.3-Relación entre inducción y programación - Especificación recursiva de datos y programas#especificacion-mediante-gramaticas]] sería:

```
<lambda_calculus> ::= var-exp (id)
                  ::= lamda-exp (id body)
                  ::= apply-exp (rator rand)
```

La sintaxis abstracta de una expresión es más fácil de comprender visualizándola como un **árbol de sintaxis abstracta**. Por ejemplo, el de la expresión `(lambda (x) (f (f x)))` es:

---

El problema de convertir un árbol de sintaxis abstracta a una representación lista-y-símbolo (con lo cual Scheme mostraría las expresiones en su sintaxis concreta), se resuelve con el procedimiento **unparse**. Para las expresiones del cálculo $lambda$ sería (con la implementación propuesta):

```RKT
(define unparse-lambda_calculus-expression (
	lambda (exp) (
		cases lambda_calculus-exp exp
			(var-exp (identifier) identifier)
			(lambda-exp (identifier body) (list 'lambda (list identifier)
				(unparse-lambda_calculus-expression body)))
			(apply-exp (rator rand) (list
				(unparse-lambda_calculus-expression rator)
				(unparse-lambda_calculus-expression rand)))
	)
))
```

La tarea de derivar el árbol de sintaxis abstracta a partir de una cadena de caracteres es denominado **parsing**, y es llevado a cabo por un programa llamado parser (analizador sintáctico). Para las expresiones del cálculo $lambda$ sería (con la implementación propuesta):

```RKT
(define parse-lambda_calculus-expresion (
	lambda (expr) (
		cond
			[(symbol? expr) (var-exp expr)]
			[(eqv? (car expr) 'lambda)
				(lambda-exp (cadr expr)
						(parse-lambda_calculus-expresion (caddr expr)))]
			[else (apply-exp
					(parse-lambda_calculus-expresion (car expr))
					(parse-lambda_calculus-expresion (cadr expr)))]
	)
))
```
