---
id: vco6i5jj04eweri921if8ox
title: 7-Laboratorio - Capa aplicación servicios de Red DHCP DNS HTTP y TFTP
desc: ''
updated: 1687734525185
created: 1683491010855
---

1. Monte los dispositivos y el cableado de red tal como se muestra en la topología.

    - R1

		- Tipo de interfaz: gigabitEthernet.

		- Identificador de interfaz: `0/0`.

		- Dirección IP: `192.168.25.1 255.255.255.128`.

		- Puerta de enlace predeterminada: `192.168.25.1`.

    - S1

		- Tipo de interfaz: vlan.

		- Identificador de interfaz: `1`.

		- Dirección IP: `192.168.25.10 255.255.255.128`.

		- Puerta de enlace predeterminada: `192.168.25.1`.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuracion-de-direccionamineto]]

2. Configuración de parámetros básicos en switch y Router.

	- Contraseña modo privilegiado: class.

	- Contraseña de consola: cisco.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

3. Configuración de acceso por SSH para el Router

	- Dominio: `cisco.com`.

	- Nombre de usuario: Admin.

	- Contraseña del usuario: Cisco123.

    ![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-acceso-por-ssh]]

5 Guardar la configuración en la NVRAM: `write memory`

    > Privilegiado.
