---
id: 49yuppzbulwsg846tjqxn40
title: 06-Funciones de orden superior
desc: ''
updated: 1707152824904
created: 1680400899813
---

> "Tzu-li y Tzu-ssu estaban jactándose del tamaño de sus últimos programas. "Doscientas mil líneas", dijo Tzu-li, "¡sin contar los comentarios!" Tzu-ssu respondió, "Pssh, el mío tiene casi un **millón** de líneas ya." El Maestro Yuan-Ma dijo, "Mi mejor programa tiene quinientas líneas." Al escuchar esto, Tzu-li y Tzu-ssu fueron iluminados." - Master Yuan-Ma, The Book of Programming.

> "Hay dos formas de construir un diseño de software: una forma es hacerlo tan simple de manera que no haya deficiencias obvias, y la otra es hacerlo tan complicado de manera que obviamente no haya deficiencias." - C.A.R. Hoare, 1980 ACM Turing Award Lecture.

---

## Introducción

Un programa grande es un programa costoso, y no solo por el tiempo que se necesita para construirlo. El tamaño casi siempre involucra complejidad, y la complejidad confunde a los programadores. A su vez, los programadores confundidos, introducen errores en los programas. Un programa grande entonces proporciona de mucho espacio para que estos bugs se oculten, haciéndolos difíciles de encontrar.

## Abstracción

En el contexto de la programación, estos tipos de vocabularios (simples) suelen ser llamados **abstracciones**. Las abstracciones esconden detalles y nos dan la capacidad de hablar acerca de los problemas a un nivel superior (o más abstracto).

En la programación, es una habilidad útil, darse cuenta cuando estás trabajando en un nivel de abstracción demasiado bajo.

## Funciones de orden superior

Operan en otras funciones, ya sea tomándolas como argumentos o retornándolas. Como ya hemos visto que las funciones son valores regulares, no existe nada particularmente notable sobre el hecho de que tales funciones existen. El término proviene de las matemáticas, donde la distinción entre funciones y otros valores se toma más en serio.

---

Hay un método de array incorporado, `forEach` que proporciona algo como un ciclo "for/of" como una función de orden superior.

```JS
["A", "B"].forEach(letra => console.log(letra))
// A
// B
```

## Filtrando arrays

```JS
function filtrar(array, prueba) {
	let pasaron = []

	for (let elemento of array)
		if (prueba(elemento))
			pasaron.push(elemento)

	return pasaron
}
```

Observa cómo la función `filtrar`, en lugar de eliminar elementos del array existente, crea un nuevo array solo con los elementos que pasan la prueba. Esta función es **pura**. No modifica el array que se le es dado.

## Transformando con `map`

El método `map` ("mapear") transforma un array al aplicar una función a todos sus elementos y construir un nuevo array a partir de los valores retornados. El nuevo array tendrá la misma longitud que el array de entrada, pero su contenido ha sido **mapeado** a una nueva forma con base en la función.

Al igual que `forEach` y `filter`, `map` es un método de array estándar.

## Resumiendo con reduce

```JS
function reduce(array, combinar, inicio) {
	let actual = inicio

	for (let elemento of array)
		actual = combinar(actual, elemento)

	return actual
}

console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0)) // 10
```

**reduce** construye un valor al repetidamente tomar un solo elemento del array y combinándolo con el valor actual. Al sumar números, comenzarías con el número cero y, para cada elemento, agregas eso a la suma.

---

El método de array estándar `reduce`, que por supuesto corresponde a esta función, tiene una mayor comodidad. Si tu array contiene al menos un elemento, tienes permitido omitir el argumento "inicio". El método tomará el primer elemento del array como su valor de inicio y comienza a reducir a partir del segundo elemento.

## Composibilidad

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

for (let codigo of SCRIPTS)
	if (codigo.living) {
		total += codigo.year
		cuenta += 1
	}

console.log(Math.round(total / cuenta)) // 1185
```

En términos de lo que la computadora realmente está haciendo, estos dos enfoques son bastante diferentes. El primero creará nuevos arrays al ejecutar `filter` y `map`, mientras que el segundo solo computa algunos números, haciendo menos trabajo. Por lo general, puedes permitirte el enfoque legible, pero si estás procesando arrays enormes, y haciéndolo muchas veces, el estilo menos abstracto podría ser mejor debido a la velocidad extra.

## Strings y códigos de caracteres

Los strings de JavaScript están codificados como una secuencia de números de 16 bits. Estos se llaman **unidades de código**. Inicialmente, se suponía que un código de carácter Unicode encajara dentro de esa unidad (lo que da un poco más de 65,000 caracteres). Cuando quedó claro que esto no sería suficiente, muchas las personas se resistieron a la necesidad de usar más memoria por carácter. Para apaciguar estas preocupaciones, UTF-16, el formato utilizado por los strings de JavaScript, fue inventado. Este describe la mayoría de los caracteres más comunes usando una sola unidad de código de 16 bits, pero usa un par de dos de esas unidades para otros caracteres.

## Resumen

Ser capaz de pasar valores de función a otras funciones es un aspecto profundamente útil de JavaScript. Nos permite escribir funciones que modelen cálculos con "brechas" en ellas. El código que llama a estas funciones pueden llenar estas brechas al proporcionar valores de función.
