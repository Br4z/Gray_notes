---
id: 82amfcjl9gb5uv80xcctuvl
title: 10-Expresiones regulares
desc: ''
updated: 1680467105737
created: 1680464943407
---

> "*Algunas personas, cuando confrontadas con un problema, piensan 'Ya sé, usaré expresiones regulares.' Ahora tienen dos problemas.*" - Jamie Zawinski.


> "*Yuan-Ma dijo: 'Cuando cortas contra el grano de la madera, mucha fuerza se necesita. Cuando programas contra el grano del problema, mucho código se necesita.'*" - Master Yuan-Ma, *The Book of Programming*.


---

1. Introducción

    Las expresiones regulares son terriblemente incómodas y extremadamente útiles. Su sintaxis es críptica, y la interfaz de programación que JavaScript proporciona para ellas es torpe. Pero son una poderosa herramienta para inspeccionar y procesar cadenas.

2. Creando una expresión regular

    ```javascript
    let re1 = new RegExp("abc");
    let re2 = /abc/;
    ```

3. Probando coincidencias

    ```javascript
    console.log(/abc/.test("abcde")); //  true
    console.log(/abc/.test("abxde")); //  false
    ```

4. Conjunto de caracteres

    Digamos que queremos encontrar cualquier número. En una expresión regular, poner un conjunto de caracteres entre corchetes hace que esa parte de la expresión coincida con cualquiera de los caracteres entre los corchetes.

    ```javascript
    console.log(/[0123456789]/.test("en 1992")); // true
    console.log(/[0-9]/.test("en 1992")); // true
    ```

    Dentro de los corchetes, un guion (`-`) entre dos caracteres puede ser utilizado para indicar un rango de caracteres, donde el orden es determinado por el número Unicode del carácter. Los caracteres 0 a 9 están uno al lado del otro en este orden (códigos 48 a 57), por lo que `[0-9]`
     los cubre a todos y coincide con cualquier dígito.

    Un número de caracteres comunes tienen sus propios atajos incorporados. Los dígitos son uno de ellos: `\d` significa lo mismo que `[0-9]`.

    | \d |                               Cualquier carácter dígito                              |
    |----|--------------------------------------------------------------------------------------|
    | \w | Un carácter alfanumérico                                                             |
    | \s | Cualquier carácter de espacio en blanco (espacio, tabulación, nueva línea y similar) |
    | \D | Un carácter que no es un dígito                                                      |
    | \W | Un carácter no alfanumérico                                                          |
    | \S | Un carácter que no es un espacio en blanco                                           |
    | .  | Cualquier carácter a excepción de una nueva línea                                    |

    ```javascript
    console.log(/[0123456789]/.test("in 1992")); // true
    console.log(/[0-9]/.test("in 1992")); // true

    let dateTime = /\d\d-\d\d-\d\d\d\d \d\d:\d\d/;
    console.log(dateTime.test("01-30-2003 15:20")); // true
    console.log(dateTime.test("30-jan-2003 15:20")); // false
    ```

    Para **invertir** un conjunto de caracteres, es decir, para expresar que deseas coincidir con cualquier carácter, **excepto** con los que están en el conjunto, puedes escribir un carácter de intercalación (`^`) después del corchete de apertura.

    ```javascript
    let noBinario = /[^01]/;
    console.log(noBinario.test("1100100010100110")); // false
    console.log(noBinario.test("1100100010200110")); // true
    ```

5. Repitiendo partes de un patrón


    ```javascript
    console.log(/'\d+'/.test("'123'")); // true
    // "+" parte del patron puede repetirse mas de una vez, pero tiene que tener al menos una coincidencia
    console.log(/'\d+'/.test("''")); // false
    console.log(/'\d*'/.test("'123'")); // true
    console.log(/'\d*'/.test("''")); // true
    // "*" permite que el patrón coincida cero veces
    ```

    ```javascript
    let reusar = /reh?usar/; // "?" parte del patron opcional
    console.log(reusar.test("rehusar")); // true
    console.log(reusar.test("reusar")); // true
    ```

    ```javascript
    let fechaHora = /\d{1,2}-\d{1,2}-\d{4} \d{1,2}:\d{2}/; // {<start>, <end>} para especificar
    // rangos (también se pueden dejar abiertos)
    console.log(fechaHora.test("30-1-2003 8:45")); // true
    ```

