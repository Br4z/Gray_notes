---
id: a4660jxbtez1g1hz81jan0x
title: 3-Metodología Scrum
desc: ''
updated: 1681502746738
created: 1681416594846
---

>  Ágil es un término que se usa para describir los enfoques iterativos del desarrollo de software que enfatizan en la entrega incremental, la colaboración en equipo, la planificación continua y el aprendizaje continuo, en lugar de intentar entregarlo todo de una vez cerca del final.

Ágil es una **mentalidad** -> Descrita por **4 valores** -> Definida por **12 principios** -> Manifestado a traves de un **numero ilimitado de practicas**.

---

El Desarrollo ágil de software es un paradigma usado en las metodologías de desarrollo de software basado en procesos ágiles.

- Se concibieron como una alternativa a las prácticas de desarrollo de software tradicional.

- Es una "sombrilla" para un conjunto de valores, principios y prácticas.

# Manifiesto ágil

- **Individuos e interacciones** sobre procesos y herramientas.

- **Software funcionando** sobre documentación extensiva.

- **Colaboración con el cliente** sobre negociación contractual.

- **Respuesta ante el cambio** sobre seguir un plan.

> Esto es, aunque valoremos los elementos de la derecha, valoramos más los de la izquierda.

## Principios

1. Nuestra mayor prioridad es satisfacer al cliente mediante la entrega temprana y continua de software con valor.

2. Aceptamos que los requisitos cambien, incluso en etapas tardías del desarrollo.

3. Entregamos software funcional frecuentemente, entre dos semanas y dos meses, con preferencia por periodos de tiempo lo más corto posibles.

4. Entregamos software funcional frecuentemente, entre dos semanas y dos meses, con preferencia por periodos de tiempo lo más corto posibles.

5. Los proyectos se desarrollan en torno a individuos motivados. Hay que darles el entorno y el apoyo que necesitan, y confiarles la ejecución del trabajo.

6. El método más eficiente y efectivo de comunicar información al equipo de desarrollo y entre sus miembros es la conversación cara a cara (presencial o virtual).

7. El software funcionando es la medida principal de progreso.

8. Los procesos Ágiles promueven el desarrollo sostenible.

9. La atención continua a la excelencia técnica y al buen diseño mejora la Agilidad.

10. La simplicidad, o el arte de maximizar la cantidad de trabajo no realizado, es esencial.

11. Las mejores arquitecturas, requisitos y diseños emergen de equipos autoorganizados.

12. A intervalos regulares, el equipo reflexiona sobre cómo ser más efectivo para a continuación ajustar y perfeccionar su comportamiento en consecuencia.

# Scrum

> Metodología ágil de desarrollo de software.

Scrum es un proceso en el que se aplican de manera regular un conjunto de buenas prácticas para trabajar colaborativamente, en equipo, y obtener el mejor resultado posible de un proyecto de desarrollo de software.

Las fases en las que se divide y define un proceso de SCRUM son las siguientes

- El **¿quién?** y el **¿qué?**: Identifica los roles de cada uno de los miembros del equipo y define su responsabilidad en el proyecto.

- El **¿dónde?** y el **¿cuándo?**: representan el Sprint (iteración).

- El **¿por qué?** y el **¿Cómo?**: representan las herramientas que utilizan los miembros de Scrum.


