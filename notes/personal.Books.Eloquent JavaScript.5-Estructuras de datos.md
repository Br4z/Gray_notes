---
id: lax77y3vrxbhr6a142qsiq8
title: 5-Estructuras de datos
desc: ''
updated: 1693163385456
created: 1680399332436
---

> "En dos ocasiones me han preguntado, "Dinos, Sr. Babbage, si pones montos equivocados en la máquina, saldrán las respuestas correctas? \[...\] No soy capaz de comprender correctamente el tipo de confusión de ideas que podrían provocar tal pregunta." - Charles Babbage, Passages from the Life of a Philosopher (1864).

---

Tanto para el contenido del capítulo como los ejercicios necesitaremos el archivo (las entradas del diario) [`JOURNAL.js`](./assets/Personal/Eloquent%20JavaScript/5-%20JOURNAL.js).

1. Introducción.

	Los números, los booleanos y los strings son los átomos que constituyen las estructuras de datos. Sin embargo, muchos tipos de información requieren más de un átomo. Los **objetos** nos permiten agrupar valores -incluidos otros objetos- para construir estructuras más complejas.

2. Propiedades.

	Las dos formas principales de acceder a las propiedades en JavaScript son con un punto y con corchetes. Tanto `valor.x` como `valor[x]` acceden una propiedad en `valor`, pero no necesariamente la misma propiedad. La diferencia está en cómo se interpreta `x`. Cuando se usa un punto, la palabra después del punto es el nombre literal de la propiedad. Cuando usas corchetes, la expresión entre corchetes es **evaluada** para obtener el nombre de la propiedad. Mientras `valor.x` obtiene la propiedad de `valor` llamada "x", `valor[x]` intenta evaluar la expresión `x` y usa el resultado, convertido en un string, como el nombre de la propiedad.

3. Métodos.

	Las propiedades que contienen funciones generalmente son llamadas **métodos** del valor al que pertenecen.

	> Un ejemplo es "toUpperCase" (método de string).

4. Objetos.

	Leer una propiedad que no existe te dará el valor `undefined`.

	---

	Es posible asignarle un valor a una expresión de propiedad con el operador `=`. Esto reemplazará el valor de la propiedad si ya tenía uno o crea una nueva propiedad en el objeto si no fuera así.

	---

	El operador `delete` ("eliminar") es un operador unario que, cuando se aplica a la propiedad de un objeto, eliminará la propiedad nombrada de dicho objeto.

	```JS
	let unObjeto = { izquierda: 1, derecha: 2 }
	console.log(unObjeto.izquierda) // 1
	delete unObjeto.izquierda
	console.log(unObjeto.izquierda) // undefined
	console.log("izquierda" in unObjeto) // false
	console.log("derecha" in unObjeto) // true
	```

	---

	Para saber qué propiedades tiene un objeto, puedes usar la función `Object.keys`. Le das un objeto y devuelve un array de strings (los nombres de las propiedades del objeto).

	```JS
	console.log(Object.keys({ x: 0, y: 0, z: 2 })) // ["x", "y", "z"]
	```

	---

	La funcion `Object.assign` copia todas las propiedades de un objeto a otro.

	```JS
	let objetoA = { a: 1, b: 2 }
	Object.assign(objetoA, { b: 3, c: 4 })
	console.log(objetoA) // { a: 1, b: 3, c: 4 }
	```

	---

	Los arrays son, entonces, solo un tipo de objeto especializado para almacenar secuencias de cosas. Si evalúas `typeof([])`, este produce `object`.

5. Mutabilidad.

	Vimos que los valores de objeto pueden ser modificados. Los tipos de valores discutidos en capítulos anteriores, como números, strings y booleanos, son todos **inmutables**, es imposible cambiar los valores de aquellos tipos. Puedes combinarlos y obtener nuevos valores a partir de ellos, pero cuando tomas un valor de string específico, ese valor siempre será el mismo. El texto dentro de él no puede ser cambiado. Si tienes un string que contiene `"gato"`, no es posible que otro código cambie un carácter en tu string para que deletree "rato".

