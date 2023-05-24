---
id: zlmh8y7seozwkunst5lkuht
title: 7-Modelos de despliegue y arquitecturas ágiles
desc: ''
updated: 1684288424560
created: 1684283476807
---

Representa la plataforma o el conjunto de servidores requeridos por una
aplicación de software para ponerla en funcionamiento para ser usada por
los usuarios finales.

# Estilo arquitectural

Con el respondemos a la pregunta: ¿como construir aplicaciones para para ser desplegadas?

# Evolución de los servidores para despliegue de aplicaciones

![Evolution of deployment servers](./assets/University/Desarrollo%20de%20software%20I/1_7-1%20Evolution_deployment_servers.jpg)

---

![Environments of development, testing and deployment](./assets/University/Desarrollo%20de%20software%20I/1_7-2%20Environments_development_testing_deployment.jpg)

# Como calcular el tamaño de los servidores de los nodos para despliegue de aplicaciones

Los factores a tener en cuenta para determinar el tamaño de un servidor:

- Carga (trafico): número de peticiones que depende del número de usuarios concurrentes.
- Tipo de aplicación: cantidad y tipos de recursos que consume.

    > Si la aplicación usa muchos videos, seria recomendable de hacer uso de los servidores de plataformas especializadas en ese tipo de recursos (como YouTube).

- Escalabilidad requerida: crecimiento por demanda.
- Presupuesto

Hay herramientas te permiten simular el tráfico de usuarios en una aplicación web y medir cómo responde el servidor.

    > De esta forma puedes determinar las características de los servidores requeridos.

# Despliegue de aplicaciones (deploy)

Consiste en copiar los archivos de una aplicación en un servidor o nodo (configurado) donde funcionará la aplicación.

Que archivos copiar:

- Programas ejecutables o scripts.
- Librerías requeridas con sus **versiones específicas**.
- Archivos de datos requeridos.
- Bases de datos y drivers de conexión.

> Los procesos de desarrollo ágil intentan que el deploy cada vez sea más automático.

## Estrategias para actualizar el servidor

### Tipo Stand Alone (Stop - Start)

- Se basa en tener un servidor (de producción) sobre el cual se realizan
los cambios, **parar** el servidor, **realizar los cambios** y luego **reiniciar** el servidor.
- Cundo es por primera vez, puede ser un proceso adecuado.
- No se recomienda esta estrategia cuando el servidor esta en producción.
- Al parar el servidor todos los usuarios no tendrán acceso al servicio.

### Rolling upgrade

Se basa en tener una capa de balanceo de la aplicación.Se desconecta un servidor del balanceador, se actualizase y se prueba, si funciona bien, se conecta al balanceador de nuevo y se repite el proceso hasta actualizar todos los servidores.

![Rolling upgrade](./assets/University/Desarrollo%20de%20software%20I/1_7-3%20Rolling_upgrade.jpg)

### Blue/Green

Duplicar temporalmente la infraestructura y desplegar todo a la vez.

![Blue and green](./assets/University/Desarrollo%20de%20software%20I/1_7-4%20Blue_green.jpg)

### Canary

Se aplica a un subconjunto de usuarios o servidores.

- La idea principal es primero desplegar los cambios en un conjunto pequeño de servidores, probar con algunos usuarios y luego continuar el despliegue hacia el resto de usuarios y servidores.
- Sirve como sistema indicador de alerta temprana, si el despliegue
del "canario" falla, el resto de servidores no se ven impactados.

![Canary](./assets/University/Desarrollo%20de%20software%20I/1_7-5%20Canary.jpg)

# Arquitecturas ágiles de software

- Adopción de las arquitecturas

    El desarrollo de software ágil ha sido adaptado por una gran cantidad de empresas en un esfuerzo por reducir costos e incrementar su habilidad para manejar los cambios en un mercado de condiciones cambiantes.

La arquitectura de software ágil es el resultado de la aplicación de las prácticas ágiles.

---

La Arquitectura ágil es una actividad en equipo que se logra iteración tras iteración y que integra estrategia, negocios y tecnología.

## Modelos arquitecturales

Consiste de la especificación de los modelos:

- Arquitectural
- Datos
- Despliegue

## Valores

- Simplicidad
- Sistemas que funcionen
- Mejoramiento continuo
- Trabajo en equipo
- Comunicación
- Diseñada pensando en los atributos de calidad

    - Testeabilidad
    - Mantenibilidad
    - Despliegue
    - Escalabilidad
    - Rendimiento
    - Seguridad
    - Usabilidad

## Documentación

![Documentation](./assets/University/Desarrollo%20de%20software%20I/1_7-6%20Documentation.jpg)