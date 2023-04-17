---
id: 4su2xxwemlymxtr829dhzv7
title: 2-Requerimientos de software
desc: ''
updated: 1681502746749
created: 1681175100572
---

- Un requisito o requerimiento es una declaración que identifica una característica o restricción operativa, funcional o de diseño de un producto o proceso, que es no ambigua, comprobable o medible, y necesaria para la aceptación del producto o proceso.

- Los requerimientos especifican lo que desea el cliente y
definen las acciones o actividades que debe hacer o
cumplir un sistema de software.


Definir adecuadamente los requerimientos permitirá

- Entender claramente cuál es el objetivo

- Realizar la estimación de costos y tiempo de desarrollo

- Crear un plan de trabajo

- Establecer prioridades


> La mayoría de lo problemas en el desarrollo de software están relacionados con los requerimientos.

---

Cosas que cumple un requerimiento

- Resuelve una necesidad

    Para alcanzar un objetivo.

- Satisface condiciones

    Capacidad que debe estar presente en un sistema o componentes del sistema para satisfacer un contrato, un estándar, una especificación u otro documento formal.

- Define lo que se necesita

    Definen lo que el sistema debe hacer en cuanto a sus procesos, consultas, reportes, ...

# Clasificación

- Funcionales

    Declaraciones de los servicios que debe proporcionar el sistema, la forma en que el sistema debe reaccionar a las entradas y la forma en que el sistema debe comportarse en situaciones particulares.

    En algunos casos, los requerimientos funcionales de los sistemas también establecen explícitamente lo que el sistema no debe hacer.

- No funcionales

    Limitaciones en los servicios o funciones ofrecidas por el sistema como de tiempo, limitaciones en el proceso de desarrollo, de rendimiento, de calidad, normas, tecnología, etc.

---

Los requerimientos

- se suelen especificar en lenguaje natural

- se expresan de forma individual

- se organizan de forma jerárquica (a distintos niveles de detalle)

- a menudo, se numeran (para facilitar su gestión)

---

Los problemas surgen cuando los requerimientos no son declarados con precisión.

- Requerimientos ambiguos pueden interpretarse de diferentes maneras por los desarrolladores y usuarios.

- Deben estar redactados de tal forma que sean comprensibles para usuarios sin conocimientos técnicos avanzados.

# Características

1. Necesario

    Lo que pida un requisito debe ser necesario para el producto.

2. Correcto

    **sí y solo sí**, cada requisito especificado es un requisito que el software **debe hacer**.

3. No ambiguo

    El texto debe ser claro, preciso y tener una única interpretación posible.

4. Conciso

    Debe redactarse en un lenguaje comprensible por los clientes en lugar de uno de tipo técnico y especializado, aunque aun así debe referenciar los aspectos importantes.

5. Consistente

    Ningún requisito debe entrar en conflicto con otro requisito diferente.

6. Completo

    Los requisitos deben contener en sí mismos toda la información necesaria, y no remitir a otras fuentes externas que los expliquen con más detalle.

7. Alcanzable

    Un requisito debe ser un objetivo realista, posible de ser alcanzado en el tiempo y los recursos disponibles.

8. Verificable

    Se debe poder verificar con absoluta certeza, si el requisito fue satisfecho o no.

# Recomendaciones para redactarlos

- Usar un formato estándar y asegurar la adherencia al mismo para todos los requerimientos.

- Utilizar el lenguaje de manera consistente.

- Resaltar el texto para distinguir las partes clave del requerimiento.

- Evite el uso de jerga informática.

Un requerimiento se especifica en dos pasos:

1. Realizar una **descripción** del requerimiento lo más precisa posible.

2. Realizar la **especificación de los detalles** del requerimiento (requerida al momento de implementar).

    En los detalles podemos encontrar campos como

    - Identificador
    - Tipo
    - Datos de entrada
    - Proceso
    - Datos de salida
    - Resultados
    - Origen
    - Dirigido
    - Prioridad
    - Requerimientos asociados

    > Estos detalles le sirven al desarrollador para entender con más precisión lo que hay que programar.

# Especificación

![Specification of requirements](./assets/University/Desarrollo%20de%20software%20I/1_2-1%20Specification_requirements.jpg)


![Specification of system](./assets/University/Desarrollo%20de%20software%20I/1_2-2%20Specification_system.jpg)

# Técnicas de obtención

- Entrevistas

    Es un diálogo formal o informal con personas, donde se busca respuesta a un conjunto de preguntas planeadas. Es importante

     - su propósito: entender con claridad cada cosa que el cliente desea.

     - identificar posibles entrevistados.

     - familiarizarse con el vocabulario del negocio.

     - tomar apuntes o grabar la reunión.

- Lluvia de ideas

    Reunión donde se proponen ideas para solucionar un problema.

    > Por lo general, se utiliza para identificar posibles soluciones a los problemas, para aplicaciones nuevas donde hay pocos antecedentes.

    Es importante

    - tener un moderador y limite de tiempo para la discusión de cada parte.

    - tomar apuntes o grabar la reunión.

- BMP (**B**usiness **P**rocess **M**odel)

    Es una notación gráfica estandarizada que permite el modelado de procesos de negocio, en un formato de flujo de trabajo.

    Su principal objetivo es proporcionar una notación gráfica estándar que sea fácilmente legible y entendible por parte de todos los involucrados e interesados del negocio (stakeholders). Entre estos interesados están los analistas de negocio (quienes definen y redefinen los procesos), los desarrolladores técnicos (responsables de implementar los procesos), los gerentes y administradores del negocio (quienes monitorizan y gestionan los procesos).

