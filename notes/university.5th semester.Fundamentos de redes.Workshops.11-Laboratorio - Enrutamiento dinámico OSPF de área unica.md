---
id: 8rvo83815ihwg1cozor1hll
title: 11-Laboratorio - Enrutamiento dinámico OSPF de área unica
desc: ''
updated: 1687652180359
created: 1685905099458
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

4. Configurar enrutamiento dinámico con OSPF.

    > Configuración global.

    - `router ospf 10`.
    - `router-id <id>`
    - `net <red ip> <wildcard mask> area 0`.

    - `R1`

        - `router-id 1.1.1.1`
        - `network 192.168.25.0 0.0.0.31 area 0`.
        - `network 192.168.25.224 0.0.0.3 area 0`.
        - `network 192.168.25.228 0.0.0.3 area 0`.
        - `passive-interface g0/0`.

    - `R2`

        - `router-id 2.2.2.2`
        - `network 192.168.25.32 0.0.0.31 area 0`.
        - `network 192.168.25.224 0.0.0.3 area 0`.
        - `network 192.168.25.232 0.0.0.3 area 0`.
        - `passive-interface g0/0`.

    - `R3`

        - `router-id 3.3.3.3`
        - `network 192.168.25.228 0.0.0.3 area 0`.
        - `network 192.168.25.232 0.0.0.3 area 0`.

5. Configurar una ruta predeterminada.

    > Configuración global.

    - `R2`

        - `ip route 0.0.0.0 0.0.0.0 200.31.12.2`.
        - `router ospf 10`.
        - `default-information originate`.