6. El diario del licántropo.

	```JS
	let diario = []

	function añadirEntrada(eventos, ardilla) {
		diario.push({ eventos, ardilla })
	}
	```

	Ten en cuenta que el objeto agregado al diario se ve un poco extraño. En lugar de declarar propiedades como `eventos: eventos`, simplemente da un nombre de propiedad. Este es un atajo que representa lo mismo si el nombre de propiedad en la notación de llaves no es seguido por un valor, el valor se toma de la vinculación con el mismo nombre.

	---

	La **correlación** es una medida de dependencia entre variables estadísticas. Una variable estadística no es lo mismo que una variable de programación. En las estadísticas, normalmente tienes un conjunto de **medidas**, y cada variable se mide para cada medida. La correlación entre variables generalmente se expresa como un valor que varía de -1 a 1. Una correlación de cero significa que las variables no están relacionadas. Una correlación de uno índica que las dos están perfectamente relacionadas -si conoces una, también conoces la otra. Uno negativo también significa que las variables están perfectamente relacionadas, pero que son opuestas- cuando una es verdadera, la otra es falsa.

	Para calcular la medida de correlación entre dos variables booleanas, podemos usar el **coeficiente phi** ($\phi$). Esta es una fórmula cuya entrada es una tabla de frecuencias que contiene la cantidad de veces que las diferentes combinaciones de las variables fueron observadas. El resultado de la fórmula es un número entre -1 y 1 que describe la correlación.

	$$
	\phi = \frac{ n_{ 11 } n_{ 00 } - n_{ 10 } n_{ 01 } }{ \sqrt{ n_{ 1\cdot } n_{ 0\cdot } n_{ \cdot 1 } n_{ \cdot 0 } } }
	$$

7. Ciclos de array.

	```JS
	for (let entrada of DIARIO) {
		console.log(`${entrada.eventos.length} eventos.`)
	}
	```

	Cuando un ciclo `for` se vea de esta manera, con la palabra "of" ("de") después de una definición de variable, recorrerá los elementos del valor dado después `of`. Esto funciona no solo para arrays, sino también para strings y algunas otras estructuras de datos.

8. Parámetros restantes.

	```JS
	function maximo(...numeros) {
		let resultado = -Infinity
		for (let numero of numeros) {
			if (numero > resultado) resultado = numero
		}
		return resultado
	}

	console.log(maximo(4, 1, 9, -2)) // 9
	```

	---

	```JS
	let palabras = ["nunca", "entenderas"]

	console.log(["tu", ...palabras, "completamente"]) // ["tu", "nunca", "entenderas", "completamente"]
	```

9. Objeto `Math`.

	Es usado como un contenedor que agrupa un grupo de funcionalidades relacionadas. Solo hay un objeto `Math`, y casi nunca es útil como un valor. Más bien, proporciona un **espacio de nombre** para que todas estas funciones y valores no tengan que ser vinculaciones globales.

	Tener demasiadas vinculaciones globales "contamina" el espacio de nombres. Cuanto más nombres hayan sido tomados, es más probable que accidentalmente sobrescribas el valor de algunas vinculaciones existentes. Por ejemplo, no es poco probable que quieras nombrar algo "max" en alguno de tus programas. Dado que la función `max` ya incorporada en JavaScript está escondida dentro del Objeto `Math`, no tenemos que preocuparnos por sobrescribirla.

	---

	Aunque las computadoras son máquinas deterministas -siempre reaccionan de la misma manera dada la misma entrada- es posible hacer que produzcan números que parecen aleatorios. Para hacer eso, la máquina mantiene algún valor escondido, y cada vez que le pidas un nuevo número aleatorio, realiza cálculos complicados en este valor oculto para crear un nuevo valor. Esta almacena un nuevo valor y retorna un número derivado de él. De esta manera, puede producir números nuevos y difíciles de predecir de una manera que **parece** aleatoria.

