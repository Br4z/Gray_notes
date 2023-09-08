---
id: 49yuppzbulwsg846tjqxn40
title: 6-Funciones de orden superior
desc: ''
updated: 1693163535071
created: 1680400899813
---

> "Tzu-li y Tzu-ssu estaban jactándose del tamaño de sus últimos programas. "Doscientas mil líneas", dijo Tzu-li, "¡sin contar los comentarios!" Tzu-ssu respondió, "Pssh, el mío tiene casi un **millón** de líneas ya." El Maestro Yuan-Ma dijo, "Mi mejor programa tiene quinientas líneas." Al escuchar esto, Tzu-li y Tzu-ssu fueron iluminados." - Master Yuan-Ma, The Book of Programming.

> "Hay dos formas de construir un diseño de software: una forma es hacerlo tan simple de manera que no haya deficiencias obvias, y la otra es hacerlo tan complicado de manera que obviamente no haya deficiencias." - C.A.R. Hoare, 1980 ACM Turing Award Lecture.

---

Tanto para el contenido del capítulo como los ejercicios necesitaremos el archivo [`SCRIPTS.js`](./assets/Personal/Eloquent%20JavaScript/5-%20SCRIPTS.js).

1. Introducción.

	Un programa grande es un programa costoso, y no solo por el tiempo que se necesita para construirlo. El tamaño casi siempre involucra complejidad, y la complejidad confunde a los programadores. A su vez, los programadores confundidos, introducen errores en los programas. Un programa grande entonces proporciona de mucho espacio para que estos bugs se oculten, haciéndolos difíciles de encontrar.

2. Abstracción.

	En el contexto de la programación, estos tipos de vocabularios (simples) suelen ser llamados **abstracciones**. Las abstracciones esconden detalles y nos dan la capacidad de hablar acerca de los problemas a un nivel superior (o más abstracto).

	En la programación, es una habilidad útil, darse cuenta cuando estás trabajando en un nivel de abstracción demasiado bajo.

3. Funciones de orden superior.

	Operan en otras funciones, ya sea tomándolas como argumentos o retornándolas. Como ya hemos visto que las funciones son valores regulares, no existe nada particularmente notable sobre el hecho de que tales funciones existen. El término proviene de las matemáticas, donde la distinción entre funciones y otros valores se toma más en serio.

	---

	Hay un método de array incorporado, `forEach` que proporciona algo como un ciclo "for/of" como una función de orden superior.

	```JS
	["A", "B"].forEach(letra => console.log(letra))
	// A
	// B
	```

4. Filtrando arrays.

	```JS
	function filtrar(array, prueba) {
		let pasaron = []
		for (let elemento of array) {
			if (prueba(elemento)) {
			pasaron.push(elemento)
			}
		}
		return pasaron
	}
	```

	Observa cómo la función `filtrar`, en lugar de eliminar elementos del array existente, crea un nuevo array solo con los elementos que pasan la prueba. Esta función es **pura**. No modifica el array que se le es dado.

5. Transformando con `map`.

	El método `map` ("mapear") transforma un array al aplicar una función a todos sus elementos y construir un nuevo array a partir de los valores retornados. El nuevo array tendrá la misma longitud que el array de entrada, pero su contenido ha sido **mapeado** a una nueva forma con base en la función.

	Al igual que `forEach` y `filter`, `map` es un método de array estándar.

6. Resumiendo con reduce.

	```JS
	function reduce(array, combinar, inicio) {
		let actual = inicio
		for (let elemento of array) {
			actual = combinar(actual, elemento)
		}
		return actual
	}

	console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0)) // 10
	```

	**reduce** construye un valor al repetidamente tomar un solo elemento del array y combinándolo con el valor actual. Al sumar números, comenzarías con el número cero y, para cada elemento, agregas eso a la suma.

	---

	El método de array estándar `reduce`, que por supuesto corresponde a esta función, tiene una mayor comodidad. Si tu array contiene al menos un elemento, tienes permitido omitir el argumento "inicio". El método tomará el primer elemento del array como su valor de inicio y comienza a reducir a partir del segundo elemento.

