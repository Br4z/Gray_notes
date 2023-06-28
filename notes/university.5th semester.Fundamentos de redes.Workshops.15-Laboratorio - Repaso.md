---
id: 807lq6fmkrk9z45k6x2hzs7
title: 15-Laboratorio - Repas
desc: ''
updated: 1687753174347
created: 1687741712935
---

1. Configuración de parámetros básico R2.

	- Contraseña modo privilegiado: 2125974.

	- Contraseña de consola: cisco.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

2. Configuración de acceso por SSH en R2.

	1. Configuracion general.

		- Dominio: `cisco.com`.

		- Nombre de usuario: Admin.

		- Contraseña del usuario: P4ssw0rd123.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-acceso-por-ssh]]

	2. Configure una ACL para acceso SSH a los switch y routers donde solo la VLAN de gestión tenga acceso al VTY.

		> Configuracion global.

		- `access-list 1 permit 192.168.25.128 0.0.0.31`.

			> `192.168.25.128` es la red asociada a la vlan de gestion.

		> > Configuración de conexiones virtuales vty (0 4).

		- `access-class 1 in`.

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

		2. `switchport mode trunk`.

		3. `switchport trunk native vlan 15`.

		4. `switchport trunk allowed vlan 10,11,12,13,14,15`.

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

		- `ip add 192.168.25.30 255.255.255.224`.

		- `no shutdown`.

		- `ip default-gateway 192.168.25.1`

			> La primera IP de la red.

	- `S2`.

		- `int vlan 14`.

		- `ip add 192.168.25.130 255.255.255.224`.

		- `no shutdown`.

		> Modo privilegiado.

		- `ip default-gateway 192.168.25.129`.

	- `S3`.

		- `int vlan 1`.

		- `ip add 192.168.25.222 255.255.255.224`.

		- `no shutdown`.

		> Modo privilegiado.

		- `ip default-gateway 192.168.25.193`.

5. Configurar enrutamiento dinámico con OSPF.

	> Configuración global.

	- `router ospf 10`.

	- `router-id <router id>`.

	- `R1`.

		- `net 192.168.25.0 0.0.0.31 area 0`.

		- `net 192.168.25.224 0.0.0.3 area 0`.

		- `net 192.168.25.228 0.0.0.3 area 0`.

		- `passive-interface gigabitEthernet 0/0`.

	- `R2`.

		- `net 192.168.25.32 0.0.0.31 area 0`.

		- `net 192.168.25.64 0.0.0.31 area 0`.

		- `net 192.168.25.96 0.0.0.31 area 0`.

		- `net 192.168.25.128 0.0.0.31 area 0`.

		- `net 192.168.25.160 0.0.0.31 area 0`.

		- `net 192.168.25.224 0.0.0.3 area 0`.

		- `net 192.168.25.232 0.0.0.3 area 0`.

		- `passive-interface gigabitEthernet 0/0`.

		- `default-information originate`.

		> Modo privilegiado.

		- `ip route 0.0.0.0 0.0.0.0  200.31.12.2`.

	- `R3`.

		- `net 192.168.25.0 0.0.0.31 area 0`.

		- `net 192.168.25.224 0.0.0.3 area 0`.

		- `net 192.168.25.228 0.0.0.3 area 0`.

		- `passive-interface gigabitEthernet 0/0`.

6. Configure la NAT/PAT.

	> Configuración global.

	- `R2`.

		- `ip nat inside source static 192.168.25.98 200.123.226.1`.

			> Traduce la IP publica a la privada.

		Aplicar `ip nat inside` en todas las interfaces expto en la de salida `gigabitEthernet 0/3/0` (`ip nat outside`).

		- `access-list 2 permit 192.168.25.0 0.0.0.255`.

		- `ip nat inside source list 2 interface g0/3/0 overload`.

			> Permitir toda la red.

7. Configuracion DHCP.

	> Configuración global.

	- `R2`.

		- `ip dhcp excluded-address 192.168.25.1 192.168.25.5`.

		- `ip dhcp excluded-address 192.168.25.33 192.168.25.37`.

		- `ip dhcp excluded-address 192.168.25.65 192.168.25.69`.

		- `ip dhcp excluded-address 192.168.25.97 192.168.25.101`.

		- `ip dhcp excluded-address 192.168.25.193 192.168.25.197`.

		- `ip dhcp pool DHCP-LAN1`.

		- `net 192.168.25.0 255.255.255.224`.

		- `default-router 192.168.25.1`.

		- `dns-server 192.168.25.98`.

		- `ip dhcp pool DHCP-LAN3`.

		- `net 192.168.25.192 255.255.255.224`.

		- `default-router 192.168.85.193`.

		- `dns-server 192.168.25.98`.

		- `ip dhcp pool DHCP-VLAN11`.

		- `net 192.168.25.32 255.255.255.224`.

		- `default-router 192.168.25.33`.

		- `dns-server 192.168.25.98`.

		- `ip dhcp pool DHCP-VLAN12`.

		- `net 192.168.25.64 255.255.255.224`.

		- `default-router 192.168.25.33`.

		- `dns-server 192.168.25.98`.

	- `R1` y `R3`.

		- `interface gigabitEthernet 0/0`.

		- `ip helper-address 192.168.25.33`.