10. JSON.

	JavaScript nos da las funciones `JSON.stringify` y `JSON.parse` para convertir datos hacia y desde este formato. El primero toma un valor en JavaScript y retorna un string codificado en JSON. La segunda toma un string como ese y lo convierte al valor que este codifica.

	```JS
	let string = JSON.stringify(
		{ ardilla: false, eventos: ["fin de semana"] }
	)

	console.log(string) // { "ardilla": false, "eventos": ["fin de semana"] }
	console.log(JSON.parse(string).eventos) // ["fin de semana"]
	```

11. Resumen.

	Los objetos y arrays (que son un tipo específico de objeto) proporcionan formas de agrupar varios valores en un solo valor. Conceptualmente, esto nos permite poner un montón de cosas relacionadas en un bolso y correr alrededor con el bolso, en lugar de envolver nuestros brazos alrededor de todas las cosas individuales, tratando de aferrarnos a ellas por separado.

## Recursos

1. Computing a correlation.

	```JS
	function phi(table) { // [n_00, n_01, n_10, n_11]
		return (table[3] * table[0] - table[2] * table[1]) /
		Math.sqrt((table[2] + table[3]) *
					(table[0] + table[1]) *
					(table[1] + table[3]) *
					(table[0] + table[2]))
	}

	/* More visual way
	function phi([n00, n01, n10, n11]) {
		return (n11 * n00 - n10 * n01) /
			Math.sqrt((n10 + n11) *
					(n00 + n01) *
					(n01 + n11) *
					(n00 + n10))
	}
	*/

	// Test
	// console.log(phi([76, 9, 4, 1]))
	```

	For creating the table for an event, we set the following data structure `[n_00, n_01, n_10, n_11]`:

	- The first number represents the squirrel.

	- The second number represents the event.

	```JS
	function tablefor(event, journal) {
		let table = [0, 0, 0, 0]

		for (let i = 0; i < journal.length; i++) {
			let entry = journal[i], index = 0

			if (entry.events.includes(event)) index += 1
			if (entry.squirrel) index += 2
			table[index] += 1
		}
		return table
	}

	// Test
	// console.log(tablefor ("pizza", JOURNAL))
	```

2. The final analysis.

	```JS
	function journalEvents(journal) {
		let events = []

		for (let entry of journal) {
			for (let event of entry.events) {
				if (!events.includes(event)) {
					events.push(event)
				}
			}
		}
		return events
	}

	// Test
	// console.log(journalEvents(JOURNAL))
	```

	To see the mos relevant ones, we can use the following code:

	```JS
	for (let event of journalEvents(JOURNAL)) {
		let correlation = phi(tablefor (event, JOURNAL))

		if (correlation > 0.1 || correlation < -0.1) {
			console.log(event + ":", correlation)
		}
	}
	```

	After realizing that the events `peanuts` and `teeth brushing` have the highest values ​​(positive and negative correlation respectively), we can set a new event called "peanut teeth".

	```JS
	for (let entry of JOURNAL) {
		if (entry.events.includes("peanuts") && !entry.events.includes("brushed teeth")) {
			entry.events.push("peanut teeth")
		}
	}
	```

	Once we create a table for it (`phi(tablefor("peanut teeth", JOURNAL))`), the result (1) means that it is completely related and also the cause of his problem.

## Ejercicios

1. The sum of a range.

	1. Write a function called "range" function that takes two arguments, start and end, and returns an array containing all the numbers from start up to (and including) end.

		> As a bonus assignment, modify your range function to take an optional third argument that indicates the "step" value used when building the array. If no step is given, the elements go up by increments of one.

		- Solution.

			```JS
			function range(start, end, step = 1) {
				let array = []

				if (step < 0) for (let i = start; i >= end; i += step) array.push(i)
				else for (let i = start; i <= end; i += step) array.push(i)

				return array
			}

			// Tests
			// console.log(range(1, 10))
			// console.log(range(5, 2, -1))
			```

	2. Write a function called "sum" function that takes an array of numbers and returns the sum of these numbers.

		- Solution.

			```JS
			function sum(array) {
				let sum = 0

				for (let number of array) sum += number

				return sum
			}

			// Test
			// console.log(sum(range(1, 10)))
			```

