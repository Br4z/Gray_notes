---
id: la78vtjpiyhi75g3o9sbg65
title: 4-Metodología XP y BMP
desc: ''
updated: 1681523840716
created: 1681442219121
---

> "Todo en el software cambia. Los requisitos cambian. El diseño cambia. El negocio cambia. La tecnología cambia. El equipo cambia. Los miembros del equipo cambia. El problema no es cambio en si mismo, puesto que sabemos que que el cambio va a suceder; el problema es la incapacidad de adaptarnos a dicho cambio" **Kent Beck**.

# ¿Qué es XP (eXtreme Programming)?

Es una metodología ágil de desarrollo de software que se basa en la simplicidad, la comunicación y la reutilización de código desarrollado.

- Surgió como respuesta y posible solución a los problemas derivados del cambio en los requerimientos.

- Es orientada principalmente a la codificación.

![XP process](./assets/University/Desarrollo%20de%20software%20I/1_4-1%20XP_process.jpg)


## Prácticas

- El proceso de planificación

    Define características que se incluirán en la versión siguiente combinando prioridades de negocio definidas con el cliente con estimaciones técnicas de los programadores.

- Diseño simple

    Diseñar la solución más simple susceptible de implementarse en el momento. No implementar nada que no se necesite ahora.

- Recodificación

    El diseño se mejora en todo el ciclo, manteniendo el software limpio, sin duplicación, simple y completo. Si funciona bien arréglenlo de todos modos.

- Programación en pares

- Propiedad colectiva

    Todo el código pertenece al grupo. Cualquiera puede cambiar cualquier parte del código en cualquier momento, siempre que escriba antes la prueba correspondiente.

- Integración continua

    Cada pieza se integra a la base de código apenas esta lista, varias veces al día. Debe correrse la prueba antes y después de la integración.

    > Hay un repositorio dedicado solamente a este propósito.

- Cliente en sitio

    El cliente debe estar presente y disponible a tiempo completo para el equipo.

    > Línea directa.

- Estándar de codificación

- Pruebas

    > Desarrollo orientado a las pruebas UT, TDD.

## Roles

- Cliente
- Programador
- Verificadores
- Consultores técnicos
- Coach o consejero
- Tracker
- Gran jefe

## Programación en parejas

La metodología XP aconseja este tipo de programación, pues incrementa la productividad y la calidad del software desarrollado.

El trabajo en pareja involucra a dos programadores trabajando en el mismo equipo; mientras uno codifica haciendo hincapié en la calidad de la función o método que está implementando, el otro analiza si ese método es adecuado y si está bien diseñado.

## Prácticas ágiles

- Reuniones diarias

- Diseños simples

    La metodología XP sugiere que hay que conseguir diseños simples y sencillos. Hay que procurar hacerlo todo lo menos complicado posible para conseguir un diseño fácilmente entendible e impleméntable(?) que a la larga costará menos tiempo y esfuerzo desarrollar.

- Glosarios de términos

    Usar glosarios de términos y una correcta especificación de los nombres de métodos y clases ayudará a comprender el diseño y facilitará sus posteriores ampliaciones y la reutilización del código.

- Riesgos

    Si surgen problemas potenciales durante el diseño, XP sugiere utilizar una pareja de desarrolladores para que investiguen y reduzcan al máximo el riesgo que supone ese problema (spyke).

- Funcionalidad extra

    Nunca se debe añadir funcionalidad extra al sistema, aunque se piense que en un futuro será utilizada. Típicamente, solo el 10% de la misma es utilizada, lo que implica que el desarrollo de funcionalidad extra es un desperdicio de tiempo y recursos.

- Refactorizar

    Es mejorar y modificar la estructura y codificación (código) ya creado sin alterar su funcionalidad. Refactorizar supone revisar de nuevo el código para procurar optimizar su funcionamiento.

- Codificación

    Debe hacerse ateniendo estándares de codificación ya creados. Programar bajo estándares mantiene el código consistente para facilitar su comprensión y escalabilidad.

    La optimización del código siempre se debe dejar para el final. Hay que hacer que funcione y que sea correcto, más tarde se puede optimizar.

## Pruebas

- Unitarias

    Es un método que prueba una unidad estructural de código.

