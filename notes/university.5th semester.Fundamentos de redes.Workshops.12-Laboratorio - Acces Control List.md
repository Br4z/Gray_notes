---
id: 4gsnv69mdq9zsfb73nztixr
title: 12-Laboratorio - Acces Control List
desc: ''
updated: 1687652251890
created: 1686155275292
---

1. Configuración de parámetros básicos.

	- `S1`, `S2`, `R1`, `R2` y `R3`.

		- Contraseña modo privilegiado: brandon.

		- Contraseña de consola: calderon.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

2. Configuración de acceso por SSH.

	- `S1`, `S2`, `R1`, `R2` y `R3`.

		- Dominio: `cisco.com`.

		- Nombre de usuario: Admin.

		- Contraseña del usuario: 2125974.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-acceso-por-ssh]]

3. Configure el direccionamiento para todos los dispositivos de acuerdo con la tabla de direccionamiento.

	- `R1`, `R2` y `R3`.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-direccionamiento]]

4. Configurar enrutamiento dinámico con OSPF.

	> Configuración global.

	- `R2`.

		- `ip route 0.0.0.0 0.0.0.0 200.31.12.2`.

	- `router ospf 10`.
	- `router-id <id>`.
	- `net <red ip> <wildcard mask> area 0`.

	- `R1`.

		- `router-id 1.1.1.1`
		- `network 192.168.25.0 0.0.0.31 area 0`.
		- `network 192.168.25.224 0.0.0.3 area 0`.
		- `network 192.168.25.228 0.0.0.3 area 0`.
		- `passive-interface g0/0`.

	- `R2`.

		- `router-id 2.2.2.2`
		- `network 192.168.25.32 0.0.0.31 area 0`.
		- `network 192.168.25.224 0.0.0.3 area 0`.
		- `network 192.168.25.232 0.0.0.3 area 0`.
		- `passive-interface g0/0`.
		- `default-information originate.`

	- `R3`.

		- `router-id 3.3.3.3`
		- `network 192.168.25.192 0.0.0.31 area 0`.
		- `network 192.168.25.228 0.0.0.3 area 0`.
		- `network 192.168.25.232 0.0.0.3 area 0`.
		- `passive-interface g0/0`.

5. Configuración de listas de control de acceso.

	Antes de ir con los puntos, hallemos algunos datos de cada red.

	$$
	\begin{array}{lllll}
		\neg &255.&255.&255.&11100000 \\
		=    &0.  &0.  &0.  &00011111
	\end{array} \\[10 pt]
	$$

	- `R1`.

		$$
		\begin{array}{lllll}
			  &192.&168.&25.  &00000000 \\
			  &0.  &0.  &0.   &00011111 \\
			= &192.&168.&25.&00011111 = 192.168.25.31
		\end{array}
		$$

		- IP broadcast: 192.168.25.31/27
		- IP último host: 192.168.25.30/27

	- `R2`.

		$$
		\begin{array}{lllll}
			  &192.&168.&25.  &00100000 \\
			  &0.  &0.  &0.   &00011111 \\
			= &192.&168.&25.&00111111 = 192.168.24.63
		\end{array}
		$$

		- IP broadcast: 192.168.25.63/27
		- IP último host: 192.168.25.62/27

	- `R3`.

		$$
		\begin{array}{lllll}
			  &192.&168.&25.  &11000000 \\
			  &0.  &0.  &0.   &00011111 \\
			= &192.&168.&25.&11011111 = 192.168.24.223
		\end{array}
		$$

		- IP broadcast: 192.168.25.223/27
		- IP último host: 192.168.25.222/27

	> Para iniciar por shh `ssh -l Admin <ip>`.

	1. Configure una ACL **estándar** que bloquee el tráfico de la primera mita de la red LAN de `R2`  a la red LAN de `R1`, pero que la segunda mita de la red tenga acceso.

		Las listas ACL **estándar** se deben configurar en el dispositivo más cercano al destino.

		La wildcard que describe a la primera mitad de la red LAN de `R2` es:

		$$
		\begin{array}{lllll|l}
			  &192.&168.&25.  &001 &00000 \\
			  &0.  &0.  &0.   &111 &00000 \\
			= &0.  &0.  &0.   &000 &01111 = 0.0.0.15
		\end{array}
		$$

		> La primera parte de la red va de la forma `00000`, `00001`, `00010`... `01111` y la segunda va de la forma `10000`, `10001`, `10010`... `11111`.

		> Configuración global.

		- `R1`.

			- `acces-list 2 deny host 192.168.25.32 0.0.0.15`.
			- `acces-list 2 permit any`.
			- `int g0/0`.
			- `ip access-group 2 out`.

				> Es out porque el tráfico sale de `R2` a su LAN.

	2. Configure una ACL que permita el acceso a la VTY de los 3 routers únicamente el último PC de cada red LAN.

		> Configuración global.

		- `R1`, `R2` y `R3`.

			- `acces-list 1 permit host 192.168.25.30`.
			- `acces-list 1 permit host 192.168.25.63`.
			- `acces-list 1 permit host 192.168.25.222`.
			- `line vty 0 4`.

			> Configuración de consola (a la que nos debió cambiar el comando `line vty`).

			- `access-class 1 in`.
