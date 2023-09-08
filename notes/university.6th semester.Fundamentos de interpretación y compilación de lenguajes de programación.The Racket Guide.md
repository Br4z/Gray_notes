---
id: z6bvbj938x49neokd6i7vo0
title: The Racket Guide
desc: ''
updated: 1693157495094
created: 1693080276230
---


## Welcome to Racket

### 1.1 Interacting with Racket

Racket uses parentheses to wrap larger expressions—almost any kind of expression, other than simple constants.

```RKT
(substring "the boy out of the country" 4 7)
```

## 1.2 Definitions and Interactions

```RKT
(define (extract str)
	(substring str 4 7))
```

```
> (enter! "extract.rkt")
> (extract "the gal out of the city")

"gal"
```

When using command-line racket instead of DrRacket, you'd save the above text in a file using your favorite editor.

### 1.3 Creating Executables

- From a command-line prompt, run `raco exe ‹src-filename›`, where "src-filename" contains the program.

## 2 Racket Essentials

### 2.2 Simple Definitions and Expressions

#### 2.2.1 Definitions

A definition of the form

```
( define ‹id› ‹expr› )
```

binds "id" to the result of "expr", while

```
(define ( ‹id› ‹id›* ) ‹expr›+)
```

binds the first "id" to a function (also called a procedure) that takes arguments as named by the remaining ids. In the function case, the expressions are the body of the function. When the function is called, it returns the result of the last "expr".

```RKT
(define pie 3)             ; defines pie to be 3

(define (piece str)        ; defines piece as a function
	(substring str 0 pie)) ; of one argument
```

```
> pie

3
> (piece "key lime")

"key"
```

Under the hood, a function definition is really the same as a non-function definition, and a function name does not have to be used in a function call. A function is just another kind of value, though the printed form is necessarily less complete than the printed form of a number or string.

```
> piece

#<procedure:piece>
> substring

#<procedure:substring>
```

---

Racket programmers prefer to avoid side-effects, so a definition usually has just one expression in its body. It's important, though, to understand that multiple expressions are allowed in a definition body, because it explains why the following "nobake" function fails to include its argument in its result:

```RKT
(define (nobake flavor)
	string-append flavor "jello")
```

```
> (nobake "green")

"jello"
```

Within "nobake", there are no parentheses around `string-append flavor "jello"`, so they are three separate expressions instead of one function-call expression. The expressions string-append and flavor are evaluated, but the results are never used. Instead, the result of the function is just the result of the final expression, "jello".

#### 2.2.5 Conditionals with "if", "and", "or", and "cond"

```
( if ‹expr› ‹expr› ‹expr› )
```

The first "expr" is always evaluated. If it produces a non-`#f` value, then the second "expr" is evaluated for the result of the whole if expression, otherwise the third "expr" is evaluated for the result.

```RKT
(define (reply s)
	(if (string-prefix? s "hello ")
		"hi!"
		"huh?"))
```

```
> (reply "hello racket")

"hi!"
> (reply "λx:(μα.α→α).xx")

"huh?"
```

The input must be a string because `string-prefix?` would error when given non-strings. You can remove this restriction by adding another if to check first if the input is a string:

```RTK
(define (reply-non-string s)
	(if (if (string? s)
			(string-prefix? s "hello ")
			#f)
		"hi!"
		"huh?"))
```

but these kinds of nested `if`s are difficult to read. Racket provides more readable shortcuts through the `and` and `or` forms:

```
(and ‹expr›*)
(or ‹expr›*)
```

```RKT
(define (reply-non-string s)
	(if (and (string? s) (string-prefix? s "hello "))
		"hi!"
		"huh?"))
```

Another common pattern of nested ifs involves a sequence of tests, each with its own result:

```RKT
(define (reply-more s)
	(if (string-prefix? s "hello ")
		"hi!"
		(if (string-prefix? s "goodbye ")
			"bye!"
			(if (string-suffix? s "?")
				"I don't know"
				"huh?"))))
```

The shorthand for a sequence of tests is the `cond` form:

```
( cond {[ ‹expr› ‹expr›* ]}* )
```

`cond` works similary to a `swith` in C++ or JavaScript. It contains a sequence of clauses between square brackets. In each clause, the first "expr" is a test expression. If it produces true, then the clause’s remaining expressions are evaluated, and the last one in the clause provides the answer for the entire cond expression; the rest of the clauses are ignored. If the test "expr" produces `#f`, then the clause’s remaining expressions are ignored, and evaluation continues with the next clause. The last clause can use `else` as a synonym for a `#t` test expression.

