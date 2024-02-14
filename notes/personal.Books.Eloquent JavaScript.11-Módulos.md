---
id: 2mrd4fday7ldrgltxzpz5xs
title: 11-Módulos
desc: ''
updated: 1707603754289
created: 1680466125583
---

> "Escriba código que sea fácil de borrar, no fácil de extender." - Tef, Programming is Terrible.

---

## Introducción

El programa ideal tiene una estructura cristalina. La forma en que funciona es fácil de explicar, y cada parte juega un papel bien definido. Estas hacen parte del módulo disponible para el mundo exterior y mantienen el resto privado. Al restringir las formas en que los módulos interactúan entre sí, el sistema se parece más a un juego de LEGOS, donde las piezas interactúan a través de conectores bien definidos, y menos como barro, donde todo se mezcla con todo.

## Módulos

Son un intento de evitar estos problemas. Un módulo es una pieza del programa que especifica en qué otras piezas este depende (sus **dependencias**) y qué funcionalidad proporciona para que otros módulos usen (su **interfaz**).

Las interfaces de los módulos tienen mucho en común con las interfaces de objetos.

Diseñar una estructura de módulo ajustada para un programa puede ser difícil. En la fase en la que todavía estás explorando el problema, intentando cosas diferentes para ver que funciona, es posible que desees no preocuparte demasiado por eso, ya que puede ser una gran distracción. Una vez que tengas algo que se sienta sólido, es un buen momento para dar un paso atrás y organizarlo.

## Paquetes

Una de las ventajas de construir un programa a partir de piezas separadas, y ser capaces de ejecutar esas piezas por sí mismas, es que tú podrías ser capaz de aplicar la misma pieza en diferentes programas.

Un paquete es un pedazo de código que puede ser distribuido (copiado e instalado). Puede contener uno o más módulos, y tiene información acerca de qué otros paquetes depende. Un paquete también suele venir con documentación que explica qué es lo que hace, para que las personas que no lo escribieron todavía puedan hacer uso de él.

Necesitamos un lugar para almacenar y encontrar paquetes, y una forma conveniente de instalar y actualizarlos. En el mundo de JavaScript, esta infraestructura es provista por NPM.

NPM es dos cosas: un servicio en línea donde uno puede descargar (y subir) paquetes, y un programa (incluido con Node.js) que te ayuda a instalar y administrarlos.

## Módulos improvisados

```JS
const diaDeLaSemana = function() {
	const nombres = ["Domingo", "Lunes", "Martes", "Miercoles",
					"Jueves", "Viernes", "Sabado"]

	return {
		nombre(numero) { return nombres[numero] },
		numero(nombre) { return nombres.indexOf(nombre) }
	}
}()

console.log(diaDeLaSemana.nombre(diaDeLaSemana.numero("Domingo"))) // Domingo
```

## Evaluando datos como código

```JS
const x = 1

function evaluarYRetornarX(codigo) {
	eval(codigo)
	return x
}

console.log(evaluarYRetornarX("var x = 2")) // 2
```

Una forma menos aterradora de interpretar datos como código es usar el constructor `Function`. Este toma dos argumentos: un string que contiene una lista de nombres de argumentos separados por comas y un string que contiene el cuerpo de la función.

```JS
let masUno = Function("n", "return n + 1")
console.log(masUno(4)) // 5
```

Esto es precisamente lo que necesitamos para un sistema de módulos. Podemos envolver el código del módulo en una función y usar el alcance de esa función como el alcance del módulo.

## CommonJS

El enfoque más utilizado para incluir módulos en JavaScript es llamado **módulos CommonJS**. Node.js lo usa, y es el sistema utilizado por la mayoría de los paquetes en NPM.

El concepto principal en los módulos CommonJS es una función llamada `require` ("requerir"). Cuando la llamas con el nombre del módulo de una dependencia, esta se asegura de que el módulo sea cargado y retorna su interfaz.

Podemos definir `require`, en su forma más mínima, así:

```JS
require.cache = Object.create(null)

function require(nombre) {
	if (!(nombre in require.cache)) {
		let codigo = leerArchivo(nombre)
		let modulo = { exportaciones: { } }
		require.cache[nombre] = modulo
		let envolvedor = Function("require, exportaciones, modulo", codigo)
		envolvedor(require, modulo.exportaciones, modulo)
	}

	return require.cache[nombre].exportaciones
}
```

## Módulos ECMAScript

Los módulos CommonJS funcionan bastante bien y, en combinación con NPM, han permitido que la comunidad de JavaScript comience a compartir código en una gran escala.

Pero siguen siendo un poco de un truco con cinta adhesiva. La notación es ligeramente incómoda, las cosas que agregas a `exports` no están disponibles en el alcance local, por ejemplo. Y ya que `require` es una llamada de función normal tomando cualquier tipo de argumento, no solo un string literal, puede ser difícil de determinar las dependencias de un módulo sin correr su código primero.

```JS
import ordinal from "ordinal"
import { days, months } from "date-names"

export function formatDate(date, format) {/* ... */}
```

Cuando hay una vinculación llamada `default`, esta se trata como el principal valor del módulo exportado. Si importas un módulo como `ordinal` en el ejemplo, sin llaves alrededor del nombre de la vinculación, obtienes su vinculación `default`. Dichos módulos aún pueden exportar otras vinculaciones bajo diferentes nombres, además de su exportación por `default`.

```JS
export default ["Invierno", "Primavera", "Verano", "Otoño"]
import { days as nombresDias } from "date-names"

console.log(nombresDias.length) // 7
```

## Construyendo y empaquetando

Incluir un programa modular que consiste de $200$ archivos diferentes en una página web produce sus propios problemas. Si buscar un solo archivo sobre la red tarda 50 milisegundos, cargar todo el programa tardaría 10 segundos, o tal vez la mitad si puedes cargar varios archivos simultáneamente. Eso es mucho tiempo perdido. Ya que buscar un solo archivo grande tiende a ser más rápido que buscar muchos archivos pequeños, los programadores web han comenzado a usar herramientas que convierten sus programas (los cuales cuidadosamente están divididos en módulos) de nuevo en un único archivo grande antes de publicarlo en la Web. Tales herramientas son llamadas **empaquetadores**.

Y podemos ir más allá. Además de la cantidad de archivos, el **tamaño** de los archivos también determina qué tan rápido se pueden transferir a través de la red. Por lo tanto, la comunidad de JavaScript ha inventado **minificadores**. Estas son herramientas que toman un programa de JavaScript y lo hacen más pequeño al eliminar automáticamente los comentarios y espacios en blanco, cambia el nombre de las vinculaciones, y reemplaza piezas de código con código equivalente que ocupa menos espacio.

## Resumen

Los módulos proporcionan de estructura a programas más grandes al separar el código en piezas con interfaces y dependencias claras. La interfaz es la parte del módulo que es visible desde otros módulos, y las dependencias son los otros módulos este que utiliza.

Debido a que históricamente JavaScript no proporcionó un sistema de módulos, el sistema CommonJS fue construido encima. Entonces, en algún momento, **consiguió** un sistema incorporado, que ahora coexiste incómodamente con el sistema CommonJS.

Un paquete es una porción de código que se puede distribuir por sí misma. NPM es un repositorio de paquetes de JavaScript. Puedes descargar todo tipo de paquetes útiles (e inútiles) de él.
