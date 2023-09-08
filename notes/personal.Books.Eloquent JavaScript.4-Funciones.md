---
id: 6h4ozbc3g5et0pw2ecgwf1w
title: 4-Funciones
desc: ''
updated: 1693162109847
created: 1680398428336
---

> "La gente piensa que las ciencias de la computación son el arte de los genios, pero la verdadera realidad es lo opuesto, estas solo consisten en mucha gente haciendo cosas que se construyen una sobre la otra, al igual que un muro hecho de piedras pequeñas." - Donald Knuth.

---

1. Funciones.

	El concepto de envolver una pieza de programa en un valor tiene muchos usos. Esto nos da una forma de estructurar programas más grandes, de reducir la repetición, de asociar nombres con subprogramas y de aislar estos subprogramas unos con otros.

	Funciones que no tienen una declaración `return` en absoluto, o en él no incluyen nada, retornan `undefined`.

2. Vinculaciones y alcance.

	- Globales: accesibles desde cualquier parte del programa.

	- Locales: accesibles solo dentro de la función que las usa: ya sea como parámetros o como parte del código dentro de ella.

	---

	Cada vez que se llame a la función, se crean nuevas instancias de estas vinculaciones. Esto proporciona cierto aislamiento entre funciones-cada llamada de función actúa sobre su pequeño propio mundo (su entorno local), y a menudo puede ser entendida sin saber mucho acerca de lo que está pasando en el entorno global.

	En JavaScript anterior a 2015, solo las funciones creaban nuevos alcances, por lo que las vinculaciones de estilo antiguo, creadas con la palabra clave "var", son visibles a lo largo de toda la función en la que aparecen o en todo el alcance global, si no están dentro de una función.

	```JS
	let x = 10
	if (true) {
		let y = 20
		var z = 30
		console.log(x + y + z) // 60
	}
	// "y" no es visible desde aqui
	console.log(x + z) // 40
	```

	En resumen, cada alcance local puede ver también todos los alcances locales que lo contengan. El conjunto de vinculaciones visibles dentro de un bloque está determinado por el lugar de ese bloque en el texto del programa. Cada alcance local puede también ver todos los alcances locales que lo contengan, y todos los alcances pueden ver el alcance global. Este enfoque para la visibilidad de vinculaciones es llamado **alcance léxico**.

3. Notación de declaración.

	```JS
	console.log("El futuro dice:", futuro())

	function futuro() {
		return "Nunca tendran autos voladores"
	}
	```

	Este código funciona, aunque la función esté definida **debajo** del código que lo usa. Las declaraciones de funciones no son parte del flujo de control regular de arriba hacia abajo. Estas son conceptualmente trasladadas a la cima de su alcance y pueden ser utilizadas por todo el código en ese alcance. Esto es a veces útil porque nos da la libertad de ordenar el código en una forma que nos parezca significativa, sin preocuparnos por tener que definir todas las funciones antes de que sean utilizadas.

4. Funciones flecha.

	En lugar de la palabra clave "function", usa una flecha (`=>`) compuesta de los caracteres igual y mayor.

	```JS
	const potencia = (base, exponente) => {
		let resultado = 1
		for (let cuenta = 0 cuenta < exponente cuenta++) {
			resultado *= base
		}
		return resultado
	}

	const cuadrado1 = (x) => { return x * x }
	const cuadrado2 = x => x * x
	```

5. Pila de llamadas.

	El lugar donde la computadora almacena el contexto es la **pila de llamadas**. Cada vez que se llama a una función, el contexto actual es almacenado en la parte superior de esta "pila". Cuando una función retorna, elimina el contexto superior de la pila y lo usa para continuar la ejecución.

6. Argumentos opcionales.

	```JS
	function cuadrado(x) { return x * x }
	console.log(cuadrado(4, true, "erizo")) // 16
	```

	JavaScript es de extremadamente mente abierta sobre la cantidad de argumentos que puedes pasar a una función. Si pasa demasiados, los adicionales son ignorados. Si pasas muy pocos, a los parámetros faltantes se les asigna el valor `undefined`.

	---

	Si escribes el operador `=` después un parámetro, seguido de una expresión, el valor de esa expresión reemplazará al argumento cuando este no sea dado.

7. Cierre.

	Poder hacer referencia a una instancia específica de una vinculación local en un alcance encerrado se llama **cierre**.

	```JS
	function multiplicador(factor) {
		return numero => numero * factor
	}

	let duplicar = multiplicador(2)
	console.log(duplicar(5)) // 10
	```