```RTK
(define (reply-more s)
	(cond
		[(string-prefix? s "hello ")
		"hi!"]
		[(string-prefix? s "goodbye ")
		"bye!"]
		[(string-suffix? s "?")
		"I don't know"]
		[else "huh?"]))
```

```
> (reply-more "hello racket")

"hi!"
> (reply-more "goodbye cruel world")

"bye!"
> (reply-more "what is your favorite color?")

"I don't know"
> (reply-more "mine is lime green")

"huh?"
```

> The use of square brackets for cond clauses is a convention. In Racket, parentheses and square brackets are actually interchangeable, as long as `(` is matched with `)` and `[` is matched with `]`. Using square brackets in a few key places makes Racket code even more readable.

#### 2.2.6 Function Calls, Again

```RKT
(define (double v)
	((if (string? v) string-append +) v v))
```

```
> (double "mnah")

"mnahmnah"
> (double 5)

10
```

#### 2.2.7 Anonymous Functions with lambda

In Racket, you can use a lambda expression to produce a function directly. The lambda form is followed by identifiers for the function’s arguments, and then the function’s body expressions:

```
( lambda ( ‹id›* ) ‹expr›+ )
```

---

Evaluating a lambda form by itself produces a function:

```
> (lambda (s) (string-append s "!"))

#<procedure>
```

---

Using examples:

1. .

	```RTK
	(define (twice f v)
		(f (f v)))
	```

	```
	> (twice (lambda (s) (string-append s "!"))
				"hello")

	"hello!!"
	> (twice (lambda (s) (string-append s "?!"))
				"hello")

	"hello?!?!"
	```

2. .

	```RKT
	(define (make-add-suffix s2)
		(lambda (s) (string-append s s2)))
	```

	```
	> (twice (make-add-suffix "!") "hello")

	"hello!!"
	> (twice (make-add-suffix "?!") "hello")

	"hello?!?!"
	> (twice (make-add-suffix "...") "hello")

	"hello......"
	```

---

The following two definitions of "louder" are equivalent:

```RKT
(define (louder s)
	(string-append s "!"))

(define louder
	(lambda (s)
		(string-append s "!")))
```

> The expression for louder in the second case is an “anonymous” function written with lambda, but, if possible, the compiler infers a name, anyway, to make printing and error reporting as informative as possible.

#### 2.2.8 Local Binding with "define", "let", and "let*"

Remembering the way to declare "define" and "lambda":

```
(define (‹id› ‹id›*) ‹definition›* ‹expr›+)
(lambda (‹id›*) ‹definition›* ‹expr›+)
```

Definitions at the start of a function body are local to the function body, for example:

```RKT
(define (converse s)
	(define (starts? s2) ; local to converse
		(define spaced-s2 (string-append s2 " ")) ; local to starts?
		(string-prefix? s spaced-s2))
	(cond
		[(starts? "hello") "hi!"]
		[(starts? "goodbye") "bye!"]
		[else "huh?"]))
```

```
> (converse "hello world")

"hi!"
> (converse "hellonearth")

"huh?"
> (converse "goodbye friends")

"bye!"
> (converse "urp")

"huh?"
> starts? ; outside of converse, so...

starts?: undefined;

starts?: undefined;

	cannot reference an identifier before its definition

		in module: top-level
```

---

Another way to create local bindings is the `let` form. An advantage of `let` is that it can be used in any expression position. Also, `let` binds many identifiers at once, instead of requiring a separate define for each identifier.

```
( let ( {[ ‹id› ‹expr› ]}* ) ‹expr›+ )
```

Each binding clause is an "id" and an "expr" surrounded by square brackets, and the expressions after the clauses are the body of the let. In each clause, the "id" is bound to the result of the "expr" for use in the body.

The bindings of a `let` form are available only in the body of the `let`, so the binding clauses cannot refer to each other. The `let*` form, in contrast, allows later clauses to use earlier bindings:

```
> (let* (
		[x (random 4)]
		[o (random 4)]
		[diff (number->string (abs (- x o)))])
	(cond
		[(> x o) (string-append "X wins by " diff)]
		[(> o x) (string-append "O wins by " diff)]
		[else "cat's game"]))

"cat's game"
```
