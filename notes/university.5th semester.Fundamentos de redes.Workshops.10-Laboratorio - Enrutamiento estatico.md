---
id: 3lfg5g3hkwmn136eguta7c4
title: 10-Laboratorio - Enrutamiento estatico
desc: ''
updated: 1687652219779
created: 1685818905087
---

1. Configuración de parámetros básicos.

	- `S1`, `S2`, `R1`, `R2` y `R3`.

		- Contraseña modo privilegiado: class.

		- Contraseña de consola: cisco.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

2. Configuración de acceso por SSH.

	- `S1`, `S2`, `R1`, `R2` y `R3`.

		- Dominio: `redes.com`.

		- Nombre de usuario: Admin.

		- Contraseña del usuario: Cisco123.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-acceso-por-ssh]]

3. Configure el direccionamiento para todos los dispositivos de acuerdo con la tabla de direccionamiento.

	- `R1`, `R2` y `R3`.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-direccionamiento]]

4. Configurar las rutas estáticas estándar y flotantes.

    > Configuración global.

    - `R1`.

        - `ip route 192.168.35.0 255.255.255.0 192.168.240.2`.
        - `ip route 192.168.35.0 255.255.255.0 192.168.240.6 2`.

            > El dos agregado corresponde a la distancia administrativa, como es una enlace de  respaldo tiene que ser mayor a 1 (que es la del enlace directo).

    - `R2`.

        - `ip route 192.168.25.0 255.255.255.0 192.168.240.1`.
        - `ip route 192.168.25.0 255.255.255.0 192.168.240.9 2`.

    - `R3`.

        - `ip route 192.168.35.0 255.255.255.0 192.168.240.10`.
        - `ip route 192.168.25.0 255.255.255.0 192.168.240.5`.

5. Configurar una ruta predeterminada.

    > Configuración global.

    - `R2`.

        - `ip route 0.0.0.0 0.0.0.0 200.31.12.2`.

    - `R1`.

        - `ip route 0.0.0.0 0.0.0.0 192.168.240.2`.

            > Con esta red tenemos redundancia con la `192.168.35.0 255.255.255.0 192.168.240.2`, así que la podemos eliminar.

        - `ip route 0.0.0.0 0.0.0.0 192.168.240.6 2`.

    - `R3`

        - `ip route 0.0.0.0 0.0.0.0 192.168.240.10`.
