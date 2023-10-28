---
id: zm1zsv7ajoorojoa8qta4bm
title: 8-Asignación de variables - Paso de parámetros por valor y referencia
desc: ''
updated: 1698450440961
created: 1698284416854
---

Diferencias entre ligadura y asignación:

- La ligadura de una variable es una acción local, mientras que la asignación de una variable es potencialmente global.

- Una ligadura crea una nueva asociación de un nombre con un valor, mientras que la asignación cambia el valor de una ligadura existente.

---

Nuestro lenguaje será extendido para incorporar ejecución secuencial de expresiones y asignación de variables. El lenguaje consistirá de las expresiones especificadas anteriormente y de expresiones para ejecución secuencial `begin ...; ... end` y asignación de variables `set ... = ...`. Para este lenguaje se extiende el conjunto de valores expresados y denotados de la siguiente manera:

$$
\text{ valor expresado } = \text{ número } + \text{ booleano } + \text{ procedimiento } \\[10 pt]

\text{ valor denotado } = Ref( \text{ valor expresado } )
$$

Se añaden las siguientes producciones a la gramática:

```
<expression> := set <identifier> = <expression>

             := begin expression { ; <expression> }*
```

Debemos agregar lo siguiente a `grammar`:

```RKT
(define grammar '(
	...
	(expression ("begin" expression (arbno ";" expression ) "end") begin-exp)
	(expression ("set" identifier "=" expression) set-exp)
	...
))
```

Para determinar el valor de una expresión `begin(exp exps)` se debe evaluar la expresión `exp` y cada una de las expresiones `exps`. Si `exps` es una lista vacía de expresiones, se debe retornar el valor de la expresión `exp`. En caso contrario, se debe retornar el valor de la última expresión en `exps`.

```RKT
(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(begin-exp (exp exps) (
				let loop ((acc (eval-expression exp env)) (exps exps))
					(if (null? exps)
						acc
						(loop (eval-expression (car exps) env) (cdr exps))
					)
			))
			...
	)
))
```

Para evaluar una expresión de asignación de variables (`set`) se debe evaluar la expresión de la parte derecha de la asignación. Luego, se debe modificar el contenido correspondiente a la variable con identificador igual a la parte izquierda de la asignación por este valor. El resultado de la expresión de asignación original es cualquier valor simbólico, dado que esta expresión solo causa un efecto, pero no produce un valor.

```RKT
(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(set-exp (id rhs-exp) (
				begin (
					set-ref (apply-env env id) (eval-expression rhs-exp env)
				)
				1
			))
	)
))
```

---

Con la inclusión de la asignación de variables surge otro problema. Cuando se crea un procedimiento se guarda el estado del ambiente, por esta razón al hacer un llamado al procedimiento, este se ejecuta sobre el ambiente que tiene almacenado y por ende no es sensible a los cambios en las variables del ambiente. Para evitar el problema anterior, cada identificador debe denotar la dirección de una ubicación en memoria (la memoria es también llamada **store**). Dicha dirección se denomina referencia y lo que hace la asignación es modificar su contenido. Dicha dirección se denomina referencia y lo que hace la asignación es modificar su contenido.

Una referencia es un tipo de dato que contiene dos campos: un entero y un vector. El entero corresponde a la posición en el vector del valor asociado a la referencia. La interfaz del tipo de dato referencia consta de un procedimiento constructor y dos procedimientos observadores `deref` y `set-ref`.

```RKT
(define-datatype reference reference?
	(a-ref (position integer?) (vector vector?))
)

(define deref (
	lambda(ref) (
		cases reference ref
			(a-ref (pos vec) (vector-ref vec pos))
	)
))

(define set-ref (
	lambda(ref val) (
		cases reference ref
			(a-ref (pos vec) (vector-set! vec pos val))
	)
))
```

---

Para implementar asignación, es necesario modificar el funcionamiento de los ambientes.

```RKT
(define-datatype environment environment?
	(empty-environment)
	(extended-environment
		(symbols (list-of symbol?))
		(vec vector?)
		(env environment?))
)

(define extend-env (
	lambda (syms vals env) (
		extended-environment syms (list->vector vals) env
	)
))

(define extend-env-recursively (
	lambda (procedures-names procedures-parametes bodies old-env) (
		let* (
			(len (length procedures-names))
			(vec (make-vector len))
			(env (extended-environment procedures-names vec old-env))
		)
		(for-each (
			lambda (pos parameters body) (
				vector-set! vec pos (closure parameters body env)
			))
			(iota len) procedures-parametes bodies)
		env
	)
))
```

Ası́ mismo, se modificara la operación `apply-env` para que cuando se encuentre un identificador, se retorne la referencia en vez de su valor.

```RKT
(define apply-env (
	lambda (env var) (
		cases environment env
			(empty-environment () (format "No binding for ~s" var))
			(extended-environment (symbols values old-env) (
					let (
						(index (index-of var symbols))
					)
					(if index
						(a-ref index values)
						(apply-env old-env var)
					)
				)
			)
	)
))
```

---

```RKT
let
	x = 100
in
	let
		p = proc (x)
			begin
				set x = add1(x);
				x
			end
	in
		+((p x), (p x))
```

El valor de esta expresion es 202 y no 203, porque estamos pasando los parametros por **vallor** y no por referencia.

> Cuando se hace una asignación a un parámetro formal, la asignación es local al procedimiento.

---