7. Composibilidad.

	Las funciones de orden superior comienzan a brillar cuando necesitas **componer** operaciones. Como ejemplo, vamos a escribir código que encuentre el año de origen promedio para los códigos vivos y muertos en el conjunto de datos.

	```JS
	function promedio(array) {
		return array.reduce((a, b) => a + b) / array.length
	}

	console.log(
		Math.round(
			promedio(
				SCRIPTS.filter(codigo => codigo.living).map(codigo => codigo.year)
			)
		)
	) // 1185
	console.log(
		Math.round(
			promedio(
				SCRIPTS.filter(codigo => !codigo.living).map(codigo => codigo.year)
			)
		)
	) // 209
	```

	```JS
	let total = 0, cuenta = 0
	for (let codigo of SCRIPTS) {
		if (codigo.living) {
			total += codigo.year
			cuenta += 1
		}
	}
	console.log(Math.round(total / cuenta)) // 1185
	```

	En términos de lo que la computadora realmente está haciendo, estos dos enfoques son bastante diferentes. El primero creará nuevos arrays al ejecutar `filter` y `map`, mientras que el segundo solo computa algunos números, haciendo menos trabajo. Por lo general, puedes permitirte el enfoque legible, pero si estás procesando arrays enormes, y haciéndolo muchas veces, el estilo menos abstracto podría ser mejor debido a la velocidad extra.

8. Strings y códigos de caracteres.

	Los strings de JavaScript están codificados como una secuencia de números de 16 bits. Estos se llaman **unidades de código**. Inicialmente, se suponía que un código de carácter Unicode encajara dentro de esa unidad (lo que da un poco más de 65,000 caracteres). Cuando quedó claro que esto no sería suficiente, muchas las personas se resistieron a la necesidad de usar más memoria por carácter. Para apaciguar estas preocupaciones, UTF-16, el formato utilizado por los strings de JavaScript, fue inventado. Este describe la mayoría de los caracteres más comunes usando una sola unidad de código de 16 bits, pero usa un par de dos de esas unidades para otros caracteres.

9. Resumen

	Ser capaz de pasar valores de función a otras funciones es un aspecto profundamente útil de JavaScript. Nos permite escribir funciones que modelen cálculos con "brechas" en ellas. El código que llama a estas funciones pueden llenar estas brechas al proporcionar valores de función.

## Recursos

1. Filtering arrays.

	To find the scripts in the data set that are still in use.

	```JS
	function filter(array, test) {
		let passed = []

		for (let element of array) {
			if (test(element)) {
				passed.push(element)
			}
		}
		return passed
	}

	// Test
	// console.log(filter(SCRIPTS, (script) => script.living))
	```

2. Transforming with map.

	```JS
	function map(array, transform) {
		let mapped = []

		for (let element of array) {
			mapped.push(transform(element))
		}
		return mapped
	}

	// Test
	// let rtlScripts = SCRIPTS.filter(s => s.direction == "rtl")
	// console.log(map(rtlScripts, s => s.name))
	```

3. Summarizing with reduce.

	```JS
	function reduce(array, combine, start) {
		let current = start

		for (let element of array) {
			current = combine(current, element)
		}
		return current
	}

	// Test
	// console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0))

	function characterCount(script) {
		return script.ranges.reduce((count, [from, to]) => {
			return count + (to - from)
		}, 0)
	}

	// Test
	// console.log(
	// 	SCRIPTS.reduce((a, b) => {
	// 			return characterCount(a) < characterCount(b) ? b : a
	// 		}
	// 	)
	// )
	```

4. Composability.

	```JS
	/* A way without higher-order functions
	let biggest = null
	for (let script of SCRIPTS) {
		if (biggest == null || characterCount(biggest) < characterCount(script)) biggest = script
	}
	console.log(biggest)
	*/

	function average(array) { return array.reduce((a, b) => a + b) / array.length }

	// Test
	// console.log(
	// 	Math.round(
	// 		average(SCRIPTS.filter(s => s.living).map(s => s.year))
	// 	)
	// )

	// console.log(
	// 	Math.round(
	// 		average(SCRIPTS.filter(s => !s.living).map(s => s.year))
	// 	)
	// )

	/* Another way
	let total = 0, count = 0
	for (let script of SCRIPTS) {
		if (script.living) {
			total += script.year
			count += 1
		}
	}
	console.log(Math.round(total / count))
	*/
	```

	So the dead scripts in Unicode are, on average, older than the living ones.

