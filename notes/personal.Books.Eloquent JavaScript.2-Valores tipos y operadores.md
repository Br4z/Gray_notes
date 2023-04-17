---
id: 1ecavrit13nfw1zbkiu7h8u
title: 2-Valores, tipos y operadores
desc: ''
updated: 1680402941534
created: 1680397563032
---

> "*Debajo de la superficie de la máquina, el programa se mueve. Sin esfuerzo, se expande y se contrae. En gran armonía, los electrones se dispersan y se reagrupan. Las figuras en el monitor son tan solo ondas sobre el agua. La esencia se mantiene invisible debajo de la superficie.*" - Master Yuan-Ma, *The Book of Programming*.

---

1. Strings

    La siguiente notación es utilizada: cuando una barra invertida (`\`) es encontrada dentro de un texto entre comillas, indica que el carácter que le sigue tiene un significado especial. Esto se conoce como **escapar** el carácter. Una comilla que es precedida por una barra invertida no representará el final del string, sino que formara parte del mismo. Cuando el carácter `n` es precedido por una barra invertida, este se interpreta como un Newline (salto de línea). De la misma forma, `t` después de una barra invertida, se interpreta como un carácter de tabulación.

    ---

    Cuando escribes algo dentro de `${}` en una plantilla literal, el resultado será computado, convertido a string, e incluido en esa posición, ejemplo:

    ```javascript
    `la mitad de 100 es ${100 / 2}` // la mitad de 100 es 50
    ```

2. Valores booleanos

    La forma en la que los strings son ordenados, es aproximadamente alfabético, aunque no realmente de la misma forma que esperaríamos ver en un diccionario: las letras mayúsculas son siempre "menores que" las letras minúsculas, así que `"Z" < "a"`, y caracteres no alfabéticos (como `!`, `-` y demás) son también incluidos en el ordenamiento. Cuando comparamos strings, JavaScript evalúa los caracteres de izquierda a derecha, comparando los códigos Unicode uno por uno.

    ```javascript
    console.log("Aardvark" < "Zoroaster") // true
    ```

3. Valores vacíos

    Existen dos valores especiales, escritos como `null` y `undefined`, que son usados para denotar la ausencia de un valor **significativo**. Son en sí mismos valores, pero no traen consigo información.

    ---

    Muchas operaciones en el lenguaje que no producen un valor significativo (veremos algunas más adelante), producen `undefined` simplemente porque tienen que producir **algún** valor.

4. Conversión de tipos automática

    Cuando un operador es aplicado al tipo de valor "incorrecto", JavaScript silenciosamente convertirá ese valor al tipo que necesita, utilizando una serie de reglas que frecuentemente no dan el resultado que quisieras o esperarías. Esto es llamado **coerción de tipo**.

5. Funcionamiento de los operadores `&&`, `||` y `?` (condicional)

    `||`: Devolverá el valor de su izquierda cuando este puede ser convertido a verdadero y de ser lo contrario devolverá el valor de la derecha.

    Si tenemos un valor que puede estar vacío, podemos usar `||`  después de este para remplazarlo con otro valor. Si el valor inicial puede ser convertido a falso, obtendrá el reemplazo en su lugar.

    ```javascript
    console.log(null || "usuario") // usuario
    console.log("Agnes" || "usuario") // Agnes
    ```

    `&&`: Funciona de manera similar, pero de forma opuesta. Cuando el valor a su izquierda es algo que se convierte a falso, devuelve ese valor, y de lo contrario, devuelve el valor a su derecha.

    Otra propiedad importante de estos dos operadores es que la parte de su derecha solo es evaluada si es necesario. En el caso de `true || X`, no importa que sea `X` -aun si es una pieza del programa que hace algo **terrible**- el resultado será verdadero, y `X` nunca será evaluado. Lo mismo sucede con `false && X`, que es falso e ignorará `X`. Esto es llamado **evaluación de corto circuito**.

    `?` (condicional):

    ```javascript
    console.log(true ? 1 : 2); // 1
    console.log(false ? 1 : 2); // 2
    ```

    El valor a la izquierda del signo de interrogación "decide" cuál de los otros dos valores será retornado. Cuando es verdadero, elige el valor de en medio, y cuando es falso, el valor de la derecha.

    El operador condicional funciona de manera similar. Del segundo y tercer valor, solo el que es seleccionado es evaluado.