Algunas veces es deseable que se permita pasar a un procedimiento variables con el objetivo de que éstas sean asignadas por dicho procedimiento. Lo anterior se realiza pasando al procedimiento una referencia a la ubicación de la variable y no su contenido.

> Este mecanismo es denominado llamado o paso por **referencia**.

Cuando se añade paso por referencia, los identificadores aún denotan referencias a valores expresados, luego los conjuntos no cambian. Sin embargo, el cambio ocurre cuando se crean nuevas referencias. En los llamados por valor, una nueva referencia es creada **para cada evaluación de un operando**. En los llamados por referencia, una nueva referencia es creada para **cada evaluación de un operando distinto a una variable**.

Para la implementación del llamado por referencia, una referencia será (como en llamado por valor) una pareja de una ubicación y un vector. La diferencia está en el contenido del vector, este puede ser:

- Blanco directo: el comportamiento del programa es igual al de paso por valor.

- Blanco indirecto: corresponde al nuevo comportamiento del llamado por referencia, en el cual no son creadas nuevas ubicaciones.

Un blanco (target) es un tipo de dato definido de la siguiente manera:

```RKT
(define-datatype target target?
	(direct-target (expval expval?))
	(indirect-target (ref ref-to-direct-target?))
)
```

Los procedimientos correspondientes al tipo de dato target son:

- `expval?`: retorna `#t` si la entrada es un valor expresado, esto es, un número o un procedimiento.

	```RKT
	(define expval? (
		lambda (x) (or (number? x) (procedure? x))
	))
	```

- `ref-to-direct-target?`: retorna `#t` si la entrada es una referencia a un valor.

	```RKT
	(define ref-to-direct-target? (
		lambda (x) (
			and (reference? x) (
				cases reference x
					(a-ref (pos vec) (
						cases target (vector-ref vec pos)
								(direct-target (v) #t)
								(indirect-target (v) #f))
					)
				)
		)
	))
	```

La implementación (procedimientos `deref` y `set-ref`) de la interfaz para el tipo de dato referencia cambian. Las nuevas definiciones observan el tipo de blanco almacenado en la referencia para determinar el valor expresado a retornar o la ubicación a cambiar.

- `deref`.

	- Si el blanco es directo se retorna su valor.

	- Si el blanco es indirecto (corresponde a una referencia a otra referencia) se busca el valor de la referencia interna.

	```RKT
	(define primitive-deref (
		lambda(ref) (
			cases reference ref
				(a-ref (pos vec) (vector-ref vec pos))
		)
	))

	(define deref (
		lambda (ref) (
			cases target (primitive-deref ref)
				(direct-target (expval) expval)
				(indirect-target (ref1) (
					cases target (primitive-deref ref1)
						(direct-target (expval) expval)
						(indirect-target (ref3) (eopl:error 'deref "Illegal reference: ~s" ref1))))
		)
	))
	```

- `set-ref`.

	- Si el blanco es directo, se modifica la referencia de la entrada.

	- Si el blanco es indirecto (corresponde a una referencia a otra referencia) se modifica el valor de la referencia interna.

	> En ambos casos el nuevo valor se almacena como un blanco directo.

	```RKT
	(define primitive-set-ref (
		lambda(ref val) (
			cases reference ref
				(a-ref (pos vec) (vector-set! vec pos val))
		)
	))

	(define set-ref (
		lambda (ref expval) (
			let (
				(ref (cases target (primitive-deref ref)
					(direct-target (expval1) ref)
					(indirect-target (ref1) ref1)))
			)
			(primitive-set-ref ref (direct-target expval))
		)
	))
	```

---

Para ligadura local (expresiones `let`), se mantiene el comportamiento de los llamados por valor pero se hacen las modificaciones correspondientes para que los valores almacenados correspondan a blancos directos.

```RKT
(define eval-let_exp-expression (
	lambda (expression env) (
		direct-target (eval-expression expression env)
	)
))

(define eval-let_exp-expressions (
	lambda (expressions env) (
		map (lambda (expression) (eval-let_exp-expression expression env)) expressions
	)
))

(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(let-exp (identifiers expressions body) (
				let (
					(args (eval-let_exp-expressions expressions env))
				)
				(eval-expression body (extend-env identifiers args env))
			))
			...
	)
))
```

---

Para la aplicación de procedimientos, se evalúa cada operando usando el procedimiento `eval-rand`.

- Si el operando no es una variable, entonces se crea una nueva ubicación retornando el blanco directo.

- Si el operando es una variable y esta denota una ubicación que contiene un valor expresado, se retorna un blanco indirecto que apunta a dicha ubicación.

- Si el operando es una variable y esta denota una ubicación que contiene un blanco directo, entonces una referencia a la ubicación es retornada.

```RKT
(define eval-rands (
	lambda (rands env) (map (lambda (x) (eval-rand x env)) rands))
)

(define eval-rand (
	lambda (rand env) (
		cases expression rand
			(var-exp (id) (
				indirect-target (
					let (
						(ref (apply-env env id))
					)
					(cases target (primitive-deref ref)
						(direct-target (expval) ref)
						(indirect-target (ref1) ref1)
					)
				)
			))
			(else (direct-target (eval-expression rand env)))
	)
))

(define eval-expression (
	lambda (exp env) (
		cases expression exp
			...
			(app-exp (rator rands) (
				let (
					(proc (eval-expression rator env))
					(args (eval-rands rands env))
				)
				(if (procedure? proc)
					(apply-procedure proc args)
					(eopl:error "exp ~s is not a procedure" proc)
				)
			))
			...
	)
))
```
