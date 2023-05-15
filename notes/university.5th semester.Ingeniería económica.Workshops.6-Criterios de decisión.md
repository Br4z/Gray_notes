---
id: 3rd4nx3vzox1kxw96u0tday
title: 6-Criterios de decisión
desc: ''
updated: 1684121180457
created: 1684109135993
---

1. Un inversionista planea emprender un proyecto de productos químicos para lo cual requiere invertir en una planta procesadora cuyo costo es de $300.000.000. Los ingresos brutos estimados son de $210.000.000 anuales y los costos brutos anuales de $130.000.000. La planta operará durante 10 años, al final de los cuales tendrá un valor de mercado de $80.000.000. Si la TMR del inversionista es de 11% anual, determine la factibilidad del proyecto usando el VPN y el VFN.

    Podríamos decir que lo que genera anualmente es:

    $$
    210 - 130 = 80
    $$

    - $P/A_{(0 - 10)}$

        $$
        P = 80 \left (\frac{(1 + 11\%)^{10} - 1}{11\%(1 + 11\%)^{10}} \right ) \approx 471 * 10^6
        $$

    - $P/F_{10}$

        $$
        P = \frac{80}{(1 + 11\%)^{10}} \approx 28 * 10^6
        $$

    $$
    \text{VPN} = (471 + 28 - 300) * 10^6 = 199 * 10^6 \\[10 pt]

    \text{VFN} = 199(1 + 11\%)^{10} \approx 565 * 10^6
    $$

2. Un ingeniero ha ahorrado dinero para inversión y le proponen un proyecto en el que debe aportar $6.000.000 al inicio del primer año y $10.000.000 iniciando el año 2. Los beneficios generados serán de $1.900.000 al final del segundo año, e irán creciendo en $700.000 anuales hasta el octavo año, en el cual se esperan vender los bienes del proyecto por un valor de $9.000.000. Si el ingeniero dispone del dinero suficiente para invertir en el proyecto, pero tiene otras opciones de inversión que le generen el 19% anual, determine si el proyecto es factible usando como criterio el VAN.

    Tomaremos el "al inicio del primer año" como el final del año que le precede.

    - $(1900,700)_{1 - 8}$

        $$
        P_A = 1900 \left (\frac{(1 + 19\%)^7 - 1}{19\%(1 + 19\%)^7} \right ) \approx 7040 * 10^3 \\[10 pt]

        P_G = 700 \left (\frac{(1 + 19\%)^7 - 1 - 19\% * 7}{19\%^2(1 + 19\%)^7} \right ) \approx 6021* 10^3 \\[10 pt]

        P \approx (7040 + 6021) * 10^3 = 13061 * 10^3
        $$

    - $P/F_1$

        $$
        P = -\frac{13061}{(1 + 19\%)} \approx -10975 * 10^3
        $$


    - $P/F_8$

        $$
        P = \frac{9000}{(1 + 19\%)^8} \approx 2238 * 10^3
        $$

    - $P/F_1$

        $$
        P = -\frac{10000}{(1 + 19\%)} \approx 8403 * 10^3
        $$

    $$
    \text{VPN} = (10975 + 2238 - 8403 - 6000)  * 10^ 3 = -1190 * 10^3 \\[10 pt]

    \text{VAN} = -1190 \left (\frac{19\%(1 + 19\%)^8}{(1 + 19\%)^8 - 1} \right ) \approx -301 * 10^3
    $$

3. Usted está estudiando el montaje de una empresa productora de ropa universitaria, para lo cual requiere una inversión en equipos de confección por un valor de $4.300.000. Usted estima que sus ingresos netos anuales serán de $830.000 y desea operar el proyecto durante 10 años. Si su TMR es de 18% anual:

    - $P/A_{(0 - 10)}$

        $$
        P = 830 \left (\frac{(1 + 18\%)^{10} - 1}{18\%(1 + 18\%)^{10}} \right ) \approx 3730 * 10^3
        $$

    $$
    \text{VPN} \approx (3730 - 4300) = -570
    $$

    - ¿Cuál debe ser el valor de mercado de los equipos de confección al final del proyecto para que su utilidad económica actual sea de $200.000?

        - $P/F_{10}$

            $$
            P = \frac{F_{10}}{(1 + 19\%)^{10}}
            $$

            $$
            \text{VPN} = (3730 + \frac{F_{10}}{(1 + 18\%)^{10}} - 4300) = 200 \\[10 pt]

            F_{10} \approx 4030 * 10^3
            $$

    - Para un valor de mercado de $2.000.000 ¿Cuál sería el nivel mínimo de ingresos netos para que el proyecto fuese factible?

        - $P/F_{10}$

            $$
            P = \frac{2000}{(1 + 19\%)^{10}} \approx 351 * 10^3
            $$

        - $P/A_{(0 - 10)}$

            $$
            P = A \left (\frac{(1 + 18\%)^{10} - 1}{18\%(1 + 18\%)^{10}} \right )
            $$

        $$
        \text{VPN} = A \left (\frac{(1 + 18\%)^{10} - 1}{18\%(1 + 18\%)^{10}} \right ) + 351 - 4300 = 0 \\[10 pt]

        A \approx 879 * 10^3
        $$

4. ToysKids es una empresa de juguetes que tiene dentro de sus principales clientes a grandes superficies y almacenes de cadena. Actualmente la empresa está atravesando por problemas de liquidez, y para financiar su operación ha considerado la opción de vender algunas de sus facturas de venta de sus mejores clientes. Dichas facturan tienen vencimiento de 30 días (10 millones), 47 días (16 millones), 96 días (27 millones) y 120 días (39 millones). ¿Cuál sería el valor que un inversionista debe pagar por esas facturas hoy si desea ganar el 21% anual?

    $$
    i_D = (1 + 21\%)^{\frac{1}{365}} - 1 = 0.053\%
    $$

    - $P/F_{30}$

        $$
        P = \frac{10}{(1 + 0.053\%)^{30}} \approx 9
        $$

    - $P/F_{47}$

        $$
        P = \frac{16}{(1 + 0.053\%)^{47}} \approx 15
        $$

    - $P/F_{96}$

        $$
        P = \frac{27}{(1 + 0.053\%)^{96}} \approx 25
        $$


    - $P/F_{120}$

        $$
        P = \frac{39}{(1 + 0.053\%)^{120}} \approx 36
        $$

    $$
    \text{VPN} \approx 9 + 15 + 25 + 36 = 85.0
    $$