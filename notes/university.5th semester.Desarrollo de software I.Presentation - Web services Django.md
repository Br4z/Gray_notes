---
id: 8mo9hrwcln3t8b1j7u9adf1
title: Presentation - Web services Django
desc: ''
updated: 1685490632120
created: 1684525289544
---

> Aunque vayamos a tratar los web services con Django (para la parte práctica), primero tenemos que verlos en general.

## Definición

Cuando hablamos de web services, hacemos referencia a la tecnología que utiliza un conjunto de protocolos y estándares (abiertos) que permiten la comunicación entre aplicaciones o sistemas diferentes a través de la web.

**NO** importa:

- Las diferencias de los lenguajes de programación.
- La plataforma.

> Las organizaciones **OASIS** (Organization for the Advancement of Structured Information Standards) y **W3C** (World Wide Web Consortium) son los comités responsables de la arquitectura y reglamentación de los servicios Web.

El W3C define un servicio web como:

Un servicio web es un sistema software diseñado para soportar la interacción máquina-a-máquina, a través de una red, de forma interoperable. Cuenta con una interfaz descrita en un formato procesable por un equipo informático (específicamente en **WSDL**), a través de la que es posible interactuar con el mismo mediante el intercambio de mensajes **SOAP**, típicamente transmitidos usando serialización **XML** sobre **HTTP** conjuntamente con otros estándares web.

### Glosario

- XML (eXtensible Markup Language): es un metalenguaje que permite definir lenguajes de marcas desarrollado por el **W3C**.

    > A diferencia de otros lenguajes, **XML** da soporte a bases de datos, siendo útil cuando varias aplicaciones deben comunicarse entre sí o integrar información.

- WSDL (Web Services Description Language): es un formato del Extensible Markup Language (XML) que se utiliza para describir servicios web (WS).

    > Con la información que provee, el cliente puede comprender qué funciones puede ejecutar en el servidor a través del servicio web.

- SOAP (Simple Object Access Protocol): es un protocolo estándar que define cómo dos objetos en diferentes procesos pueden comunicarse por medio de intercambio de datos **XML**.

- UDDI (Universal Description, Discovery and Integration): es un estándar XML para describir, publicar y encontrar servicios web. Es un directorio donde las compañías pueden registrar y buscar servicios web.

    > Podemos utilizarlo para comprobar qué servicios web están disponibles.

## Características

### Ventajas

- Aportan interoperabilidad entre aplicaciones de software independientemente de sus propiedades o de las plataformas sobre las que se instalen.
- Los servicios Web fomentan los estándares y protocolos basados en texto, que hacen más fácil acceder a su contenido y entender su funcionamiento.
- Permiten que servicios y software de diferentes compañías ubicadas en diferentes lugares geográficos puedan ser combinados fácilmente para proveer servicios integrados (es **distribuido**).

### Desventajas

- Seguridad

    Hay que implementar un gran número de restricciones, en caso contrario no podemos asegurar la integridad de la información.

    - Autenticación y autorización.
    - Vulnerabilidades en la capa de transporte (en el caso de usar HTTP).
    - Validación de datos y ataques de inyección.
    - Manejo inadecuado de errores y excepciones: un manejo inadecuado de los errores puede dar lugar a condiciones de error reveladoras o mensajes de error detallados que pueden ser explotados.

- Transacciones

    En el contexto de los servicios web, una transacción se refiere a una unidad de trabajo lógica y coherente que involucra múltiples operaciones o acciones. En términos generales, una transacción representa una secuencia de operaciones que se considera una unidad indivisible, lo que implica que todas las operaciones deben ejecutarse correctamente o ninguna de ellas se debe ejecutar en absoluto.

    > Para el manejo de ellas es recomendable usar herramientas especializadas.

## ¿Cómo funciona?

1. El proveedor de servicios envía al publicador del servicio un fichero **WSDL** con la definición del servicio web.

2. El que pide el servicio contacta con el publicador y descubre quién es el proveedor (protocolo **WSDL**) y contacta con el proveedor (protocolo **SOAP**)

3. El proveedor valida la petición de servicio y envía el dato estructurado en formato **XML** utilizando el protocolo SOAP.

4. El fichero **XML** es validado de nuevo por el que pide el servicio, utilizando un fichero **XSD** (XML Schema Definition) para interpretarlo. La información resultante se envía al software y estará lista para ser procesada.

## Esquema (WSDL)

- Tipos de datos (`<types>`): esta sección define los tipos de datos usados en los mensajes.

    - Se utilizan los tipos definidos en la especificación de esquemas XML.

