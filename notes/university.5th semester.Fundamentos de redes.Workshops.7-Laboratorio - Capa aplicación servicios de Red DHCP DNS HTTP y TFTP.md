---
id: vco6i5jj04eweri921if8ox
title: 7-Laboratorio - Capa aplicación servicios de Red DHCP DNS HTTP y TFTP
desc: ''
updated: 1683496352477
created: 1683491010855
---

1. Monte los dispositivos y el cableado de red tal como se muestra en la topología.

    >  Configuración global.

    - R1

        1. `interface g 0/0`
        2. `ip address 192.168.25.1 255.255.255.128`
        3. `no shutdown`
        4. `ip default-gateway 192.168.25.1`

    - S1

        1. `interface vlan 1`
        2. `ip address 192.168.25.10 255.255.255.128`
        3. `no shutdown`
        4. `ip default-gateway 192.168.25.1`

2. Configuración de parámetros básico en switch y Router.

    1. Nombre según la tabla de direccionamiento

        - R1

            > Configuración global.

            - `hostname R1`

        - S1

            > Configuración global.

            - `hostname R1`

    2. Asigne "class" como la contraseña de enable y asigne "cisco" como la contraseña de consola.

        - enable

            > Configuración de consola.

            - `enable secret class`

        - consola

            > Configuración de consola (`line console 0`).

            - `pass cisco`
            - `login`

    3. Mensaje de bienvenida con la palabra "Advertencia".

        > Configuración global.

        - `banner motd +Advertencia: estas entrando a el dispositivo <device name>+`

    4. Cifre todas las contraseñas de texto no cifrado

        > Configuración global.

        `service password-encription`

3. Configuración de acceso por SSH para el Router

    > Configuración global.

    - `ip domain-name cisco.com`
    - `username Admin secret Cisco123`
    - `crypto key generate rsa` (1024 bits)
    - `line vty 0 4`

    > Configuración de consola (a la que nos debió cambiar el comando `line vty`).

    - `transport input ssh`
    - `login local`

5 Guardar la configuración en la NVRAM: `write memory`

    > Privilegiado.
