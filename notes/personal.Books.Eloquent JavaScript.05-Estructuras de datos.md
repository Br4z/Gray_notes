---
id: lax77y3vrxbhr6a142qsiq8
title: 05-Estructuras de datos
desc: ''
updated: 1707152841151
created: 1680399332436
---

> "En dos ocasiones me han preguntado, "Dinos, Sr. Babbage, si pones montos equivocados en la máquina, saldrán las respuestas correctas? \[...\] No soy capaz de comprender correctamente el tipo de confusión de ideas que podrían provocar tal pregunta." - Charles Babbage, Passages from the Life of a Philosopher (1864).

---

## Introducción

Los números, los booleanos y los strings son los átomos que constituyen las estructuras de datos. Sin embargo, muchos tipos de información requieren más de un átomo. Los **objetos** nos permiten agrupar valores -incluidos otros objetos- para construir estructuras más complejas.

## Propiedades

Las dos formas principales de acceder a las propiedades en JavaScript son con un punto y con corchetes. Tanto `valor.x` como `valor[x]` acceden una propiedad en `valor`, pero no necesariamente la misma propiedad. La diferencia está en cómo se interpreta `x`. Cuando se usa un punto, la palabra después del punto es el nombre literal de la propiedad. Cuando usas corchetes, la expresión entre corchetes es **evaluada** para obtener el nombre de la propiedad. Mientras `valor.x` obtiene la propiedad de `valor` llamada "x", `valor[x]` intenta evaluar la expresión `x` y usa el resultado, convertido en un string, como el nombre de la propiedad.

## Métodos

Las propiedades que contienen funciones generalmente son llamadas **métodos** del valor al que pertenecen.

> Un ejemplo es `toUpperCase` (método de string).

## Objetos

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

## Mutabilidad

Vimos que los valores de objeto pueden ser modificados. Los tipos de valores discutidos en capítulos anteriores, como números, strings y booleanos, son todos **inmutables**, es imposible cambiar los valores de aquellos tipos. Puedes combinarlos y obtener nuevos valores a partir de ellos, pero cuando tomas un valor de string específico, ese valor siempre será el mismo. El texto dentro de él no puede ser cambiado. Si tienes un string que contiene `"gato"`, no es posible que otro código cambie un carácter en tu string para que deletree "rato".

## El diario del licántropo

```JS
let diario = []

function añadirEntrada(eventos, ardilla) {
	diario.push({ eventos, ardilla })
}
```

Ten en cuenta que el objeto agregado al diario se ve un poco extraño. En lugar de declarar propiedades como `eventos: eventos`, simplemente da un nombre de propiedad. Este es un atajo que representa lo mismo si el nombre de propiedad en la notación de llaves no es seguido por un valor, el valor se toma de la vinculación con el mismo nombre.

---

La **correlación** es una medida de dependencia entre variables estadísticas. Una variable estadística no es lo mismo que una variable de programación. En las estadísticas, normalmente tienes un conjunto de **medidas**, y cada variable se mide para cada medida. La correlación entre variables generalmente se expresa como un valor que varía de $-1$ a $1$. Una correlación de cero significa que las variables no están relacionadas. Una correlación de uno índica que las dos están perfectamente relacionadas -si conoces una, también conoces la otra. Uno negativo también significa que las variables están perfectamente relacionadas, pero que son opuestas- cuando una es verdadera, la otra es falsa.

Para calcular la medida de correlación entre dos variables booleanas, podemos usar el **coeficiente phi** ($\phi$). Esta es una fórmula cuya entrada es una tabla de frecuencias que contiene la cantidad de veces que las diferentes combinaciones de las variables fueron observadas. El resultado de la fórmula es un número entre $-1$ y $1$ que describe la correlación.

$$
\phi = \frac{ n_{ 11 } n_{ 00 } - n_{ 10 } n_{ 01 } }{ \sqrt{ n_{ 1\cdot } n_{ 0\cdot } n_{ \cdot 1 } n_{ \cdot 0 } } }
$$

## Ciclos de array

```JS
for (let entrada of DIARIO)
	console.log(`${entrada.eventos.length} eventos.`)
```

Cuando un ciclo `for` se vea de esta manera, con la palabra "of" ("de") después de una definición de variable, recorrerá los elementos del valor dado después `of`. Esto funciona no solo para arrays, sino también para strings y algunas otras estructuras de datos.

## Parámetros restantes

```JS
function maximo(...numeros) {
	let resultado = -Infinity

	for (let numero of numeros)
		if (numero > resultado)
			resultado = numero

	return resultado
}

console.log(maximo(4, 1, 9, -2)) // 9
```

---

```JS
let palabras = ["nunca", "entenderas"]

console.log(["tu", ...palabras, "completamente"]) // ["tu", "nunca", "entenderas", "completamente"]
```

## Objeto `Math`

Es usado como un contenedor que agrupa un grupo de funcionalidades relacionadas. Solo hay un objeto `Math`, y casi nunca es útil como un valor. Más bien, proporciona un **espacio de nombre** para que todas estas funciones y valores no tengan que ser vinculaciones globales.

Tener demasiadas vinculaciones globales "contamina" el espacio de nombres. Cuanto más nombres hayan sido tomados, es más probable que accidentalmente sobrescribas el valor de algunas vinculaciones existentes. Por ejemplo, no es poco probable que quieras nombrar algo "max" en alguno de tus programas. Dado que la función `max` ya incorporada en JavaScript está escondida dentro del Objeto `Math`, no tenemos que preocuparnos por sobrescribirla.

---

Aunque las computadoras son máquinas deterministas -siempre reaccionan de la misma manera dada la misma entrada- es posible hacer que produzcan números que parecen aleatorios. Para hacer eso, la máquina mantiene algún valor escondido, y cada vez que le pidas un nuevo número aleatorio, realiza cálculos complicados en este valor oculto para crear un nuevo valor. Esta almacena un nuevo valor y retorna un número derivado de él. De esta manera, puede producir números nuevos y difíciles de predecir de una manera que **parece** aleatoria.

## JSON

JavaScript nos da las funciones `JSON.stringify` y `JSON.parse` para convertir datos hacia y desde este formato. El primero toma un valor en JavaScript y retorna un string codificado en JSON. La segunda toma un string como ese y lo convierte al valor que este codifica.

```JS
let string = JSON.stringify(
	{ ardilla: false, eventos: ["fin de semana"] }
)

console.log(string) // { "ardilla": false, "eventos": ["fin de semana"] }
console.log(JSON.parse(string).eventos) // ["fin de semana"]
```

## Resumen

Los objetos y arrays (que son un tipo específico de objeto) proporcionan formas de agrupar varios valores en un solo valor. Conceptualmente, esto nos permite poner un montón de cosas relacionadas en un bolso y correr alrededor con el bolso, en lugar de envolver nuestros brazos alrededor de todas las cosas individuales, tratando de aferrarnos a ellas por separado.
