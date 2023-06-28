---
id: ewfvoyu1tuocpq7dtugyp78
title: 14-Laboratorio - DHCP Y NAT-PAT
desc: ''
updated: 1687741363713
created: 1686757394987
---

1. Configuración de parámetros básico R2.

	- Contraseña modo privilegiado: 2125974.

	- Contraseña de consola: cisco.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

2. Configuración de acceso por SSH en R2.

	- Dominio: `cisco.com`.

	- Nombre de usuario: Admin.

	- Contraseña del usuario: Cisco123.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-acceso-por-ssh]]

3. Configuración de opciones de seguridad puertos switch S2.

	1. Antes de ir con las opciones de seguridad configuraremos las vlans.

		1. `vlan <vlan number>`.

		2. `name <vlan name>`.

	2. Configuracion de los puertos de acceso.

		1. `interface range <interface type> <interface range>`.

		2. `switchport mode access`.

		3. `switchport access vlan <vlan number>`.

	3. Configuracion de puerto troncal.

		1. `interface gigabitEthernet 0/1`.

		2. `switchport mode access trunk`.

		3. `switchport trunk native vlan 199`.

		4. `switchport trunk allowed vlan 100,101,102,120,199`.

	4. Desabilitacion de puertos sin usar.

		1. `interface range <interface type> <interface range>`.
		2. `shutdown`.

		> La otra opcion es deshabilitar todos los puertos y luego habilitar los que se van a usar.

	- Tipo de interfaz: fastEthernet.

	- Identificador de interfaz: `0/1-24` (rango).

	- MAC por puerto: 2.

	- `mac-address` mode: sticky.

	- `violation` mode: restrict.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-opciones-de-seguridad]]

4. Configure el direccionamiento para todos los dispositivos de acuerdo con la tabla de direccionamiento.

	> Configuración global.

	- `R1` y `R3`.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-direccionamiento]]

	- `R2`.

		- `interface gigabitEthernet 0/0.<vlan number>`.

		- `encapsulation dot1Q <vlan number>`.

			> Si es la nativa se le pone `native` al final.

		- `ip add <IP> <mask>`.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-direccionamiento]]

	- `S1`.

		- `int vlan 1`.

		- `ip add`.

	- `S2`.

		- `int vlan 120`.

		- `ip add 192.168.25.130 255.255.255.224`.

		- `no shutdown`.

		> Modo privilegiado.

		- `ip default-gateway 192.168.25.129`.
