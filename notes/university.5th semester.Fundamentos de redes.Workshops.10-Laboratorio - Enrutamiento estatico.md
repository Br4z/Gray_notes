---
id: 3lfg5g3hkwmn136eguta7c4
title: 10-Laboratorio - Enrutamiento estatico
desc: ''
updated: 1685907396887
created: 1685818905087
---

1. Configuración de parámetros básicos.

    - `S1`, `S2`, `R1`, `R2` y `R3`.

        > Configuración global.

        1. `hostname <devicename>`.
        2. `no ip doamin-lookup`.
        3. `enable secret class`.
        4. Consola.

            > Configuración de consola (`line console 0`).

            - `pass cisco`
            - `login`

        5. `banner motd +Warning: you're entering in the device <device name>+`.
        6. `service password-encription`.

2. Configuración de acceso por SSH.

    - `S1`, `S2`, `R1`, `R2` y `R3`.

        > Configuración global.

        - `ip domain-name redes.com`.
        - `username Admin secret Cisco123`.
        - `crypto key generate rsa` (1024 bits).
        - `line vty 0 4`.

        > Configuración de consola (a la que nos debió cambiar el comando `line vty`).

        - `transport input ssh`.
        - `login local`.

3. Configure el direccionamiento para todos los dispositivos de acuerdo con la tabla de direccionamiento.

    - `R1`, `R2` y `R3`.

        > Configuración global.

        - `int gigabitEthernet  <interface identifier>`.
        - `ip add <ip> <mask>`.
        - `description <description>`.
        - `no sh`.

            > Puede dar error si no hemos configurado las IP de los otros routers.

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