6. Agrupando sub expresiones

    Para usar un operador como `*` o `+` en más de un elemento a la vez, tienes que usar paréntesis. Una parte de una expresión regular que se encierre entre paréntesis cuenta como un elemento único en cuanto a los operadores que la siguen están preocupados.

    ```javascript
    let caricaturaLlorando = /boo+(hoo+)+/i; // La "i" al final de la expresión
    // hace que esta expresión regular sea insensible a mayúsculas y minúsculas
    console.log(caricaturaLlorando.test("Boohoooohoohooo")); // true
    ```

7. Coincidencias y grupos

    El método `test` es la forma más simple de hacer coincidir una expresión. Solo te dice si coincide y nada más. Las expresiones regulares también tienen un método `exec` ("ejecutar") que retorna `null` si no se encontró una coincidencia y retorna un objeto con información sobre la coincidencia de lo contrario.

    ```javascript
    let coincidencia = /\d+/.exec("uno dos 100");
    console.log(coincidencia); // ["100"]
    console.log(coincidencia.index); // 8
    ```

    Los valores de tipo string tienen un método `match` que se comporta de manera similar.

    ```javascript
    console.log("uno dos 100".match(/\d+/)); //  ["100"]
    ```

8. La clase `Date` ("Fecha")

    ```javascript
    console.log(new Date()); // Mon Nov 13 2017 16:19:11 GMT+0100 (CET)
    console.log(new Date(2009, 11, 9)); // Wed Dec 09 2009 00:00:00 GMT+0100 (CET)
    console.log(new Date(2009, 11, 9, 12, 59, 59, 999)); // Wed Dec 09 2009 12:59:59 GMT+0100 (CET)
    ```

    Las marcas de tiempo se almacenan como la cantidad de milisegundos desde el inicio de 1970, en la zona horaria UTC. Esto sigue una convención establecida por el "Tiempo Unix", el cual se inventó en ese momento. Puedes usar números negativos para los tiempos anteriores a 1970. Usar el método `getTime` ("obtenerTiempo") en un objeto fecha retorna este número. Es bastante grande, como te puedes imaginar.

9. Patrones de elección

    ```javascript
    let conteoAnimales = /\b\d+ (cerdo|vaca|pollo)s?\b/;
    console.log(conteoAnimales.test("15 cerdo")); // true
    console.log(conteoAnimales.test("15 cerdopollos")); // false
    ```

10. El método `replace`

    ```javascript
    console.log("papa".replace("p", "m")); // mapa

    console.log("Borobudur".replace(/[ou]/, "a")); // Barobudur
    console.log("Borobudur".replace(/[ou]/g, "a")); // Barabadar, "g" por global

    console.log(
        "Liskov, Barbara\nMcCarthy, John\nWadler, Philip"
            .replace(/(\w+), (\w+)/g, "$2 $1"));
    // Barbara Liskov
    // John McCarthy
    // Philip Wadler
    // Puedes hacer referencia a la coincidencia completa con $&

    let s = "la cia y el fbi";
    console.log(s.replace(/\b(fbi|cia)\b/g,
                str => str.toUpperCase())); // la CIA y el FBI
    ```

11. Codicia

    ```javascript
    function removerComentarios(codigo) {
        return codigo.replace(/\/\/.*|\/\*[^]*\*\//g, "");
    }

    console.log(removerComentarios("1 + /* 2 */3")); // 1 + 3
    console.log(removerComentarios("x = 10;// ten!")); // x = 10;
    console.log(removerComentarios("1 /* a */+/* b */ 1")); // 1  1
    ```

    Usamos `[^]` (cualquier carácter que no está en el conjunto de caracteres vacíos) como una forma de unir cualquier carácter.

    La parte `[^]*` de la expresión, como describí en la sección retroceder, primero coincidirá tanto como sea posible. Si eso causa un fallo en la siguiente parte del patrón, el emparejador retrocede un carácter e intenta nuevamente desde allí. En el ejemplo, el emparejador primero intenta emparejar el resto del string y luego se mueve hacia atrás desde allí. Este encontrará una ocurrencia de `*/` después de retroceder cuatro caracteres y emparejar eso. Esto no es lo que queríamos, la intención era hacer coincidir un solo comentario, no ir hasta el final del código y encontrar el final del último comentario de bloque.

    Debido a este comportamiento, decimos que los operadores de repetición (`+`, `*`, `?` y `{}`) son codiciosos, lo que significa que coinciden con tanto como pueden y retroceden desde allí. Si colocas un signo de interrogación después de ellos (`+?`, `*?`, `??`, `{}?`), se vuelven no-codiciosos y comienzan a hacer coincidir lo menos posible, haciendo coincidir más solo cuando el patrón restante no se ajuste a la coincidencia más pequeña.

