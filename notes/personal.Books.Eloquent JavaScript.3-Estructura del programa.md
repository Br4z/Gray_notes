---
id: l46n25x3imv01amxh8com6i
title: 3-Estructura del programa
desc: ''
updated: 1693161785974
created: 1680398135817
---

> "Y mi corazón brilla de un color rojo brillante bajo mi piel transparente y translúcida, y tienen que administrarme 10cc de JavaScript para conseguir que regrese. (respondo bien a las toxinas en la sangre.) Hombre, esa cosa es ¡increíble!" - _why, Why's (Poignant) Guide to Ruby.

---

1. Expresiones y declaraciones.

	En algunos casos, JavaScript te permite omitir el punto y coma al final de una declaración. En otros casos, tiene que estar allí, o la próxima línea serán tratadas como parte de la misma declaración. Las reglas para saber cuando se puede omitir con seguridad son algo complejas y propensas a errores.

2. Vinculaciones.

	Las palabras "var" y "const" también pueden ser usadas para crear vinculaciones, en una manera similar a "let".

	La primera, "var" (abreviatura de "variable"), es la forma en la que se declaraban las vinculaciones en JavaScript previo al 2015. Por ahora, recuerda que generalmente hace lo mismo, pero raramente la usaremos porque tiene algunas propiedades confusas.

3. Entorno.

	La colección de vinculaciones y sus valores que existen en un momento dado se llama **entorno**. Cuando se inicia un programa, este entorno no está vacío. Siempre contiene vinculaciones que son parte del estándar del lenguaje, y la mayoría de las veces, también tiene vinculaciones que proporcionan formas de interactuar con el sistema circundante.

4. Funciones.

	Una función es una pieza de programa envuelta en un valor. Dichos valores pueden ser **aplicados** para ejecutar el programa envuelto.

5. Función `console.log`.

	Aunque los nombres de las vinculaciones no puedan contener caracteres de puntos, `console.log` tiene uno. Esto es porque `console.log` no es una vinculación simple. En realidad, es una expresión que obtiene la propiedad `log` del valor mantenido por la vinculación `console`.

6. Indentación

	Podrías escribir un programa en una sola línea inmensa si así quisieras.

	---

	El rol de la indentación dentro de los bloques es hacer que la estructura del código se destaque. En código donde se abren nuevos bloques dentro de otros bloques, puede ser difícil ver dónde termina un bloque y donde comienza el otro. Con la indentación apropiada, la forma visual de un programa corresponde a la forma de los bloques dentro de él.

## Ejercicios

1. Looping a triangle.

	Given an input number, you must build a "stairs" that high.

	- Example.

		```
		#
		##
		###
		####
		#####
		######
		#######
		```

	- Solution.

		```JS
		height = 8

		for (let i = ""; i.length < height; i += "#") console.log(i)
		```

2. FizzBuzz.

	Write a program that uses `console.log` to print all the numbers from 1 to 100, with two exceptions. For numbers divisible by 3, print "Fizz" instead of the number, and for numbers divisible by 5 (and not 3), print "Buzz" instead. When you have that working, modify your program to print "FizzBuzz" for numbers that are divisible by both 3 and 5 (and still print "Fizz" or "Buzz" for numbers divisible by only one of those).

	- Solution.

		```JS
		for (let i = 1; i <= 100; i++) {
			let output = ""

			if (i % 3 == 0) output += "Fizz"
			if (i % 5 == 0) output += "Buzz"

			console.log(output || i)
		}
		```

3. Chessboard.

	Write a program that creates a string that represents a 8x8 grid, using newline characters to separate lines. At each position of the grid, there is either a space or a `#` character. The characters should form a chessboard.

	- Example.

		```
		# # # #
		# # # #
		# # # #
		# # # #
		# # # #
		# # # #
		# # # #
		# # # #
		```

	- Solution.

		```JS
		var size = 8
		var chessboard = ""

		for (let i = 0; i < size; i++) {
			for (let j = 0; j < size; j++) {
				if ((i + j) % 2 != 0) chessboard += "#" // odd positions
				else chessboard += " "
			}
			chessboard += "\n"
		}

		console.log(chessboard)
		```
