---
id: w053k82y65taxj62u4g1yv8
title: 1-Introducción
desc: ''
updated: 1693354661451
created: 1693231864182
---

- Programación: actividad general del hombre, que significa la acción de extender o cambiar la funcionalidad de un sistema [Peter Van-Roy].

- Lenguaje de programación: es un lenguaje artificial diseñado para expresar computaciones que pueden ser llevadas a cabo por una máquina.

	> Como cualquier lenguaje, cuenta con un conjunto de símbolos y reglas sintácticas y semánticas.

- Paradigma de programación: es un enfoque para programar máquinas (computadores) basado en un conjunto coherente de principios o teoría matemática [Peter Van-Roy].

	- Las teorías de computación resultan en diferentes paradigmas ($\lambda$ calculus, $\pi$ calculus, lógica de primer orden, etc.).

	- Ninguna teoría existente cubre todos los conceptos de programación.

	> Según el tipo de situación o problema que estemos modelando, un paradigma puede ser más acertado que otro.

## Paradigmas de programacion

Los principales son:

- Declarativos (Funcional, Lógico, Por Restricciones).

- Imperativo.

- Relacional.

- Orientado a Objetos.

- Por Restricciones.

- Concurrente.

- Orientado a agentes.

### Declarativo

- Una operación es declarativa si siempre que es llamada con los mismos argumentos, retorna el mismo resultado.

- Una operación declarativa es:

	- Independiente (depende solo de sus argumentos).

	- Sin estado (no hay memoria entre distintos llamados).

	- Determinista (un llamado con los mismos argumentos da siempre el mismo resultado).

#### Funcional

- Basado en el cálculo $\lambda$ (sistema formal 1930).

- El concepto de función es fundamental.

- Funciones son ciudadanos de primera clase (las funciones pueden ser parámetros o valores de retorno de otras funciones).

##### Calculo $\lambda$

- Diseñado para investigar la definición de función, la noción de la aplicación de funciones y la recursión.

- Utilizado para definir algoritmos computables o decididles.

- Es una estrategia para definir si un algoritmo es computable.

	> Puesto que el problema de **la parada** es un problema indecidible.

- Cualquier función computable puede ser expresada y evaluada a través de este calculo.

	> Por lo tanto, es equivalente a las máquinas de Turing.

- Las funciones son consideradas un valor tipo procedimiento.

#### Declarativo lógico

- Basado en el cálculo de predicados.

- Mecanismo de demostración automática de teoremas.

- Esencial: concepto de deducción lógica.

- Programa: conjunto de axiomas y un objetivo.

#### Imperativa

- Esencial: asignación y secuenciación.

- La programación está dada en términos del estado del programa.

- Programa: secuencia de instrucciones.

	> Parecido a lo que es un guion.

#### Orientada a objetos

- Se representa el mundo real mediante objetos y sus interacciones (métodos).

- Esencial: concepto de objeto, herencia, mensaje.

- Programa: conjunto de objetos y sus interacciones.

#### Concurrente

- Basado en la teoría de concurrencia y cálculos de procesos (Cálculo $\pi$, CCS, CCP).

- Esencial: mecanismos de comunicación entre procesos.

- Programa: conjunto de procesos.

#### Relacional

- Las relaciones pueden tener cero, una o más salidas (frente a funciones).

- Puede intercambiarse el rol de las entradas y salidas.

- Selección no-determinista de una opción entre varias.

#### Restricciones

- Basado en el concepto de restricción (un predicado o relación lógica).

- Esencial.

	- Concepto de secuencia lógica.

	- Búsqueda en árboles y reducción de dominios (distribución y propagación).

- Programa: variables + restricciones (conjunto de relaciones entre variables) + estrategia de exploración.

- La búsqueda de soluciones es concurrente (se exploran varias posibilidades a la vez).

### ¿Cuál es el mejor?

- Cada uno es mejor para una clase específica de problema (la paradoja del paradigma - "more is not better or worse, only different").

- Las fronteras de los paradigmas son completamente artificiales (solo existen por razones históricas).

	> Un lenguaje puede implementar varios paradigmas.

- Un programa grande casi siempre necesita diversos paradigmas (por esto es necesario aprender múltiples paradigmas).

### ¿Por qué estudiar los conceptos?

- Incrementa la capacidad para expresar ideas.

- Amplía el espectro de conocimientos necesario para seleccionar un lenguaje.

- Incrementa la habilidad para aprender nuevos lenguajes y paradigmas.

- Mejor uso de los lenguajes de programación que ya se conocen.