- Mensajes (`<message>`): aquí definimos los elementos de mensaje.

    - Cada mensaje puede consistir en una serie de partes lógicas.
    - Las partes pueden ser de cualquiera de los tipos definidos en la sección anterior.

- Tipos de puerto (`<portType>`): con este apartado definimos las operaciones permitidas y los mensajes intercambiados en el Servicio.

- Bindings (`<binding>`): especificamos los protocolos de comunicación usados.

- Servicios (`service`): conjunto de puertos y dirección de los mismos.

    > Esta parte final hace referencia a lo aportado por las secciones anteriores.

> Con estos elementos no sabemos qué hace un servicio, pero sí disponemos de la información necesaria para interactuar con él (funciones, mensajes de entrada/salida, protocolos...).

## Ejemplos

### Amazon

Ademá de contar con servicios para su propia empresa, como la posibilidad de hacer consultas simples de los catálogos de Amazon y sitios web de ecommerce que operan en asociación con Amazon a través de su programa de afiliados. También tienen Amazon Web Services (AWS), servicio que brinda acceso a la infraestructura técnica de Amazon.

> AWS se puede implementar utilizando los tipos de servicios web **SOAP** o **REST**, pero la mayoría de las implementaciones de AWS siguen el segundo enfoque.

### Google

proporciona una interfaz de servicio web basada en **SOAP** a su motor de búsqueda público para acceder a sus recursos en un modelo de servicios web. De hecho, este web service se denomina API web de Google. Dicha API puede ser usada para:

- Ejecutar búsquedas con el motor de Google.
- Recibir los resultados de una búsqueda.
- Sugerencias ortográficas.
- Obtención de una página almacenada en caché.

## Ejemplo practico

En general se caracterizan por poder ser desarrolladas utilizando prácticamente cualquier lenguaje de programación y admiten una variedad de formatos de datos. El único requisito es que se alineen con los siguientes seis principios de diseño de REST:

1. Interfaz uniforme: todas las solicitudes de API para el mismo recurso deben tener el mismo aspecto, sin importar de dónde provenga la solicitud. La API REST debe garantizar que el mismo dato, como el nombre o la dirección de correo electrónico de un usuario, pertenezca a un solo identificador uniforme de recursos (URI). Los recursos no deben ser demasiado grandes, pero deben contener toda la información que el cliente necesite.

2. Desacoplamiento cliente-servidor: en el diseño de API REST, las aplicaciones de cliente y servidor deben ser completamente independientes entre sí. La única información que debe conocer la aplicación del cliente es el URI del recurso solicitado; no puede interactuar con la aplicación del servidor de ninguna otra manera. De manera similar, una aplicación de servidor no debería modificar la aplicación del cliente además de pasarla a los datos solicitados a través de HTTP.

3. Sin estado: las API REST no tienen estado, lo que significa que cada solicitud debe incluir toda la información necesaria para procesarla. En otras palabras, las API REST no requieren ninguna sesión del lado del servidor. Las aplicaciones de servidor no pueden almacenar ningún dato relacionado con la solicitud de un cliente.

4. Capacidad de caché: cuando sea posible, los recursos deben almacenarse en la memoria caché en el lado del cliente o del servidor. Las respuestas del servidor también deben contener información sobre si se permite el almacenamiento en caché para el recurso entregado. El objetivo es mejorar el rendimiento en el lado del cliente, mientras aumenta la escalabilidad en el lado del servidor.

5. Arquitectura del sistema en capas: en las API REST, las llamadas y respuestas pasan por diferentes capas. Como regla general, no asuma que las aplicaciones cliente y servidor se conectan directamente entre sí. Puede haber varios intermediarios diferentes en el bucle de comunicación. Las API REST deben diseñarse de modo que ni el cliente ni el servidor puedan saber si se comunican con la aplicación final o con un intermediario.

6. Código bajo demanda (opcional): las API REST generalmente envían recursos estáticos, pero en ciertos casos, las respuestas también pueden contener código ejecutable (como los subprogramas de Java). En estos casos, el código solo debe ejecutarse bajo demanda.

Las API REST se comunican mediante solicitudes HTTP para realizar funciones de bases de datos estándar como crear, leer, actualizar y eliminar registros (también conocidas como **CRUD**) dentro de un recurso. Por ejemplo, una API REST usaría una solicitud `GET` para recuperar un registro, una solicitud `POST` para crearlo, una solicitud `PUT` para actualizar un registro y una solicitud `DELETE` para eliminarlo. Todos los métodos HTTP se pueden utilizar en llamadas a API. Una API REST bien diseñada es similar a un sitio web que se ejecuta en un navegador web con funcionalidad HTTP incorporada.