# Técnicas de validación

1. Validación de expertos

2. Prototipado de interfaz de usuario

    Es una técnica de representación aproximada de la interfaz de usuario.

    Los dos tipos principales son

    - Desechables

        Se utilizan solo para la validación de los requisitos y posteriormente se desechan. Pueden ser prototipos en papel o en software.

    - Evolutivos

        Una vez utilizados para la validación de los requisitos, se mejora su calidad y se convierten progresivamente en el producto final.

# Metodologías tradicionales

## Requerimientos no funcionales

- Especifican "qué tan bien" y "como" debe comportarse un sistema.

- Imponen **restricciones** que típicamente limitan los requerimientos funcionales.

- Conocidos como "requisitos técnicos", "atributos de calidad" o "requisitos de calidad de servicio".

Son aquellos requerimientos que **no se refieren directamente** a las funciones específicas que entrega el sistema, sino a las **propiedades** emergentes de este, como la fiabilidad, la respuesta en el tiempo y la capacidad de almacenamiento.

Además, definen las **restricciones** del sistema como la capacidad de los dispositivos de entrada/salida y la representación de datos que se utiliza en la interface del sistema.

---

- Factores internos: los requerimientos no funcionales **surgen de la necesidad del usuario**, debido a las restricciones en el **presupuesto**, a las políticas de la organización, a la necesidad de **interoperabilidad** con otros sistemas de software o hardware.

- Factores externos: como los reglamentos de seguridad, las políticas del gobierno, entre otros.

### Tipos

- Eficiencia

- Seguridad de lógica y de datos

- Usabilidad

- Tecnología

# Metodologías ágiles

## Requerimientos

- Las metodologías ágiles se concibieron como una alternativa a las prácticas de desarrollo de software tradicional.

- Es una "sombrilla" para un conjunto de valores, principios y prácticas.

- **Las Historias de Usuario (HU) es el mecanismo usado para obtener las necesidades del usuario**.

---

Los requerimientos no funcionales imponen **restricciones** para guiar el trabajo en un proyecto de desarrollo.

### Historias de usuario

> En el desarrollo ágil de software, las historias de usuario ayudan a articular el **valor que puede aportar** una característica de la aplicación a desarrollar y a comprender mejor por qué los usuarios quieren una determinada funcionalidad.

- describen las necesidades de algo que es valioso para un usuario de
un sistema o software.

- Una historia debe permitir conocer la base de las necesidades del usuario, así como los detalles que después permitan fijar la batería de pruebas para poder determinar si un desarrollo es correcto o no.

- Las historias de usuario luego se pueden dividir en tareas técnicas para su implementación.

Esperamos que una historia de usuario siga el modelo **INVEST**

- Independiente: una historia debería ser independiente de otra. Facilita planificar, priorizar y estimar.

- Negociable: la "tarjeta" de la historia es solo una descripción corta que no incluye detalles. Los detalles se añaden mediante la conversación.

- Valiosa: cada historia tiene que tener valor para el cliente (para el usuario o el comprador).

- Estimable

    > Historias demasiado largas o inconcretas no se pueden estimar.

- Pequeña: una buena historia debe ser pequeña en esfuerzo, debería ser realizable en menos de una semana.

- Verificable (testable): una buena historia necesita poder probarse para saber si sea realizado con éxito.

---

Para crearlas usamos la plantilla

Como **\<actor\>** desero **\<tarea\>** para **\<propósito\>**

> Plantilla propuesta por Mike Cohn.

---

En sus características encontraremos que deben

- ser lo suficientemente completa como para demostrar el valor para el usuario.

    > Incluir archivos y documentación de apoyo si es necesario.

- centrarse en el usuario.

- ser breve, sencilla y clara.

    > Sencillo como para desarrollarlo en una sola iteración.

- Si no se identifica necesidades precisas, se puede iniciar con una historia de usuario **Épica**.

---

- DoD (Definition of Done)

    Cada equipo de desarrollo tiene su propia definición, pero la DoD puede ser una lista de actividades o simplemente una serie de acuerdos que agregan valor verificable y demostrable al producto.

    Por lo general incluye los siguientes aspectos

    - Diseño
    - Código
    - Documentación
    - Despliegue
    - Pruebas
    - Otros

---

> Spyke (investigar de cosas que el equipo de desarrollo no conoce).

#### Historia Épicas

Es una gran historia de usuario que no se puede entregar como se define en una sola iteración o es lo suficientemente grande como para dividirse en historias de usuario más pequeñas.

Hacemos la descomposición con el fin de

- expresar los pasos para implementar una historia de usuario.

- precisar la actividad en la que está trabajando.

- ayudar para pedir colaboración más específica.

- conducir a estimaciones más precisas.

---

No existe una regla para descomponer historias de usuario en tareas, pero si tenemos algunas recomendaciones

- Descomponga la HU en tareas técnicas.

- No programe tareas demasiado pequeñas.

- Antes de implementar tareas debes de cero verifique si hay componentes listos que pueda usar.

---

El Product BackLog contiene una lista priorizada y estimada de las
historias de usuario, donde cada item está compuesto por

- Características -> Historias de Usuario
- Defectos
- Trabajo técnico
- Adquisición de conocimiento

    > Spyke (investigar de cosas que el equipo de desarrollo no conoce).
