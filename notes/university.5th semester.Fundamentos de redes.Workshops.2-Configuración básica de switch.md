---
id: 19t085yjlvwn0zgri5qyrq9
title: 2-Configuración básica de switch
desc: ''
updated: 1680125633223
created: 1680121276936
---

1. Examine la ayuda de IOS

    - ¿Qué comando uso? `?`

2. Ingrese al modo privilegiado

    - ¿Qué comando uso? `enable`

3. Ingrese en el modo de configuración global

    - ¿Qué comando uso? `configure terminal`

4. Examine el archivo de configuración actual del switch

    - ¿Qué comando uso? `show running-config`

5. Asigne un nombre a un switch use su nombre como nombre del switch

    - ¿Qué comando uso? `hostname  Brandon`

    > Configuración global.

6. Proporcione acceso seguro a la línea de consola. Use cisco como contraseña

    - ¿Qué comando uso? `password cisco`

    > Configuración de consola (`line console 0`).

    > Para que pida la contraseña usamos `login` (también en el modo de configuración global).

7. Proporcione un acceso seguro al modo privilegiado, usando una contraseña encriptada, use su código de estudiante como contraseña

    - ¿Qué comando uso? `enable password 2125974`

    > Configuración de consola.

8. Encripte las contraseñas de consola y de enable

    - ¿Qué comando uso? `service password-encription`

    > Configuración global.

9. Configure un aviso de mensaje del día (MOTD), el mensaje debe incluir su nombre y código

    - ¿Qué comando uso? `banner motd <symbol>This switch is property of Brandon (2125974)<symbol>`

    > Configuración global.

10. Guarde el archivo de configuración

    - ¿Cuáles son las 2 opciones para guardar?
        - `write memory`
        - `copy running-config startup-config`

11. Examine el archivo de configuración guardado.

    - ¿Qué comando uso? `show startup-config`

12. ¿En qué memoria queda almacenado el archivo de configuración guardado? En la **NVRAM**

13. Realice una prueba de ping entre los 2 PC

    - ¿Tiene respuesta? Si
    - ¿Podría hacer ping a los switch? Sí, para gestionarlo remotamente

14. Verifique la tabla MAC de S1

    - ¿Qué comando uso? `show mac-addresses-table`

15. Configure y habilite en el S1 con una dirección IP (vlan 1)

    - ¿Qué comandos uso?

        >  Configuración global.

        1. `interface vlan 1`
        2. `ip address 192.168.25.250 255.255.255.0`
        3. `no shutdown`
        4. `ip default-gateway 192.168.1.1`

16. Realice una conexión remota a S1 desde PC1 usando el protocolo TELNET

    - ¿Obtuvo respuesta? No, porque no configuramos las conexiones virtuales (solo configuramos las de consola).

17. Configure una clave Class123 en las líneas VTY para acceso remoto, pruebe nuevamente con el protocolo TELNET.

    - ¿Qué comandos uso?

        >  Configuración global.

        1. `line vty 0 4`
        2. `password Class123`
        3. `login`

18. Establezca el nombre de dominio en `redes.com`

    - ¿Qué comando uso? `ip domain-name redes.com`

        > Configuración global.

19. Cree un usuario Admin con una contraseña segura Class123

    - ¿Qué comando uso? `username Admin secret Class123`

    >  Configuración global.

20. Genere claves RSA de 1024 bits

    - ¿Qué comando uso? `crypto key generate rsa`

    > Configuración global.

21. Bloquee durante tres minutos a cualquier persona que no pueda iniciar sesión después de cuatro intentos en un período de dos minutos.

    - ¿Qué comando uso? - `login block-for 180 attempts 4 within 120`

    > Configuración global.

22. Configure las líneas VTY para el acceso por SSH y solicite los perfiles de usuarios locales para la autenticación.

    - ¿Qué comandos uso?

        >  Configuración global.

        1. `line vty 0 4`
        2. `transport input ssh`
        3. `login local`

23. Realice una conexión remota a S1 desde PC1 usando el protocolo SSH

    - ¿Qué comandos uso? `ssh -l Admin 192.168.25.250`

    - ¿Obtuvo respuesta? Si