8. Recursión.

	En JavaScript, correr a través de un ciclo simple es generalmente más barato en términos de memoria que llamar a una función múltiples veces.

	---

	El dilema de velocidad versus elegancia es interesante. Puedes verlo como una especie de compromiso entre accesibilidad humana y accesibilidad máquina. Casi cualquier programa se puede hacer más rápido haciéndolo más grande y complicado. El programador tiene que decidir acerca de cuál es un equilibrio apropiado.

	---

	La recursión no siempre es solo una alternativa ineficiente a los ciclos. Algunos problemas son realmente más fáciles de resolver con recursión que con ciclos. En la mayoría de los casos, estos son problemas que requieren explorar o procesar varias "ramas", cada una de las cuales podría ramificarse de nuevo en aún más ramas.

9. Funciones y efectos secundarios.

	Las funciones se pueden dividir aproximadamente en aquellas que se llaman por sus efectos secundarios y aquellas que son llamadas por su valor de retorno.

	> Aunque definitivamente también es posible tener tanto efectos secundarios como devolver un valor en una misma función.

	---

	Una función **pura** es un tipo específico de función de producción de valores que no solo no tiene efectos secundarios, pero que tampoco depende de los efectos secundarios de otro código, por ejemplo, no lee vinculaciones globales cuyos valores puedan cambiar. Una función pura tiene la propiedad agradable de que cuando se le llama con los mismos argumentos, siempre produce el mismo valor (y no hace nada más).

	Cuando no estás seguro de que una función pura esté funcionando correctamente, puedes probarla simplemente llamándola, y saber que si funciona en ese contexto, funcionará en cualquier contexto. Las funciones no puras tienden a requerir más configuración para poder ser probadas.

10. Resumen.

	Un aspecto clave en para comprender a las funciones es comprender los alcances. Cada bloque crea un nuevo alcance. Los parámetros y vinculaciones declaradas en un determinado alcance son locales y no son visibles desde el exterior. Vinculaciones declaradas con "var" se comportan de manera diferente, terminan en el alcance de la función más cercana o en el alcance global.

	Separar las tareas que realiza tu programa en diferentes funciones es útil. No tendrás que repetirte tanto, y las funciones pueden ayudar a organizar un programa agrupando el código en piezas que hagan cosas específicas.

## Recursos

- Recursion.

	By starting from the number 1 and repeatedly either adding 5 or multiplying by 3, an infinite set of numbers can be produced. How would you write a function that, given a number, tries to find a sequence of such additions and multiplications that produces that number?

	```JS
	function findSolution(target) {
		function find(current, history) {
			if (current == target) {
				return history
			} else if (current > target) {
				return null
			} else {
				return find(current + 5, `(${history} + 5)`) || find(current * 3, `(${history} * 3)`)
			}
		}
		return find(1, "1")
	}

	// Test
	// console.log(findSolution(24))
	```

	> Does not necessarily find the shortest path.

## Ejercicios

1. Minimum.

	Write a function "min" that takes two arguments and returns their minimum.

	- Solution.

		```JS
		function min(a, b) {
			if (a < b) console.log(a)
			else console.log(b)
		}

		// Tests
		// console.log(min(0, 10))
		// console.log(min(0, -10))
		```

2. Recursion.

	Define a recursive function "isEven" corresponding to this description. The function should accept a single parameter (a positive, whole number) and return a Boolean.

	- Help.

		- Zero is even.

		- One is odd.

		- For any other number N, its evenness is the same as N - 2.

		- "-N" and "N" have the same primality.

	- Solution.

		```JS
		function isEven(number) {
			if (number < 0) return isEven(-number)
			else if (number == 0) return true
			else if (number == 1) return false
			else return isEven(number - 2)
		}

		// Tests
		// console.log(isEven(50))
		// console.log(isEven(75))
		// console.log(isEven(-1))
		```

3. Bean counting.

	1. Write a function "countBs" that takes a string as its only argument and returns a number that indicates how many uppercase "B" characters there are in the string.

		- Solution.

			```JS
			function countBs(string) {
				let length = string.length
				let count = 0

				for (let i = 0; i < length; i++) {
					let char = string[i]

					if (char == "B") count += 1
				}
				return count
				//countChar(string, "B")
			}

			// Test
			// console.log(countBs("BBC"))
			```

	2. Write a function called "countChar" that behaves like countBs, except it takes a second argument that indicates the character that is to be counted (rather than counting only uppercase "B" characters).

		- Solution.

			```JS
			function countChar(string, char) {
				let count = 0

				for (let currentChar of string) {
					if (currentChar == char) count += 1
				}
				return count
			}

			// Test
			// console.log(countChar("kakkerlak", "k"))
			```
