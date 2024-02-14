---
id: tetnorq4s99z5g7dhaupq7a
title: 12-Programación asíncrona
desc: ''
updated: 1707690090423
created: 1680466612592
---

> "¿Quién puede esperar tranquilamente mientras el barro se asienta? ¿Quién puede permanecer en calma hasta el momento de actuar?" - Laozi, Tao Te Ching.

---

## Introducción

Cuando una cosa como tal esté sucediendo, sería una pena dejar que el procesador se mantenga inactivo, podría haber algún otro trabajo que este pueda hacer en el mientras tanto. En parte, esto es manejado por tu sistema operativo, que cambiará el procesador entre múltiples programas en ejecución. Pero eso no ayuda cuando queremos que un **único** programa pueda hacer progreso mientras este espera una solicitud de red.

## Devolución de llamadas (callback)

Un enfoque para la programación asincrónica es hacer que las funciones que realizan una acción lenta, tomen un argumento adicional, una **función de devolución de llamada**. La acción se inicia y, cuando esta finaliza, la función de devolución es llamada con el resultado.

## Promesas

Una **promesa** es una acción asíncrona que puede completarse en algún punto y producir un valor. Esta puede notificar a cualquier persona que esté interesada cuando su valor esté disponible.

```javascript
let quince = Promise.resolve(15);
quince.then(valor => console.log(`Obtuve ${valor}`)); // Obtuve 15
```

Es útil pensar acerca de las promesas como dispositivos para mover valores a una realidad asincrónica. Un valor normal simplemente está allí. Un valor prometido es un valor que **podría** ya estar allí o podría aparecer en algún momento en el futuro. Las computaciones definidas en términos de promesas actúan en tales valores envueltos y se ejecutan de forma asíncrona a medida los valores se vuelven disponibles.

## Fracaso