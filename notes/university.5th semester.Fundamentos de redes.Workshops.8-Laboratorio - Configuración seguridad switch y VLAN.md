---
id: hfslkx9vn7il6mgd29h4ejk
title: 8-Laboratorio - Configuración seguridad switch y VLAN
desc: ''
updated: 1686155220882
created: 1684516521186
---

1. Configuración de parámetros básicos en switch:

    1. Nombre según la tabla de direccionamiento

        > Configuración global.

        - `hostname <name>`

    2. Desactive la búsqueda de DNS.

        > Configuración global.

        - `no ip domain-lookup`

    3. Asigne su nombre en minúscula como la contraseña de enable y asigne su apellido en minúscula como la contraseña de consola.

        - enable

            > Configuración de consola.

            - `enable secret brandon`

        - consola

            > Configuración de consola (`line console 0`).

            - `pass calderon`
            - `login`

    4. Mensaje de bienvenida con la palabra "Advertencia".

        > Configuración global.

        - `banner motd +Warning: you're entering in the device <device name>+`

    5. Cifre todas las contraseñas de texto no cifrado.

        > Configuración global.

        `service password-encription`

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

        - `int range fastEthernet 0/1-24`
        - `switchport port-security`
        - `switchport port-security maximum 2`

            > Configure máximo 2 MAC permitidas por puerto.

        - `switchport port-security mac-address sticky`

            > Agregar todas las direcciones MAC seguras que se detectan dinámicamente en un puerto.

        - `switchport port-security violation restrict`

            > Configure la opción de violación de seguridad para que se envíe un mensaje al log, pero que no deshabilite el puerto.