- Aceptación

    Se especifica por medio de criterios de aceptación.

    Para medir la calidad de un criterio de aceptación se utiliza el método SMART en el que se han de cumplir en lo máximo posible los siguientes criterios

    - S: Specific (específicas)
    - M: Measurable (medibles)
    - A: Achievable (alcanzables)
    - R: Relevant (relevantes)
    - T: Time-boxed (limitados en el tiempo)

    - Pruebas

        - acción/reacción

            Son las condiciones que una historia de usuario debe satisfacer para ser aceptada por un usuario, cliente o stakeholder.

            Si todas las HU son aceptadas, el producto de software es aceptado.

        - escenarios

            - Restringir la forma en que el usuario procedería y el sistema correspondería.

            - Elimina toda la información innecesaria.

            - Tiene la ventaja de que permite al equipo de desarrollo ir dando por hechas las funcionalidades y los casos que de ella se origina mientras las van implementando.

            - Un test de aceptación puede comprobar más de un criterio de aceptación.

            - Permiten usar más de un usuario para describir el escenario del criterio.

            - Su mayor beneficio es que los criterios de aceptación pueden ser trasladados directamente de la historia de usuario a un test de aceptación automático.

            ---

            Usa la sintaxis de **Gherkin** creada específicamente para las descripciones de comportamiento de un software. Usa la siguiente sintaxis

            - (Scenario) Escenario \[número de escenario\] \[título del escenario\]

                - número de escenario: número que identifica al escenario asociado a la historia.

                - título del escenario: describe el contexto del escenario que define un comportamiento.


            - (Given) Dado que \[Contexto\] y adicionalmente \[Contexto\]

                - Contexto: proporciona mayor descripción sobre las condiciones que desencadenan el escenario.

            - (When) cuando \[evento\] y \[evento\]

                - evento: representa la acción que el usuario ejecuta, en el contexto definido para el escenario.

            - (Then) entonces el sistema \[Resultado/Comportamiento esperado\]

                - Resultado/Comportamiento esperado: dado el contexto y la acción ejecutada por el usuario, la consecuencia es el comportamiento del sistema en esa situación.

# ¿Cómo iniciar el desarrollo de proyecto de software usando prácticas ágiles?

## El Sprint cero

En algunos equipos es frecuente el uso del llamado Sprint cero, cuyo objetivo son los **preparativos previos a comenzar el desarrollo**.

![Zero Sprint](./assets/University/Desarrollo%20de%20software%20I/1_4-2%20Zero_Sprint.jpg)

Entre las actividades principales encontramos

- Idea inicial del sistema a desarrollar.

- Fechas críticas.

- Necesidades (requerimientos a alto nivel).

- Restricciones del proyecto.

- Selección del equipo de desarrollo.

- Se selecciona las tecnologías y se dejan listos los entornos de desarrollo.

- Se acuerda la metodología de desarrollo a usar.

- Hacer la elicitación del sistema (Product Backlog).

- Se trabaja en el product backlog, principalmente en dejar listas las historias de usuario, priorizadas y estimadas.

- Se selecciona el estilo arquitectural, modelo de datos y modelo de despliegue.

- Release plan (Se hace una distribución de historias de usuario por Sprints).

# BPM

- Es un estándar para el modelamiento de procesos de negocio.

- Ayuda a entender los procesos de negocio desde una notación gráfica.

## Las historias de usuario desde los BPMs

- Usada como una técnica en el proceso de elicitación de requisitos.

- Los requisitos se obtienen desde la perspectiva de los usuarios mediante el modelado de procesos de negocio.

### Pasos

1. Modelar los procesos de negocio utilizando BPM.

2. Analizar los elementos del proceso para extraer historias de usuario para cada rol.

3. Plantear las historias de usuario

4. Realizar un análisis adicional del proceso de negocio, en conjunto con usuarios/clientes, para generar nuevas historias de usuario.

## Desafíos

- Decidir el nivel de detalle en que se modelará el proceso de negocio.

- Cómo manejar las variaciones en el proceso de negocios (secuencias de las actividades)

## Elementos básicos

- Objetos de flujo (flow objects)

    Principales elementos que ayudan a definir el comportamiento de los procesos.

    ![Flow objects](./assets/University/Desarrollo%20de%20software%20I/1_4-3%20Flow_objects.jpg)

    - Actividades

        Representan trabajo o tareas realizadas por los participantes del proceso.

        > Pueden ser manuales o automáticas, pueden ser compuestas o no.

        ![Flow objects - Activities](./assets/University/Desarrollo%20de%20software%20I/1_4-4%20Flow_objects-Activities.jpg)

    - Eventos

        Es algo que sucede durante el proceso.

        > Normalmente tiene una causa que lo acciona.

        ![Events](./assets/University/Desarrollo%20de%20software%20I/1_4-5%20Events.jpg)

        ![Events](./assets/University/Desarrollo%20de%20software%20I/1_4-6%20Events.jpg)

    - Compuertas

        Usadas para controlar la divergencia y convergencia del flujo.

        ![Gateways](./assets/University/Desarrollo%20de%20software%20I/1_4-7%20Gateways.jpg)

- Objetos de conexión (connecting objects)

    Son los que conectan los objetos de flujo.

    ![Connecting objects](./assets/University/Desarrollo%20de%20software%20I/1_4-8%20Connecting_objects.jpg)

- Canales/carriles (swimlanes)

    Utilizados para organizar las actividades del flujo. Son contenedores gráficos de las actividades de un proceso. Pueden ser áreas funcionales, sistemas, procesos, personas.

- Artefactos (artifacts)

    Se encargan de proveer información adicional sobre el proceso. No afectan la secuencia del flujo. Ejemplo: una carta, un correo electrónico, un documento, un mensaje

    ![Artifacts](./assets/University/Desarrollo%20de%20software%20I/1_4-9%20Artifacts.jpg)