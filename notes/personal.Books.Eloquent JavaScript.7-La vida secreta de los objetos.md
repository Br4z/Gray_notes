---
id: s3i87q8unlthnvy19hy1wkt
title: 7-La vida secreta de los objetos
desc: ''
updated: 1693164312213
created: 1680401607368
---

> "Un tipo de datos abstracto se realiza al escribir un tipo especial de programa [...] que define el tipo con base en las operaciones que puedan ser realizadas en él." - Barbara Liskov, Programming with Abstract Data Types.

---

1. Encapsulación.

	La idea central en la programación orientada a objetos es dividir a los programas en piezas más pequeñas y hacer que cada pieza sea responsable de gestionar su propio estado.

	De esta forma, los conocimientos acerca de como funciona una parte del programa pueden mantenerse **locales** a esa pieza. Alguien trabajando en otra parte del programa no tiene que recordar o ni siquiera tener una idea de ese conocimiento.

	Las diferentes piezas de un programa, como tal, interactúan entre sí a través de **interfaces**, las cuales son conjuntos limitados de funciones y vinculaciones que proporcionan funcionalidades útiles en un nivel más abstracto, ocultando así su implementación interna.

	Tales piezas del programa se modelan usando objetos. Sus interfaces consisten en un conjunto específico de métodos y propiedades. Las propiedades que son parte de la interfaz se llaman **públicas**. Las otras, las cuales no deberían ser tocadas por el código externo, se les llama **privadas**.

2. Métodos.

	```JS
	function hablar(linea) {
		console.log(`El conejo ${this.tipo} dice '${linea}'`)
	}
	let conejoBlanco = { tipo: "blanco", hablar }
	let conejoHambriento = { tipo: "hambriento", hablar }

	conejoBlanco.hablar("Oh mis orejas y bigotes, " +
						"que tarde se esta haciendo!") // El conejo blanco dice "Oh mis orejas y bigotes, que tarde se esta haciendo!"
	conejoHambriento.hablar("Podría comerme una zanahoria ahora mismo.") // El conejo hambriento dice "Podría comerme una zanahoria ahora mismo."

	// call toma el valor de this como primer argumento y trata a los
	// argumentos adicionales como parámetros normales
	hablar.call(conejoHambriento, "Burp!") // El conejo hambriento dice 'Burp!'
	```

	Como cada función tiene su propia vinculación `this`, cuyo valor depende de la forma en como esta se llama, no puedes hacer referencia al `this` del alcance envolvente en una función regular definida con la palabra clave "function".

	Las funciones de flecha son diferentes, no crean su propia vinculación `this`, pero pueden ver la vinculación `this` del alcance a su alrededor. Por lo tanto, puedes hacer algo como el siguiente código, que hace referencia a `this` desde adentro de una función local:

	```JS
	function normalizar() {
		console.log(this.coords.map(n => n / this.length))
	}

	normalizar.call({ coords: [0, 2, 3], length: 5 }) // [0, 0.4, 0.6]
	// Usando la palabra "function" en map el código no funcionaría
	```

3. Prototipos.

	En adición a su conjunto de propiedades, la mayoría de los objetos también tienen un **prototipo**. Un prototipo es otro objeto que se utiliza como una reserva de propiedades alternativa. Cuando un objeto recibe una solicitud por una propiedad que este no tiene, se buscará en su prototipo la propiedad, luego en el prototipo del prototipo y así sucesivamente.

	---

	Las relaciones prototipo de los objetos en JavaScript forman una estructura en forma de árbol, y en la raíz de esta estructura se encuentra `Object.prototype`. Este proporciona algunos métodos que pueden ser accedidos por todos los objetos, como `toString`, que convierte un objeto en una representación de tipo string.

	Ejemplo:

	```JS
	let conejoPrototipo = {
		hablar(linea) {
			console.log(`El conejo ${this.tipo} dice '${linea}'`)
		}
	}
	let conejoAsesino = Object.create(conejoPrototipo)
	conejoAsesino.tipo = "asesino"
	conejoAsesino.hablar("SKREEEE!") // El conejo asesino dice 'SKREEEE!'
	```

	El conejo "prototipo" actúa como un contenedor para las propiedades que son compartidas por todos los conejos. Un objeto de conejo individual, como el conejo asesino, contiene propiedades que aplican solo a sí mismo -en este caso su tipo- y deriva propiedades compartidas desde su prototipo.