2. Reversing an array.

	1. Write the function reverseArray, takes an array as an argument and produces a new array that has the same elements in the inverse order.

		- Solution.

			```JS
			function reverseArray(array) {
				let reversedArray = []

				for (let i = array.length - 1; i >= 0; i--) reversedArray.push(array[i])

				return reversedArray
			}

			// Test
			// console.log(reverseArray(["A", "B", "C"]))
			```

	2. Write the function reverseArrayInPlace, does what the reverse method does: it modifies the array given as an argument by reversing its elements.

		- Solution.

			```JS
			function reverseArrayInPlace(array) {
				let length = array.length

				for (let i = 0; i < Math.floor(length / 2); i++) {
					// We use Math.floor approximation, because the middle element (if it has) always results in the same position
					// it occurs when the array has an odd number of elements
					const old = array[i]

					array[i] = array[(length - 1) - i]
					array[(length - 1) - i] = old
				}

				return array
			}

			// Test
			// let arrayValue = [1, 2, 3, 4, 5]
			// reverseArrayInPlace(arrayValue)
			// console.log(arrayValue)
			```

3. A list.

	1. Write the function "arrayToList" that builds up a list structure like the one shown.

		![Linked list](./assets/Personal/Eloquent%20JavaScript/5-1%20Linked-list.svg)

		- Solution.

			```JS
			function arrayToList(array) {
				/*
				let list = null

				for (let i = array.length - 1; i >= 0; i--) {
					list = { value: array[i], rest: list }
				}
				return list
				*/

				if (array.length == 0) return null
				else list = { value : array.shift(), rest : arrayToList(array) }

				return list
			}

			// Test
			// console.log(arrayToList([]))
			```

	2. Write the function "listToArray" function that produces an array from a list.

		- Solution.

			```JS
			function listToArray(list, array = []) {
				/*
				let array = []

				for (let node = list; node; node = node.rest) array.push(node.value)

				return array
				*/

				if (list) {
					array.push(list.value)
					listToArray(list.rest, array)
				}
				return array
			}

			// Test
			// console.log(listToArray(arrayToList([10, 20, 30])))
			```

	3. Write a helper function "prepend", which takes an element and a list and creates a new list that adds the element to the front of the input list.

		- Solution.

			```JS
			function prepend(value, rest) { // value = element, rest = list
				return { value, rest }
			}
			```

	4. Write the function "nth", which takes a list and a number and returns the element at the given position in the list (with zero referring to the first element) or undefined when there is no such element.

		- Solution.

			```JS
			function nth(list, index) {
				if (!list) return undefined
				else if (index == 0) return list.value
				else return nth(list.rest, index - 1)
			}

			// Test
			// console.log(nth(arrayToList([10, 20, 30]), 1))
			```

4. Deep comparison.

	Write the function "deepEqual" that takes two values and returns true only if they are the same value or are objects with the same properties, where the values of the properties are equal when compared with a recursive call to deepEqual.

	- Solution.

		```JS
		function deepEqual(a, b) {
			if (a === b) return true
			else if (a == null || typeof a != "object" ||
			b == null || typeof b != "object") return false // null is an object
			else {
				let keysA = Object.keys(a), keysB = Object.keys(b)

				if (keysA.length != keysB.length) return false

				for (let key of keysA) {
					if (!keysB.includes(key) || !deepEqual(a[key], b[key])) return false // If none of the calls return true, that means that
					// the objects are the same
				}
				return true
			}
		}

		// Test
		// let obj = { here: { is: "an" }, object: 2 }
		// console.log(deepEqual(obj, obj))
		// console.log(deepEqual(obj, { here : 1, object : 2 }))
		// console.log(deepEqual(obj, { here : { is: "an" }, object : 2 }))
		```