12. La propiedad `lastIndex`

    Los objetos de expresión regular tienen propiedades. Una de esas propiedades es `source` ("fuente"), que contiene el string de donde se creó la expresión. Otra propiedad es `lastIndex` ("ultimoIndice"), que controla, en algunas circunstancias limitadas, donde comenzará la siguiente coincidencia.

    Esas circunstancias son que la expresión regular debe tener la opción global (`g`) o adhesiva (`y`) habilitada, y la coincidencia debe suceder a través del método `exec`. De nuevo, una solución menos confusa hubiese sido permitir que un argumento adicional fuera pasado a `exec`, pero la confusión es una característica esencial de la interfaz de las expresiones regulares de JavaScript.

    ```javascript
    let patron = /y/g;
    patron.lastIndex = 3;
    let coincidencia = patron.exec("xyzzy");
    console.log(coincidencia.index); // 4
    console.log(patron.lastIndex); // 5
    ```

    La diferencia entre las opciones globales y las adhesivas es que, cuando adhesivo está habilitado, la coincidencia solo tendrá éxito si comienza directamente en `lastIndex`, mientras que con global, buscará una posición donde pueda comenzar una coincidencia.

    ```javascript
    let global = /abc/g;
    console.log(global.exec("xyz abc")); // ["abc"]

    let adhesivo = /abc/y;
    console.log(adhesivo.exec("xyz abc")); // null
    ```

13. Análisis de un archivo INI

    Reglas de un archivo `INI`:

    - Las líneas en blanco y líneas que comienzan con punto y coma se ignoran.
    - Las líneas envueltas en `[` y `]` comienzan una nueva sección.
    - Líneas que contienen un identificador alfanumérico seguido de un carácter `=` agregan una configuración a la sección actual.
    - Cualquier otra cosa no es válida.
14. Caracteres internacionales

    Debido a la simplista implementación inicial de JavaScript y al hecho de que este enfoque simplista fue luego establecido en piedra como comportamiento estándar, las expresiones regulares de JavaScript son bastante tontas acerca de los caracteres que no aparecen en el idioma inglés.

    ```javascript
    console.log(/🍎{3}/.test("🍎🍎🍎")); // false
    console.log(/<.>/.test("<🌹>")); // false
    console.log(/<.>/u.test("<🌹>")); // true
    ```

    Debe agregar una opción `u` (para Unicode) a tu expresión regular para hacerla tratar a tales caracteres apropiadamente.

    ```javascript
    console.log(/\p{Script=Greek}/u.test("α")); // true
    console.log(/\p{Script=Arabic}/u.test("α")); // false
    console.log(/\p{Alphabetic}/u.test("α")); // true
    console.log(/\p{Alphabetic}/u.test("!")); // false
    ```

    Unicode define una cantidad de propiedades útiles, aunque encontrar la que necesitas puede no ser siempre trivial. Puedes usar la notación `\p{Property=Value}` para hacer coincidir con cualquier carácter que tenga el valor dado para esa propiedad. Si el nombre de la propiedad se deja afuera, como en `\p{Name}`, se asume que el nombre es una propiedad binaria como `Alfabético` o una categoría como `Número`.

15. Resumen


    | /abc/ | Una secuencia de caracteres |
    | --- | --- |
    | /[abc]/ | Cualquier carácter de un conjunto de caracteres |
    | /[^abc]/ | Cualquier carácter que no esté en un conjunto de caracteres |
    | /[0-9]/ | Cualquier carácter en un rango de caracteres |
    | /x+/ | Una o más ocurrencias del patrón x |
    | /x+?/ | Una o más ocurrencias, no codiciosas |
    | /x*/ | Cero o más ocurrencias |
    | /x?/ | Cero o una ocurrencia |
    | /x{2,4}/ | De dos a cuatro ocurrencias |
    | /(abc)/ | Un grupo |
    | /a|b|c/ | Cualquiera de varios patrones |
    | /\d/ | Cualquier carácter de dígito |
    | /\w/ | Un carácter alfanumérico ("carácter de palabra") |
    | /\s/ | Cualquier carácter de espacio en blanco |
    | /./ | Cualquier carácter excepto líneas nuevas |
    | /\b/ | Un límite de palabra |
    | /^/ | Inicio de entrada |
    | /$/ | Fin de la entrada |

    Las expresiones regulares son herramientas afiladas con un manejo incómodo. Ellas simplifican algunas tareas enormemente, pero pueden volverse inmanejables rápidamente cuando se aplican a problemas complejos. Parte de saber cómo usarlas es resistiendo el impulso de tratar de calzar cosas que no pueden ser expresadas limpiamente en ellas.