Las historias de usuarios se realizan como fueron descritas para las [[metodologías ágiles | university.5th semester.Desarrollo de software I.Classes.2-Requerimientos de software###historias-de-usuario]].

![Scrum process](./assets/University/Desarrollo%20de%20software%20I/1_3-1%20Scrum_process.jpg)

## ¿Qué es priorizar?

> Proceso importante para el Product BackLog.

Como principio significa "hacer lo primero". Como proceso, significa "evaluar un grupo de elementos y clasificarlos en orden de importancia o necesidad".

> La priorización de requerimientos en todas las metodologías de desarrollo de software se considera una parte vital del proyecto, pero es especialmente importante en el desarrollo de software Ágil.

### Técnicas de priorización

- Clasificación de lista

    En la gestión de Proyectos, se trata de indicar a cada HU un orden de prioridad, empezando por el 1, luego el 2, 3, y continuando hasta n, que es la cantidad total de HU.

    > Requiere un conocimiento profundo de todas las HU definidas y un esfuerzo grande por parte del equipo, para situar cada una de las HU en la posición correcta.

- Clasificación por rangos

    Para asignar una historia de usuario a un rango se aplican los criterios de prioridad, entre los cuales tenemos

    - Alta
    - Media
    - Baja

- MoSCow

    Es una técnica que aporta un valor semántico de lo que realmente es importante.

    - M: Esta funcionalidad debe estar (MUST).
    - S: Esta funcionalidad debería estar (SHOULD).
    - C: Esta funcionalidad podría estar (COULD).
    - W: Esta funcionalidad no estará ahora, quizás en un futuro (WON'T).

## ¿Qué es estimar?

Estimar es una forma de cuantificar la magnitud del proyecto y de las tareas que tenemos que asumir, a hacernos una idea aproximada del tiempo y recursos que vamos a consumir.

La estimación en la metodología ágil consiste en asignar
puntos a una tarea o Historia de usuario, puntos que representan

- cantidad de esfuerzo que supone desarrollar la historia de usuario.

- complejidad de su desarrollo.

- riesgo.

> La estimación ágil se basa en la estimación relativa, y una técnica colaborativa, sencilla, divertida y efectiva de poder estimar historias de usuario es la de **Planning Poker**.

### Planning Poker

Su objetivo es obtener una medida de **tamaño relativo** de todas las historias respecto una historia base.

Es una técnica de estimación puesta en marcha por primera vez por James Grenning en un equipo Ágil utilizando XP en 2002, donde se utiliza una baraja de cartas con una distribución de números muy parecida a la secuencia de Fibonacci (0, 1/2, 1, 2, 3, 5, 8, 13, etc.).

---

Para realizar una sesión de planning poker hay que seguir los siguientes pasos

1. Reunir a todo el equipo y repartir las barajas a cada miembro o (iniciar la App).

2. El product owner, o moderador, lee una historia de usuario, y responde cualquier duda que tengan los miembros del equipo de desarrollo. Esto sirve para que todos tengan una comprensión en común de lo que hay que desarrollar.

3. Cada miembro del equipo de desarrollo selecciona una carta, equivalente a la estimación que él considera adecuada, y la pone boca abajo, cuando todos tengan seleccionada una carta, se ponen boca arriba todas a la vez.

4. Una vez mostradas las cartas, nos quedamos con la estimación media más elegida (moda), o se debate hasta conseguir la unanimidad.

> Esto se repite con cada historia de usuario que haya que estimar.

- Ventajas

  - Estimar colaborativamente ayuda a detectar riesgos, que se pueden ir solventando antes de comenzar la historia de usuario.

  - Promueve la participación y la colaboración.

  - Abstrae el concepto de tiempo.

  - Estimar entre varias personas nos acerca al máximo a la realidad, evitando márgenes de error muy grandes que afecten al desarrollo de producto.

- Desventajas

    - El llegar a un consenso, no garantiza el acierto

    - Requiere de un histórico de información

---

## Sprint

Es un intervalo de tiempo prefijado durante el cual se realizan HU y el resultado es un incremento de software, potencialmente entregable. Un sprint inicia con una planeación de las HU a realizar.

> Típicamente dura de 1 a 4 semanas.

> Durante el sprint a cada HU se le hace el Análisis, Diseño, Codificación, Pruebas y Despliegue.

## Reuniones

1. Sprint planning

    Es el primer evento de Scrum en dónde se planifican las tareas a realizar en el Sprint en curso. En esta reunión participan, de manera colaborativa, todo el equipo Scrum: Scrum Master, Product Owner y Equipo de Desarrollo.

    - El tiempo de esta reunión es de máximo 8 horas para Sprints de 4 semanas de duración. Para Sprints de menor duración, esta reunión debe proporcionalmente ser más corta. El Scrum Master es el encargado de asegurar que esta reunión se realice, se enseñe la importancia de la misma, y además debe asegurarse de que se realiza en el tiempo establecido.

    - La labor del Product Owner es la de describir las tareas con mayor prioridad al resto del equipo. El equipo de desarrollo pregunta todo lo necesario para convertir estas historias de usuario en tareas más específicas.

    Responde las siguientes preguntas

    - ¿Qué se puede hacer en este Sprint? - Objetivo del Sprint

    - ¿Cómo haremos el trabajo elegido? - equipo autoorganizado define como realizara los items del Sprint

2. Daily Scrum

    Es un evento de 15 minutos, cuyo objetivo es que el equipo de desarrollo sincronice actividades y cree un plan para las próximas 24 horas. Los integrantes del equipo responden las siguientes preguntas

    - ¿Qué has hecho desde la última reunión?
    - ¿Qué problemas has encontrado para realizar el trabajo previsto?
    - ¿Qué planeas hacer antes de la próxima reunión?

3. Sprint review

    Es la reunión que ocurre al final del Sprint, donde el product owner y el Equipo de Desarrollo presentan a los stakeholders el incremento terminado para su inspección y adaptación correspondiente.

    - Se revisará el incremento terminado. Se mostrará el software funcionando y los stakeholders tendrán la oportunidad de hacer cuantas preguntas estimen oportunas sobre el mismo.

    - Es una gran oportunidad para poder recibir feedback sobre el desarrollo del producto y podría conducir a actualizar el Product Backlog.

    - El software funcionando ha sido validado previamente por el product owner, que se ha encargado de trabajar con el equipo durante el Sprint para asegurarse que cumple con la Definition of Done (DoD).

    > La duración típica es de 4 horas para un sprint de 4 semanas.

4. Sprint retrospective

    Su objetivo es analizar cómo les fue en el último sprint, cómo trabajaron, qué problemas tuvieron, qué cosas funcionaron bien y cuáles no. Participan el equipo de desarrollo y el Scrum master.

    El equipo y el Scrum master analizan cómo ha sido su manera de trabajar durante el sprint, por qué está consiguiendo o no los objetivos a que se comprometió al inicio del sprint y si el incremento de producto que acaba de demostrar al cliente era lo que él esperaba o no. Respondiendo las siguientes preguntas

    - ¿Qué cosas han funcionado bien?
    - ¿Cuáles hay que mejorar?
    - ¿Qué cosas quiere probar hacer en la siguiente iteración
    - ¿Cuáles son los problemas que podrían impedirle progresar adecuadamente

        > El Scrum master se encargará de ir eliminando los obstáculos identificados que el propio equipo no pueda resolver por sí mismo.

5. Backlog refinement (Sprint grooming)

    El product owner y el equipo revisan los elementos del product backlog para asegurarse de que este contenga los items adecuados y que estos estén bien priorizados.

    > Esta actividad ocurre de manera regular y puede ser una reunión programada oficialmente o una actividad continua.

    Algunas actividades que ocurren durante el trascurso de una incluyen

    - Eliminar historias de usuarios que ya no se requieren.

    - Crear nuevas historias de usuario en respuesta a necesidades recién descubiertas.

    - Reevaluar la prioridad relativa de las historias.

    - Asignar estimaciones a historias.

    - Corregir estimaciones a la luz de la información recién descubierta.

    - Dividir historias de usuarios que son de alta prioridad pero demasiado generales para caber en una próxima iteración.

## BurnDown chart

Gráfico de trabajo pendiente a lo largo del tiempo muestra la velocidad a la que se está completando los objetivos/HU. Permite extrapolar si el equipo podrá completar el trabajo en el tiempo estimado.

> Nos recuerda cuantas HU quedan pendientes.

## Release plan

Es donde se representan los Sprints que tendrá el proyecto, las HU a desarrollar por sprint y se acuerdan las entregas a realizar. Representa el plan de trabajo para el proyecto.