5. Strings and character codes.

	```JS
	function characterScript(code) {
		for (let script of SCRIPTS) {
			if (script.ranges.some(([from, to]) => {return code >= from && code < to})) {
				return script
			}
		}
		return null
	}

	// Test
	// console.log(characterScript(121))
	```

6. Recognizing text.

	```JS
	function countBy(items, groupName) {
		let counts = []

		for (let item of items) {
			let name = groupName(item)
			let known = counts.findIndex(c => c.name == name)

			if (known == -1) {
				counts.push({ name, count: 1 })
			} else {
				counts[known].count++
			}
		}
		return counts
	}

	// Test
	// console.log(countBy([1, 2, 3, 4, 5], n => n > 2))
	```

	```JS
	function textScripts(text) {
		let scripts = countBy(text, char => {
				let script = characterScript(char.codePointAt(0))
				return script ? script.name : "none"
			}
		).filter(({ name }) => name != "none")

		let total = scripts.reduce((n, { count }) => n + count, 0) // (count, char) => count + char.count
		if (total == 0) return "No scripts found"

		return scripts.map(({ name, count }) => { // char
			/*
			let name = char.name
			let count = char.count
			*/
			return `${Math.round(count * 100 / total)}% ${name}`
		}).join(", ")
	}

	// Test
	// console.log(textScripts('英国的狗说"woof", 俄罗斯的狗说"тяв"'))
	```

## Ejercicios

For this chapter, we required the "countBy" and "characterScript" functions.

1. Flattering.

	Use the reduce method in combination with the concat method to "flatten" an array of arrays into a single array that has all the elements of the original arrays.

	- Solution.

		```JS
		var arrays = [[1, 2, 3], [4, 5], [6]]

		console.log(arrays.reduce((flat, current) => flat.concat(current), []))
		```

2. Your own loop.

	Write a higher-order function called "loop" that provides something like a for loop statement. It takes a value, a test function, an update function, and a body function. Each iteration, it first runs the test function on the current loop value and stops if that returns false. Then it calls the body function, giving it the current value. Finally, it calls the update function to create a new value and starts from the beginning.

	- Solution.

		```JS
		function loop(start, test, update, body) {
			for (let value = start; test(value); update(value)) {
				body(value)
			}
		}

		// Test
		// loop(3, n => n > 0, n => n - 1, console.log)
		```

3. Everything.

	Write a function called "everything" that takes an array and a predicate function as parameters. Write two versions, one using a loop and one using the `some` method.

	- Solution.

		- Loop.

			```JS
			function loopEvery(array, predicate) {
				for (let element of array) {
					if (!predicate(element)) return false
				}
				return true
			}
			```

		- Using the `some` method.

			```JS
			function someEvery(array, predicate) {
				return !array.some(element => !predicate(element))
			}
			```

		- Tests.

			```JS
			console.log(every([1, 3, 5], n => n < 10))
			console.log(every([2, 4, 16], n => n < 10))
			console.log(every([], n => n < 10))
			```

4. Dominant writing direction.

	Write a function that computes the dominant writing direction in a string of text. The dominant direction is the direction of a majority of the characters that have a script associated with them.

	- Solution.

		```JS
			function dominantDirection(text) {
			let directions = countBy(text,
				char => {
						let script = characterScript(char.codePointAt(0))
						return script ? script.direction : "none"
					}
			).filter(({ direction }) => direction != "none")

			return directions.reduce(
				(a, b) => {
				return a.count > b.count ? a : b
				}
			).name
		}

		// Tests
		// console.log(dominantDirection("Hello!"))
		// console.log(dominantDirection("Hey, مساء الخير"))
		```