4. Clases.

	El sistema de prototipos en JavaScript se puede interpretar como un enfoque informal de un concepto orientado a objetos llamado **clases**. Una clase define la forma de un tipo de objeto, qué métodos y propiedades tiene este. Tal objeto es llamado una **instancia** de la clase.

	JavaScript proporciona una manera de hacer que la definición de este tipo de funciones sea más fácil. Si colocas la palabra clave "new" ("nuevo") delante de una llamada de función, la función será tratada como un constructor. Esto significa que un objeto con el prototipo adecuado es creado automáticamente, vinculado a `this` en la función, y retornado al final de la función.

	---

	Los constructores (todas las funciones, de hecho) automáticamente obtienen una propiedad llamada "prototype", que por defecto contiene un objeto simple y vacío, que deriva de `Object.prototype`. Puedes sobrescribirlo con un nuevo objeto si así quieres. O puedes agregar propiedades al objeto ya existente.

	---

	Por convención, los nombres de los constructores tienen la primera letra en mayúscula para que se puedan distinguir fácilmente de otras funciones.

	---

	```JS
	function Conejo(tipo) {
		this.tipo = tipo
	}
	Conejo.prototype.hablar = function(linea) {
		console.log(`El conejo ${this.tipo} dice '${linea}'`)
	}

	let conejoRaro = new Conejo("raro")

	console.log(Object.getPrototypeOf(Conejo) == Function.prototype) // true
	console.log(Object.getPrototypeOf(conejoRaro) == Conejo.prototype) // true
	```

5. Notación clase.

	```JS
	class Conejo {
		constructor(tipo) {
			this.tipo = tipo
		}

		hablar(linea) {
			console.log(`El conejo ${this.tipo} dice '${linea}'`)
		}
	}

	let conejoAsesino = new Conejo("asesino")
	let conejoNegro = new Conejo("negro")
	```

	La palabra clave "class" ("clase") comienza una declaración de clase, que nos permite definir un constructor y un conjunto de métodos, todo en un solo lugar. Cualquier número de métodos se pueden escribir dentro de las llaves de la declaración. El método llamado "constructor" es tratado de una manera especial. Este proporciona la función constructora real, que estará vinculada al nombre "Conejo". Los otros métodos estarán empacados en el prototipo de ese constructor. Por lo tanto, la declaración de clase anterior es equivalente a la definición de constructor en la sección anterior. Solo que se ve mejor.

	---

	Actualmente, las declaraciones de clase solo permiten que los **métodos** propiedades que contengan funciones puedan ser agregados al prototipo. Esto puede ser algo inconveniente para cuando quieras guardar un valor no funcional allí.

	---

	```JS
	let objeto = new class { obtenerPalabra() { return "hola" } }

	console.log(objeto.obtenerPalabra()) // hola
	```

6. Sobreescribiendo propiedades derivadas.

	```JS
	Rabbit.prototype.dientes = "pequeños"
	console.log(conejoAsesino.dientes) // pequeños
	conejoAsesino.dientes = "largos, filosos, y sangrientos"
	console.log(conejoAsesino.dientes) // largos, filosos, y sangrientos
	console.log(conejoNegro.dientes) // pequeños
	console.log(Rabbit.prototype.dientes) // pequeños
	```

	![Rabbit](assets/Personal/Eloquent%20JavaScript/7-%20Rabbits.svg)

	También puedes sobreescribir para darle a los prototipos estándar de función y array un método diferente `toString` al del objeto prototipo básico.

	```JS
	console.log(Array.prototype.toString == Object.prototype.toString) // false
	console.log([1, 2].toString()) // 1, 2
	console.log(Object.prototype.toString.call([1, 2])) // [object Array]
	```

