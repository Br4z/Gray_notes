---
id: mqh6gubgy99cssa3l7ad8qw
title: Guía de configuraciones
desc: ''
updated: 1687737379890
created: 1687644292943
---

## Configuración de parámetros básicos

> Configuración global.

1. `hostname <device name>`.

2. `no ip doamin-lookup`.

	> Desactivar la búsqueda DNS.

3. `enable secret <password>`.

	> Contraseña del modo privilegiado.

4. Consola.

	> Configuración de consola (`line console 0`).

	- `password <password>`.
	- `login`.

5. `banner motd <opening character>Warning: you're entering in the device <device name><ending character>`.

6. `service password-encription`.

## Configuración de acceso por SSH

> Configuración global.

1. `ip domain-name <domain>`.

2. `username Admin secret <password>`.

3. `crypto key generate rsa` (1024 bits).

4. `line vty 0 4`.

	> Configuración de conexiones virtuales vty.

5. `transport input ssh`.

6. `login local`.

## Configuración de direccionamiento

> Configuración global.

1. `interface <interface type> <interface identifier>`.

2. `ip add <IP> <mask>`.

3. `description <description>`.

4. `no shutdown`.

5. `ip <IP>`.

## Configuración de opciones de seguridad

1. `interface <interface type> <interface identifier>`.

2. `switchport port-security`.

3. `switchport port-security maximum <number>`.

4. `switchport port-security mac-address <mode>`.

	- sticky: agregar todas las direcciones MAC (como seguras) que se detectan dinámicamente en un puerto.

5. `switchport port-security violation <mode>`.

	- restrict: envía un mensaje al log, pero no se deshabilita el puerto.

	- shutdown: se deshabilita el puerto.

	- protect: deniega sin notificar.
