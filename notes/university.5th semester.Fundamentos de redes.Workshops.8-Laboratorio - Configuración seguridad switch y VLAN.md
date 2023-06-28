---
id: hfslkx9vn7il6mgd29h4ejk
title: 8-Laboratorio - Configuración seguridad switch y VLAN
desc: ''
updated: 1687738276820
created: 1684516521186
---

1. Configuración de parámetros básicos en switch:

	- Contraseña modo privilegiado: brandon.

	- Contraseña de consola: calderon.

	![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-parámetros-básicos]]

2. Crear redes VLAN y asignar puertos de switch.

    1. Crear las VLAN en los switches de acuerdo a la tabla VLAN.

        > Configuración global.

        - `vlan <vlan number>`
        - `name <vlan name>`

    2. Verifique las vlans creadas.

        > Privilegiado.

        - `show vlan`

    3. Asignar las VLAN a las interfaces de acceso del switch correctas de acuerdo a la tabla.

        > Configuración global.

        - S1 y S2

            - `int range fastEthernet 0/<start>-<end>`
            - `switchport mode access`
            - `switchport access vlan <vlan number>`

    4. Configurar un enlace troncal 802.1Q entre los switches.

        > Configuración global.

        - S1 y S2

            - `int gigabitEthernet 0/1`
            - `switchport mode trunk`
            - `switchport trunk native vlan 99`
            - `switchport trunk allowed vlan 10,20,30,100`

        - S0

            - `int range gigabitEthernet 0/1-2`
            - `switchport mode trunk`
            - `switchport trunk native vlan 99`
            - `switchport trunk allowed vlan 10,20,30,100`

3. Configure el direccionamiento para todos los dispositivos de acuerdo con la tabla de direccionamiento.

    - S0, S1 y S2

        - `int vlan 100`
        - `ip add <ip> <mask>`
        - `no shutdown`

4. Configuración de opciones de seguridad en los puertos switch.

    - S1 y S2

		- Tipo de interfaz: fastEthernet.

		- Identificador de interfaz: `0/1-24` (rango).

		- MAC por puerto: 2.

		- `mac-address` mode: sticky.

		- `violation` mode: restrict.

		![[Guía | university.5th semester.Fundamentos de redes.Workshops.Guía de configuraciones#Configuración-de-opciones-de-seguridad]]