7. Mapa

	Un **mapa** (sustantivo) es una estructura de datos que asocia valores (las llaves) con otros valores. Por ejemplo, es posible que desees mapear nombres a edades. Es posible usar objetos para esto.

	```JS
	let edades = {
		Boris: 39,
		Liang: 22,
		Júlia: 62
	}

	console.log(`Júlia tiene ${edades["Júlia"]}`) // Júlia tiene 62
	console.log("¿Se conoce la edad de Jack?", "Jack" in edades) // ¿Se conoce la edad de Jack? false
	console.log("¿Se conoce la edad de toString?", "toString" in edades) // ¿Se conoce la edad de toString? true
	```

	---

	Como tal, usar objetos simples como mapas es peligroso. Hay varias formas posibles de evitar este problema. Primero, es posible crear objetos sin **ningún** prototipo. Si pasas `null` a `Object.create`, el objeto resultante no se derivará de `Object.prototype` y podrá ser usado de forma segura como un mapa.

	```JS
	console.log("toString" in Object.create(null)) // false

	let edades = new Map()
	edades.set("Boris", 39)
	edades.set("Liang", 22)
	edades.set("Júlia", 62)

	console.log(`Júlia tiene ${edades.get("Júlia")}`) // Júlia tiene 62
	console.log("Se conoce la edad de Jack?", edades.has("Jack")) // Se conoce la edad de Jack? false
	console.log(edades.has("toString")) // false
	```

	Si tienes un objeto simple que necesitas tratar como un mapa por alguna razón, es útil saber que `Object.keys` solo retorna las llaves propias del objeto, no las que están en el prototipo. Como alternativa al operador `in`, puedes usar el método `hasOwnProperty` ("tienePropiaPropiedad"), el cual ignora el prototipo del objeto.

	---

	```JS
	console.log({ x: 1 }.hasOwnProperty("x")) // true
	console.log({ x: 1 }.hasOwnProperty("toString")) // false
	```

8. Polimorfismo

	El código polimórfico puede funcionar con valores de diferentes formas, siempre y cuando soporten la interfaz que este espera.

9. Símbolos

	Los símbolos son valores creados con la función `Symbol`. A diferencia de los strings, los símbolos recién creados son únicos, no puedes crear el mismo símbolo dos veces.

	```JS
	let simbolo = Symbol("nombre")
	console.log(simbolo == Symbol("nombre")) // false
	Conejo.prototype[simbolo] = 55
	console.log(conejoNegro[simbolo]) // 55
	```

	El string que pases a `Symbol` es incluido cuando lo conviertas a string, y puede hacer que sea más fácil reconocer un símbolo cuando, por ejemplo, lo muestres en la consola. Pero no tiene sentido más allá de eso, múltiples símbolos pueden tener el mismo nombre.

	Al ser únicos y utilizables como nombres de propiedad, los símbolos son adecuados para definir interfaces que pueden vivir pacíficamente junto a otras propiedades, sin importar cuáles sean sus nombres.

	---

	```JS
	const simboloToString = Symbol("toString")
	Array.prototype[simboloToString] = function() {
		return `${this.length} cm de hilo azul`
	}

	console.log([1, 2].toString()) // 1,2
	console.log([1, 2][simboloToString]()) // 2 cm de hilo azul

	let objetoString = {
		[simboloToString]() { return "una cuerda de cañamo" }
	}
	console.log(objetoString[simboloToString]()) // una cuerda de cañamo
	```

10. La interfaz de iterador

	```JS
	let iteradorOK = "OK"[Symbol.iterator]()
	console.log(iteradorOK.next()) // {value: "O", done: false}
	console.log(iteradorOK.next()) // {value: "K", done: false}
	console.log(iteradorOK.next()) // {value: undefined, done: true}
	```

11. Getters, setters y estáticos

	A menudo, las interfaces consisten principalmente de métodos, pero también está bien incluir propiedades que contengan valores que no sean de función. Por ejemplo, los objetos `Map` tienen una propiedad `size` ("tamaño") que te dice cuántas claves hay almacenadas en ellos.

	Ni siquiera es necesario que dicho objeto calcule y almacene tales propiedades directamente en la instancia. Incluso las propiedades que pueden ser accedidas directamente pueden ocultar una llamada a un método. Tales métodos se llaman **getters**, y se definen escribiendo "get" ("obtener") delante del nombre del método en una expresión de objeto o declaración de clase.

