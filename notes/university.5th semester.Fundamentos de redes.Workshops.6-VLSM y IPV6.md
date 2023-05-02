---
id: np8y3ula9232o3k9xav5vtk
title: 6-VLSM y IPV6
desc: ''
updated: 1682878161733
created: 1682721907826
---

1. Divida la red 172.16.0.0/16 en subredes para cada área así:

    - Comercial: 5000 hosts
    - Ingeniería: 1000 hosts
    - Contabilidad: 500 hosts
    - Mercadeo: 200 hosts

    Empezamos desde la más grande a la más pequeña

    1. Comercial

        $$
        2^n - 2 \geq 5000 \quad n \geq \lg 4998 \quad n = 13
        $$

        Necesitamos 13 bits para los hostss, lo que nos deja con 19 (32 - 13) bits para las redes, es decir, con la máscara:

        $$
        255.255.111 \quad 00000.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.16  &.0        &.0 \\
                &255.255 &.11100000 &.0 \\
                &= 172.16.0.0 = 172.16.0.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.16.000 \quad 11111.11111111 = 172.16.31.255
            $$

        Por lo que la siguiente red empezara en 172.16.32.0

        > También pudimos hallar la red donde empezara cambiando el ultimo dígito que cubre la subred, en este caso $000 \rightarrow 001$ quedando $00100000 = 32$.

    2. Ingeniería

        $$
        2^n - 2 \geq 1000 \quad n \geq \lg 998 \quad n = 8
        $$

        Necesitamos 8 bits para los hosts, lo que nos deja con 22 (32 - 8) bits para las redes, es decir, con la máscara:

        $$
        255.255.111111 \quad 00.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.16  &.00100000 &.0 \\
                &255.255 &.11100000 &.0 \\
                &= 172.16.00100000.0 = 172.16.32.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.16.001000 \quad 11.11111111 = 172.16.35.255
            $$

        Por lo que la siguiente red empezara en 172.16.36.0

    3. Contabilidad

        $$
        2^n - 2 \geq 500 \quad n \geq \lg 498 \quad n = 7
        $$

        Necesitamos 7 bits para los hosts, lo que nos deja con 23 (32 - 7) bits para las redes, es decir, con la máscara:

        $$
        255.255.1111111 \quad 0.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.16. &.00100100  &.0 \\
                &255.255 &.1111110 &.0 \\
                &= 172.16.00100100.0 = 172.16.36.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.16.0010010 \quad 1.11111111 = 172.16.37.255
            $$

        Por lo que la siguiente red empezara en 172.16.38.0

    4. Mercadeo

        $$
        2^n - 2 \geq 200 \quad n \geq \lg 198 \quad n = 8
        $$

        Necesitamos 8 bits para los hosts, lo que nos deja con 24 (32 - 8) bits para las redes, es decir, con la máscara:

        $$
        255.255.1255.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.16  &.00100110  &.0 \\
                &255.255 &.1111111   &.0 \\
                &= 172.16.00100110.0 = 172.16.38.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.16.38.11111111 = 172.16.38.255
            $$

        Por lo que la siguiente red empezara en 172.16.39.0

2. Divida la red 172.31.0.0/16 en subredes para cada área así:

    - Comercial: 16000 host
    - Ingeniería: 8000 host
    - Contabilidad: 4000 host
    - Mercadeo: 2000 host

    1. Comercial

        $$
        2^n - 2 \geq 16000 \quad n \geq \lg 17998 \quad n = 14
        $$

        Necesitamos 14 bits para los hosts, lo que nos deja con 18 (32 - 14) bits para las redes, es decir, con la máscara:

        $$
        255.255.11 \quad 000000.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.31  &.0        &.0 \\
                &255.255 &.11000000 &.0 \\
                &= 172.16.0.0 = 172.31.0.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.31.00 \quad 111111.11111111 = 172.31.63.255
            $$

        Por lo que la siguiente red empezara en 172.31.64.0

    2. Ingeniería

        $$
        2^n - 2 \geq 8000 \quad n \geq \lg 7998 \quad n = 13
        $$

        Necesitamos 13 bits para los hosts, lo que nos deja con 19 (32 - 13) bits para las redes, es decir, con la máscara:

        $$
        255.255.111 \quad 00000.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.31  &.01000000 &.0 \\
                &255.255 &.11100000 &.0 \\
                &= 172.31.01000000.0 = 172.31.64.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.31.010 \quad 11111.11111111 = 172.31.95.255
            $$

        Por lo que la siguiente red empezara en 172.31.96.0

    3. Contabilidad

        $$
        2^n - 2 \geq 4000 \quad n \geq \lg 3998 \quad n = 12
        $$

        Necesitamos 12 bits para los hosts, lo que nos deja con 20 (32 - 12) bits para las redes, es decir, con la máscara:

        $$
        255.255.1111 \quad 0000.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.31  &.0110000 &.0 \\
                &255.255 &.11110000 &.0 \\
                &= 172.31.0110000.0 = 172.31.96.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.31.0110 \quad 1111.11111111 = 172.31.111.255
            $$

        Por lo que la siguiente red empezara en 172.31.112.0

    4. Mercadeo

        $$
        2^n - 2 \geq 2000 \quad n \geq \lg 1998 \quad n = 11
        $$

        Necesitamos 11 bits para los hosts, lo que nos deja con 21 (32 - 11) bits para las redes, es decir, con la máscara:

        $$
        255.255.11111 \quad 000.0
        $$

        - IP red:

            $$
            \begin{align*}
                &172.31  &.0111000  &.0 \\
                &255.255 &.11111000 &.0 \\
                &= 172.31.0111000.0 = 172.31.112.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            172.31.01110 \quad 111.11111111 = 172.31.119.255
            $$

        Por lo que la siguiente red empezara en 172.31.120.0


