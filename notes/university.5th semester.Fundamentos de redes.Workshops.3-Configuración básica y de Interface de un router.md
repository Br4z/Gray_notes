---
id: eglnvulzytrna53s3cp0u1c
title: 3-Configuración básica y de Interface de un router
desc: ''
updated: 1680718427111
created: 1680121580927
---

1. Asigne el nombre `R1`

    > Configuración global.

    - `hostname R1`

2. Utilice su código como contraseña para EXEC del usuario para la consola 0.

    > Configuración de consola.

    - `pass 2125974`
    - `login`

3. Utilice su primer nombre (todo en minúsculas) como contraseña de EXEC privilegiado.

    > Configuración de consola.

    - `enable secret brandon`

4. Cifre todas las contraseñas de texto no cifrado.

    > Configuración global.

    - `service password-encryption`

5. Configure un aviso de bienvenida apropiado.

    > Configuración global.

    - `banner motd +Bienvenido al router R1+`

6. Configuración acceso remoto por SSH.

    > Configuración global.

    - `ip domain-name redes.com`
    - `username Admin secret Cisco123`
    - `crypto key generate rsa` (1024 bits)
    - `login block-for 180 attempts 4 within 120`
    - `line vty 0 4`

    > Configuración de consola (a la que nos debió cambiar el comando `line vty`).

    - `transport input ssh`
    - `login local`

7. Conéctese remotamente al `R1` por SSH desde el command Prompt.

    Si hacemos un `sh ip rou`, vemos que solos nos sale un mensaje que dice "Gateway of last resort is not set", por lo que debemos configurar las interfaces

    > Configuración de consola.

    - `int g 0/0`
    - `ip add 192.168.25.1 255.255.255.0`
    - `no sh`
    - `do sh ip rou` (para verificar que lo hicimos bien)
    - `int g 0/1`
    - `ip add 192.168.26.1 255.255.255.0`
    - `no sh`

    Dependiendo desde que pc vamos a hacer la conexión, usaremos la ip asociada a su interfaz.

    > Desde el `PC0` sería `ssh -l Admin 192.168.25.1`

8. Guardar la configuración en la NVRAM.

    > Privilegiado.

    - `write memory` en todos los dispositivos

9. Verifique y analice la tabla de enrutamiento del router (`sh ip route`).

    ```
        192.168.25.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.25.0/24 is directly connected, GigabitEthernet0/0
    L       192.168.25.1/32 is directly connected, GigabitEthernet0/0
        192.168.26.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.26.0/24 is directly connected, GigabitEthernet0/1
    L       192.168.26.1/32 is directly connected, GigabitEthernet0/1
    ```

10. Configure el nombre `S1` y `S2`.

    >  Configuración global.

    - `S1`

        - `hostname S1`

    - `S2`

        - `hostname S2`

11. Configure el direccionamiento `IP` y el `GATEWAY` de acuerdo con la tabla de direccionamiento.

    >  Configuración global.

    - `S1`

        1. `interface vlan 1`
        2. `ip address 192.168.25.254 255.255.255.0`
        3. `no shutdown`
        4. `ip default-gateway 192.168.25.1`

    - `S2`

        1. `interface vlan 1`
        2. `ip address 192.168.26.254 255.255.255.0`
        3. `no shutdown`
        4. `ip default-gateway 192.168.26.1`

12. Registre las interfaces con descripciones, incluida la interfaz `VLAN 1` de los switch

    >  Configuración global.

    - `R1`

        1. `interface g 0/0`
        2. `description "interface g 0/0"`
        3. `interface g 0/1`
        4. `description "interface g 0/1"`


    - `S1`

        1. `interface vlan 1`
        2. `description "interface vlan 1"`

    - `S2`

        1. `interface vlan 1`
        2. `description "interface vlan 1"`