12. Herencia

	El sistema de prototipos en JavaScript hace posible crear una **nueva** clase, parecida a la clase anterior, pero con nuevas definiciones para algunas de sus propiedades.

	---

	La herencia nos permite construir tipos de datos ligeramente diferentes a partir de tipos de datos existentes con relativamente poco trabajo. Es una parte fundamental de la tradición orientada a objetos, junto con la encapsulación y el polimorfismo. Pero mientras que los últimos dos son considerados como ideas maravillosas en la actualidad, la herencia es más controversial.

	Mientras que la encapsulación y el polimorfismo se pueden usar para **separar** piezas de código entre sí, reduciendo el enredo del programa en general, la herencia fundamentalmente vincula las clases, creando **más** enredo. Al heredar de una clase, generalmente tienes que saber más sobre cómo funciona que cuando simplemente la usas. La herencia puede ser una herramienta útil, pero no debería ser la primera herramienta que busques, y probablemente no deberías estar buscando oportunidades para construir jerarquías (árboles genealógicos de clases) de clases de una manera activa.

13. Resumen

	Entonces los objetos hacen más que solo tener sus propias propiedades. Ellos tienen prototipos, que son otros objetos. Estos actuarán como si tuvieran propiedades que no tienen mientras su prototipo tenga esa propiedad. Los objetos simples tienen `Object.prototype` como su prototipo.

	Los constructores, que son funciones cuyos nombres generalmente comienzan con una mayúscula, se pueden usar con el operador `new` para crear nuevos objetos. El prototipo del nuevo objeto será el objeto encontrado en la propiedad `prototype` del constructor. Puedes hacer un buen uso de esto al poner las propiedades que todos los valores de un tipo dado comparten en su prototipo. Hay una notación "class" que proporciona una manera clara de definir un constructor y su prototipo.

	Puedes definir getters y setters para secretamente llamar a métodos cada vez que se acceda a la propiedad de un objeto. Los métodos estáticos son métodos almacenados en el constructor de clase, en lugar de su prototipo.

	El operador `instanceof` puede, dado un objeto y un constructor, decir si ese objeto es una instancia de ese constructor.

	Una cosa útil que hacer con los objetos es especificar una interfaz para ellos y decirle a todos que se supone que deben hablar con ese objeto solo a través de esa interfaz. El resto de los detalles que componen tu objeto ahora están **encapsulados**, escondidos detrás de la interfaz.

	Más de un tipo puede implementar la misma interfaz. El código escrito para utilizar una interfaz automáticamente sabe cómo trabajar con cualquier cantidad de objetos diferentes que proporcionen la interfaz. Esto se llama **polimorfismo**.

	Al implementar múltiples clases que difieran solo en algunos detalles, puede ser útil escribir las nuevas clases como **subclases** de una clase existente, **heredando** parte de su comportamiento.

## Recursos

1. The iterator interface.

	```JS
	class Matrix {
		constructor(width, height, element = (x, y) => undefined) {
			this.width = width
			this.height = height
			this.content = []

			// Array to matrix conversion
			for (let y = 0; y < height; y++) {
				for (let x = 0; x < width; x++) {
					this.content[y * width + x] = element(x, y)
				}
			}
		}

		get(x, y) {
			return this.content[y * this.width + x]
		}

		set(x, y, value) {
			this.content[y * this.width + x] = value
		}

		static show(matrix) {
			const width = matrix.width
			const height = matrix.height

			for (let y = 0; y < height; y++) {
				let row = ""

				for (let x = 0; x < width; x++) row += matrix.get(x, y) + " "
				console.log(row)
			}
		}
	}

	class MatrixIterator {
		constructor(matrix) {
			this.x = 0
			this.y = 0
			this.matrix = matrix
		}

		next() {
			if (this.y == this.matrix.height) return { done: true } // Reaches the size of the rows, which means the end of the matrix
			else {
				let value = { x: this.x, y: this.y, value: this.matrix.get(this.x, this.y) }

				this.x++

				if (this.x == this.matrix.width) { // Reaches the column's size
					this.x = 0
					this.y++
				}
				return { value, done: false }
			}
		}
	}

	Matrix.prototype[Symbol.iterator] = function() {
		return new MatrixIterator(this)
	}

	// Test
	// let matrix = new Matrix(2, 2, (x, y) => `value ${x},${y}`)
	// for (let {x, y, value} of matrix) {
	// 	console.log(x, y, value)
	// }
	```

