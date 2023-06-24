---
id: 8rvo83815ihwg1cozor1hll
title: 11-Laboratorio - Enrutamiento dinámico OSPF de área unica
desc: ''
updated: 1685917842268
created: 1685905099458
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