3. Divida la red 192.168.200.0/24 en subredes para cada área así:

    - Estudiantes: 100 hosts
    - Profesores: 60 hosts
    - Administrativo: 30 hosts
    - Directivo: 12 hosts

    1. Estudiantes

        $$
        2^n - 2 \geq 100 \quad n \geq \lg 98 \quad n = 7
        $$

        Necesitamos 7 bits para los hosts, lo que nos deja con 25 (32 - 7) bits para las redes, es decir, con la máscara:

        $$
        255.255.255.1 \quad 0000000
        $$

        - IP red:

            $$
            \begin{align*}
                &192.168  &.11001000 &.0 \\
                &255.255  &.255       &.10000000 \\
                &= 192.168.11001000.0 = 192.168.200.0
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            192.168.200.0 \quad 1111111 = 192.168.200.127
            $$

        Por lo que la siguiente red empezara en 192.168.200.128

    2. Profesores

        $$
        2^n - 2 \geq 60 \quad n \geq \lg 58 \quad n = 6
        $$

        Necesitamos 6 bits para los hosts, lo que nos deja con 26 (32 - 6) bits para las redes, es decir, con la máscara:

        $$
        255.255.255.11 \quad 000000
        $$

        - IP red:

            $$
            \begin{align*}
                &192.168.200  &.10000000 \\
                &255.255.255  &.11000000 \\
                &= 192.168.200.10000000 = 192.168.200.128
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            192.168.200.10 \quad 111111 = 192.168.200.191
            $$

        Por lo que la siguiente red empezara en 192.168.200.192

    3. Administrativo

        $$
        2^n - 2 \geq 30 \quad n \geq \lg 28 \quad n = 5
        $$

        Necesitamos 5 bits para los hosts, lo que nos deja con 27 (32 - 5) bits para las redes, es decir, con la máscara:

        $$
        255.255.255.111 \quad 00000
        $$

        - IP red:

            $$
            \begin{align*}
                &192.168.200  &.11000000 \\
                &255.255.255  &.11100000 \\
                &= 192.168.200.11000000 = 192.168.200.192
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            192.168.200.110 \quad 11111 = 192.168.200.223
            $$

        Por lo que la siguiente red empezara en 192.168.200.224

    4. Directivo

        $$
        2^n - 2 \geq 12 \quad n \geq \lg 10 \quad n = 4
        $$

        Necesitamos 4 bits para los hosts, lo que nos deja con 28 (32 - 4) bits para las redes, es decir, con la máscara:

        $$
        255.255.255.1111 \quad 0000
        $$

        - IP red:

            $$
            \begin{align*}
                &192.168.200  &.11100000 \\
                &255.255.255  &.11110000 \\
                &= 192.168.200.11100000 = 192.168.200.224
            \end{align*}
            $$

        - Broadcast:

            Llenamos con 1 los espacios de host:

            $$
            192.168.200.1110 \quad 1111 = 192.168.200.239
            $$

        Por lo que la siguiente red empezara en 192.168.200.240

5. Comprima las siguientes direcciones IPV6 con la regla de omitir ceros:

    - 2001:0000:0000:ABCD:0000:0000:0010:0100

        2001::ABCD:0000:0000:10:100

    - 2001:0DB8:000B:1000:0101:1010:0010:0100

        2001:DB8:B:1000:101:1010:10:100

    - 2001:0DB8:0000:0000:0000:0000:0010:0100

        2001:DB8::10:0100

    - 2001:0DB8:000B:1000:0000:0000:0010:0100

        2001:DB8B:1000::10:100

    - 2001:0000:0000:0000:0000:0000:0000:0010

        2001::10