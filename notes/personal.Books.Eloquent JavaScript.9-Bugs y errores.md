---
id: jqfmgfdythd4tgmqjphk4hx
title: 9-Bugs y errores
desc: ''
updated: 1680467115604
created: 1680464513385
---

> "*Arreglar errores es dos veces más difícil que escribir el código en primer lugar. Por lo tanto, si escribes código de la manera más inteligente posible, eres, por definición, no lo suficientemente inteligente como para depurarlo.*" - Brian Kernighan and P.J. Plauger, *The Elements of Programming Style*.

---

1. Introducción

    Si un programa es un pensamiento cristalizado, puedes categorizar en grandes rasgos a los bugs en aquellos causados al confundir los pensamientos, y los causados por cometer errores al convertir un pensamiento en código. El primer tipo es generalmente más difícil de diagnosticar y corregir que el último.

2. Lenguaje

    Muchos errores podrían ser señalados automáticamente por la computadora, si esta supiera lo suficiente sobre lo que estamos tratando de hacer. Pero aquí la soltura de JavaScript es un obstáculo. Su concepto de vinculaciones y propiedades es lo suficientemente vago que rara vez atrapará errores ortográficos antes de ejecutar el programa. E incluso entonces, te permite hacer algunas cosas claramente sin sentido, como calcular `true * "mono"`.

    El proceso de encontrar errores -bugs- en los programas se llama **depuración**.

3. Modo estricto

    ```javascript
    function puedesDetectarElProblema() {
        "use strict";
        for (contador = 0; contador < 10; contador++) {
            console.log("Feliz feliz");
        }
    }

    puedesDetectarElProblema(); // ReferenceError: contador is not defined
    ```

    Normalmente, cuando te olvidas de poner `let` delante de tu vinculación, como con `contador` en el ejemplo, JavaScript silenciosamente crea una vinculación global y utiliza eso.

    Los constructores creados con la notación `class` siempre se quejan si se llaman sin `new`, lo que hace que esto sea menos un problema incluso en el modo no-estricto.

    En resumen, poner `"use strict"` en la parte superior de tu programa rara vez duele y puede ayudarte a detectar un problema.

4. Tipos

    Algunos lenguajes quieren saber los tipos de todas tus vinculaciones y expresiones incluso antes de ejecutar un programa. Estos te dirán de una vez cuando uses un tipo de una manera inconsistente. JavaScript solo considera a los tipos cuando ejecuta el programa, e incluso a menudo intentará convertir implícitamente los valores al tipo que espera, por
    lo que no es de mucha ayuda

    Aun así, los tipos proporcionan un marco útil para hablar acerca de los programas. Muchos errores provienen de estar confundido acerca del tipo de valor que entra o sale de una función. Si tienes esa información anotada, es menos probable que te confundas.

5. Probando

    Escribir pruebas de esta manera tiende a producir código bastante repetitivo e incómodo. Afortunadamente, existen piezas de software que te ayudan a construir y ejecutar colecciones de pruebas (**suites de prueba**) al proporcionar un lenguaje (en forma de funciones y métodos) adecuado para expresar pruebas y obtener información informativa cuando una prueba falla. Estos generalmente se llaman **corredores de pruebas**.

    Algunos programas son más fáciles de probar que otros programas. Por lo general, con cuantos más objetos externos interactúe  el código, más difícil es establecer el contexto en el cual probarlo.

6. Depuración

    Una vez que notes que hay algo mal con tu programa porque se comporta mal o produce errores, el siguiente paso es descubrir **cuál** es el problema.

    A veces es obvio. El mensaje de error apuntará a una línea específica de tu programa, y si miras la descripción del error y esa línea de código, a menudo puedes ver el problema.

    Pero no siempre. A veces, la línea que provocó el problema es simplemente el primer lugar en donde un valor extraño producido en otro lugar es usado de una manera inválida.

7. Propagación de errores

    Desafortunadamente, no todos los problemas pueden ser prevenidos por el programador. Si tu programa se comunica con el mundo exterior de alguna manera, es posible obtener una entrada malformada, sobrecargarse con el trabajo, o la red falle en la ejecución.

    En muchas situaciones, principalmente cuando los errores son comunes y la persona que llama debe tenerlos explícitamente en cuenta, retornar un valor especial es una buena forma de indicar un error. Sin embargo, esto tiene sus desventajas. Primero, ¿qué pasa si la función puede retornar cada tipo de valor posible? En tal función, tendrás que hacer algo como envolver el resultado en un objeto para poder distinguir el éxito del fracaso.

8. Excepciones

    Cuando una función no puede continuar normalmente, lo que nos **gustaría** hacer es simplemente detener lo que estamos haciendo e inmediatamente saltar a un lugar que sepa cómo manejar el problema. Esto es lo que el **manejo de excepciones** hace.

    Escribir programas que funcionan de manera confiable, incluso cuando aparecen excepciones en lugares inesperados, es muy difícil. Muchas personas simplemente no se molestan, y porque las excepciones suelen reservarse para circunstancias excepcionales, el problema puede ocurrir tan raramente que nunca siquiera es notado. Si eso es algo bueno o algo realmente malo, depende de cuánto daño hará el software cuando falle.

9. Captura selectiva

    Cuando una excepción llega hasta el final de la pila sin ser capturada, esta es manejada por el entorno. Lo que esto significa difiere entre los entornos. En los navegadores, una descripción del error generalmente será escrita en la consola de JavaScript (accesible a través de las herramientas de desarrollador del navegador). Node.js, el entorno de JavaScript sin navegador, es más cuidadoso con la corrupción de datos. Aborta todo el proceso cuando ocurre una excepción no manejada.

    JavaScript (en una omisión bastante evidente) no proporciona soporte directo para la captura selectiva de excepciones: o las atrapas todas o no atrapas nada. Esto hace que sea tentador **asumir** que la excepción que obtienes es en la que estabas pensando cuando escribiste el bloque `catch`.

10. Afirmaciones

    Son comprobaciones dentro de un programa que verifican que algo esté en la forma en la que se supone que debe estar. Se usan no para manejar situaciones que puedan aparecer en el funcionamiento normal, pero para encontrar errores hechos por el programador.

11. Resumen

    Los errores y las malas entradas son hechos de la vida. Una parte importante de la programación es encontrar, diagnosticar y corregir errores. Los problemas pueden será más fáciles de notar si tienes un conjunto de pruebas automatizadas o si agregas afirmaciones a tus programas.

    Por lo general, los problemas causados por factores fuera del control del programa deberían ser manejados con gracia. A veces, cuando el problema pueda ser manejado localmente, los valores de devolución especiales son una buena forma de rastrearlos. De lo contrario, las excepciones pueden ser preferibles.

    Al lanzar una excepción, se desenrolla la pila de llamadas hasta el próximo bloque `try/catch` o hasta el final de la pila. Se le dará el valor de excepción al bloque `catch` que lo atrape, que debería verificar que en realidad es el tipo esperado de excepción y luego hacer algo con eso. Para ayudar a controlar el impredecible flujo de control causado por las excepciones, los bloques `finally` se pueden usar para asegurarte de que una parte del código *siempre* se ejecute cuando un bloque termina.