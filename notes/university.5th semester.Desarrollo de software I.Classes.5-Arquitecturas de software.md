---
id: 8uqwdjzlcy09fl5mzbsybcp
title: 5-Arquitecturas de software
desc: ''
updated: 1683819713461
created: 1683588603026
---

# Interfaces de usuario

## Conceptos

- Actor: quien interactúa con la aplicación (persona, otro sistema).

- Rol de usuario: papel que una persona realiza en un sistema.

- Perfil: son las funcionalidades asociadas a un rol.

Es una secuencia de imágenes o prototipos de las interfaces de una App que muestran el conjunto de pantallas o  interfaces de usuario de una aplicación, las cuales representan el **flujo** visual de una aplicación de software.

- Modelo o maqueta del sistema que se desea construir para comprender mejor el problema y sus posibles soluciones

- Se usa para obtener retroalimentación de los clientes

- Son un complemento que ayuda a especificar las funcionalidades de un sistema.

- Presentan la información que se manejará en la aplicación que puede ser de entrada o de salida.

## Reportes en apps

Un reporte presenta información disponible en una aplicación que puede ser útil para los usuarios o clientes de una app.

- Los reportes normalmente es el resultado de hacer una consulta a una base de datos.

- Puede ser el resultado de realizar cálculos simples o complejos.

## Dashboard

Es un reporte que nos permite visualizar datos de manera resumida, mediante la combinación de  imágenes y texto y que pueden servir a una entidad o persona para la toma de decisiones.

> Se espera que sea en tiempo "real".

# Arquitecturas de software

> La complejidad del software crece con el tamaño.

## Visión del sistema

Encapsula las características importantes del diseño de un sistema.

## Estructura del software

La arquitectura describe las múltiples facetas de la estructura del software, el comportamiento, el diseño, la codificación y la documentación.

## Componentes y sus relaciones

Una arquitectura es la organización fundamental de un sistema encarnada en sus componentes, sus relaciones entre sí y con el medio en que se desarrolla, así como los principios rectores de su diseño y evolución.

## Atributos de calidad

Representan un grupo de principios y restricciones sobre cómo las soluciones software **deben** ser construidas dentro de un ámbito dado.

1. Testeabilidad

    Se debe diseñar sus componentes para que sean fácilmente probados.

2. Mantenibilidad

    Facilidad para efectuarle cambios.

3. Desplegabilidad

    Facilidad con la que se puede pasar de desarrollo a producción.

4. Escalabilidad

    Capacidad para manejar aumentos de carga sin disminuir los tiempos de respuesta y facilidad para crecer.

5. Evolución (releasability)

    Fáciles de entender para facilitar la generación de nuevas versiones.

6. Rendimiento

    Cuantificación de la velocidad con la que realiza una tarea o proceso.

7. Interoperabilidad

    Facilidad para intercambiar información con otras apps.

# Arquitectura de aplicaciones web

Describe los componentes y las interacciones entre el front-end y el back-end.

- Puede ser vista como la forma de organizar el código de la aplicación, diseño y actividades de desarrollo y documentación.

- Se estructura para que múltiples tecnologías funcionen simultáneamente.

## ¿Cómo funcionan?

En las aplicaciones web, en esencia, hay dos programas que se ejecutan al mismo tiempo, por tanto, la arquitectura debe ser pensada en términos del cliente/servidor:

- Cliente: el código que está en el navegador y responde a alguna entrada del usuario.

- Servidor: el código que está en el servidor y responde a las solicitudes HTTP o HTTPS.

# Tipos de estilos arquitecturales

- Monolíticas

    ![Monolitic architecture](./assets/University/Desarrollo%20de%20software%20I/1_5-1%20Monolitic_architecture.jpg)

- Basadas en api

    ![API architecture](./assets/University/Desarrollo%20de%20software%20I/1_5-2%20API_architecture.jpg)

- Micro servicios

    ![Microservices architecture](./assets/University/Desarrollo%20de%20software%20I/1_5-3%20Microservices_architecture.jpg)

- Micro front-ends

    ![Micro front-ends architecture](./assets/University/Desarrollo%20de%20software%20I/1_5-4%20Micro_front-ends_architecture.jpg)

> Vemos una tendencia a descomponer, generando aislamiento y por lo tanto modularidad en una app.