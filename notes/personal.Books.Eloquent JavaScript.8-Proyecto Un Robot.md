---
id: joimerczlpytbtmu3pt6a6n
title: 8-Proyecto Un Robot
desc: ''
updated: 1692557060559
created: 1680463423578
---

> "[...] la pregunta de si las Máquinas Pueden Pensar [...] es tan relevante como la pregunta de si los Submarinos Pueden Nadar." - Edsger Dijkstra, The Threats to Computing Science.

---

1. Introducción

	La teoría es necesaria para aprender a programar, pero leer y entender programas reales es igual de importante.

2. La tarea

	El hecho de que algo suena como un objeto no significa automáticamente que debe ser un objeto en tu programa. Escribir por reflejo las clases para cada concepto en tu aplicación tiende a dejarte con una colección de objetos interconectados donde cada uno tiene su propio estado interno y cambiante. Tales programas a menudo son difíciles de entender y, por lo tanto, fáciles de romper.

3. Datos persistentes

	Las estructuras de datos que no cambian se llaman **inmutables** o **persistentes**. Se comportan de manera muy similar a los strings y números en que son quienes son, y se quedan así, en lugar de contener diferentes cosas en diferentes momentos.

	En JavaScript, casi todo **puede** ser cambiado, así que trabajar con valores que se supone que sean persistentes requieren cierta restricción. Hay una función llamada `Object.freeze` ("Objeto.congelar") que cambia un objeto de manera que escribir en sus propiedades sea ignorado. Podrías usar eso para asegurarte de que tus objetos no cambien, si quieres ser cuidadoso.

	```javascript
	let objeto = Object.freeze({valor: 5});
	objeto.valor = 10;
	console.log(objeto.valor); //  5
	```

	Esto es acerca de manejar la complejidad nuevamente. Cuando los objetos en mi sistema son cosas fijas y estables, puedo considerar las operaciones en ellos de forma aislada. Cuando los objetos cambian con el tiempo, eso agrega una dimensión completamente nueva de complejidad a este tipo de razonamiento.

	Para un sistema pequeño como el que estamos construyendo en este capítulo, podríamos manejar ese poco de complejidad adicional. Pero el límite más importante sobre qué tipo de sistemas podemos construir es cuánto podemos entender. Cualquier cosa que haga que tu código sea más fácil de entender hace que sea posible construir un sistema más ambicioso.

	Lamentablemente, aunque entender un sistema basado en estructuras de datos persistentes es más fácil, **diseñar** uno, especialmente cuando tu lenguaje de programación no ayuda, puede ser un poco más difícil.

4. Búsqueda de rutas

	El problema de encontrar una ruta a través de un grafo es un típico **problema de búsqueda**. Podemos decir si una solución dada (una ruta) es una solución válida, pero no podemos calcular directamente la solución de la misma manera que podríamos para 2 + 2. En cambio, tenemos que seguir creando soluciones potenciales hasta que encontremos una que funcione.

	De hecho, estamos más interesados en la ruta **más corta**. Entonces queremos asegurarnos de mirar las rutas cortas antes de mirar las más largas. Un buen enfoque sería "crecer" las rutas desde el punto de partida, explorando cada lugar accesible que aún no ha sido visitado, hasta que una ruta alcance la meta. De esa forma, solo exploraremos las rutas que son potencialmente interesantes, y encontremos la ruta más corta (o una de las rutas más cortas, si hay más de una) a la meta.