2. Inheritance.

	```JS
	class SymmetricMatrix extends Matrix {
		constructor(size, element = (x, y) => undefined) {
			super(size, size,
				(x, y) => {
					if (x < y) return element(y, x) // Lower diagonal
					else return element(x, y) // Upper diagonal (and the diagonal)
				}
			)
		}

		set(x, y, value) {
			super.set(x, y, value)

			if (x != y) { // This conditional makes sure that the matrix stays symmetric
				super.set(y, x, value)
			}
		}
	}

	const size = 3
	let symmetricMatrix = new SymmetricMatrix(size, (x, y) => `(${x}, ${y})`)
	Matrix.show(symmetricMatrix)


	function symmetryChecker(matrix) {
		let symmetric = true

		for (let y = 0; y < size; y++) {
			for (let x = 0; x < size; x++) {
				if (!matrix.get(x, y) == matrix.get(y, x))  {
					symmetric = false
					break
				}
			}
			if (!symmetric) break
		}
		return symmetric
	}

	// Test
	// console.log(symmetryChecker(symmetricMatrix))
	```

## Ejercicios

1. A vector type.

	Write a class "Vec" that represents a vector in two-dimensional space. It takes "x" and "y" parameters (numbers), which it should save to properties of the same name.

	- Give the "Vec" prototype two methods, plus and minus, that take another vector as a parameter and return a new vector that has the sum or difference of the two vectors (this and the parameter) "x" and "y" values.

	- Add a getter property length to the prototype that computes the length of the vector—that is, the distance of the point $(x,y)$ from the origin $(0,0)$.

	```JS
	class Vec {
		constructor(x, y) {
			this.x = x
			this.y = y
		}

		plus(vector) {
			let newX = vector.x + this.x
			let newY = vector.y + this.y

			return new Vec(newX, newY)
		}

		minus(vector) {
			let newX = vector.x - this.x
			let newY = vector.y - this.y

			return new Vec(newX, newY)
		}

		get length() {
			let x = this.x
			let y = this.y

			return Math.sqrt(x * x + y * y)
		}
	}

	// Tests
	// console.log(new Vec(1, 2).plus(new Vec(2, 3))) // Vec{x: 3, y: 5}
	// console.log(new Vec(1, 2).minus(new Vec(2, 3))) // Vec{x: -1, y: -1}
	// console.log(new Vec(3, 4).length) // 5
	```

2. Groups.

	Write a class called "Group" (since Set is already taken). Like `Set`, it has "add", "delete", and "has" methods. Its constructor creates an empty group, add adds a value to the group (but only if it isn't already a member), delete removes its argument from the group (if it was a member), and has returns a Boolean value indicating whether its argument is a member of the group.

	Give the class a static "from" method that takes an iterable object as argument and creates a group that contains all the values produced by iterating over it.

	```JS
	class Group {
		constructor() {
			this.members = []
		}

		add(element) {
			if (!this.has(element)) {
				this.members.push(element)
			}
		}

		delete(element) {
			let elementIndex = this.members.indexOf(element) + 1
			console.log(elementIndex)

			if (elementIndex != 0) { // When indexOf returns "-1"
				this.members = this.members.splice(elementIndex, 1)
			}

			// this.members = this.members.filter(v => v !== value)
		}

		has(element) {
			return this.members.includes(element)
		}

		static from(collection) {
			let group = new Group()

			for (let element of collection) group.add(element)

			return group
		}

		[Symbol.iterator]() {
			return new GroupIterator(this)
		}
	}

	// Tests
	// let group = Group.from([10, 20])
	// console.log(group.has(10)) // true
	// console.log(group.has(30)) // false
	// group.add(10)
	// group.delete(10)
	// console.log(group.members)
	// console.log(group.has(10)) // false
	```

3. Iterable groups.

	```JS
	class GroupIterator {
		constructor(group) {
			this.index = 0
			this.group = group
		}

		next() {
			let members = this.group.members

			if (this.index >= members.length) return { done: true } // ">=" in case the index exceded the members.length
			else {
				let value = { index: this.index, value: members[this.index] }
				this.index++
				return { value, done: false }
			}
		}
	}

	// Test
	// for (let value of Group.from(["a", "b", "c"])) {
	// 	console.log(value)
	// }
	```

4. Borrowing a method.

	Can you think of a way to call `hasOwnProperty` on an object that has its own property by that name?

	```JS
	let map = { one: true, two: true, hasOwnProperty: true }


	console.log(Object.prototype.hasOwnProperty.call(map, "one")) // true
	// We replace the "this" (in the call) for our map to use the original function
	```
