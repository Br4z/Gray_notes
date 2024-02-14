---
id: l46n25x3imv01amxh8com6i
title: 03-Estructura del programa
desc: ''
updated: 1707152846570
created: 1680398135817
---

> "Y mi corazón brilla de un color rojo brillante bajo mi piel transparente y translúcida, y tienen que administrarme 10cc de JavaScript para conseguir que regrese. (respondo bien a las toxinas en la sangre.) Hombre, esa cosa es ¡increíble!" - _why, Why's (Poignant) Guide to Ruby.

---

## Expresiones y declaraciones

En algunos casos, JavaScript te permite omitir el punto y coma al final de una declaración. En otros casos, tiene que estar allí, o la próxima línea serán tratadas como parte de la misma declaración. Las reglas para saber cuando se puede omitir con seguridad son algo complejas y propensas a errores.

## Vinculaciones

Las palabras "var" y "const" también pueden ser usadas para crear vinculaciones, en una manera similar a "let".

La primera, "var" (abreviatura de "variable"), es la forma en la que se declaraban las vinculaciones en JavaScript previo al 2015. Por ahora, recuerda que generalmente hace lo mismo, pero raramente la usaremos porque tiene algunas propiedades confusas.

## Entorno

La colección de vinculaciones y sus valores que existen en un momento dado se llama **entorno**. Cuando se inicia un programa, este entorno no está vacío. Siempre contiene vinculaciones que son parte del estándar del lenguaje, y la mayoría de las veces, también tiene vinculaciones que proporcionan formas de interactuar con el sistema circundante.

## Funciones

Una función es una pieza de programa envuelta en un valor. Dichos valores pueden ser **aplicados** para ejecutar el programa envuelto.

## Función `console.log`

Aunque los nombres de las vinculaciones no puedan contener caracteres de puntos, `console.log` tiene uno. Esto es porque `console.log` no es una vinculación simple. En realidad, es una expresión que obtiene la propiedad `log` del valor mantenido por la vinculación `console`.

## Indentació

Podrías escribir un programa en una sola línea inmensa si así quisieras.

---

El rol de la indentación dentro de los bloques es hacer que la estructura del código se destaque. En código donde se abren nuevos bloques dentro de otros bloques, puede ser difícil ver dónde termina un bloque y donde comienza el otro. Con la indentación apropiada, la forma visual de un programa corresponde a la forma de los bloques dentro de él.
