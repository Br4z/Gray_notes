---
id: sehfz3ivw998icktnr6tghd
title: 3-Equivalencias - GA anualidad y GG presente
desc: ''
updated: 1682284543306
created: 1681681862218
---

1. De acuerdo con la siguiente serie anual y considerando una tasa de interés del 12% anual

    ![Money flow diagram](./assets/University/Ingenieria%20economica/2_3-1%20Money_flow_diagram.jpg)


    > Podemos obtener el presente de todos los flujos o identificar estructuras.

    Identificamos

    - Anualidad $160_{0 - 3}$

    - Gradiente aritmético $(230,40)_{3 - 8}$

    - Presente $P_9 = 500$

    - Presente $P_{10} = 625$

    encuentre

    - El valor presente de los flujos

        - Anualidad ($P_0/A_{0 - 3}$)

            $$
            P = 160 \left (\frac{(1 + 12\%)^3 - 1}{12\%(1 + 12\%)^3} \right ) \approx 385 \\[10 pt]
            $$

        - Gradiente aritmético ($P_3/(230,40)_{3 - 8} \rightarrow P_0/F_3$)

            $$
            P_A = 230 \left (\frac{(1 + 12\%)^5 - 1}{12\%(1 + 12\%)^5} \right ) \approx 8291\\[10 pt]


            P_G = 40 \left (\frac{(1 + 12\%)^5 - 1 - 12\% * 5}{{12\%}^2(1 + 12\%)^5} \right ) \approx 256 \\[10 pt]

            P = P_A + P_G \approx 8291 + 256 = 8547
            $$

            Como necesitamos llevar a presente el flujo usamos $P/F_3$

            $$
            P = \frac{8547}{(1 + 12\%)^3} \approx 772
            $$

        - Presente $F_9 = 500$ ($P_0/F_3$)

            $$
            P = \frac{500}{(1 + 12\%)^9} \approx 180
            $$

        - Presente $F_{10} = 625$ ($P_0/F_{10}$)

            $$
            P = \frac{625}{(1 + 12\%)^{10}} \approx 201
            $$

        $$
        P \approx 385 + 772 + 180 + 201 = 1538
        $$

    - El valor de una anualidad equivalente

        $$
        A = 1538 \left (\frac{12\%(1 + 12\%)^{10}}{(1 + 12\%)^{10} - 1} \right ) \approx 272
        $$

2. Una fábrica firma un contrato con un importante cliente donde se compromete a entregarle 200 unidades de su producto al mes durante un año. El precio unitario del producto es de $3500 el primer mes y aumentará $50 cada mes. Si el gerente financiero de la fábrica decide depositar la mitad de los ingresos de este negocio en una cuenta de ahorros que paga el 0.49% mensual.

    - ¿Cuál es el valor presente de los ahorros de la empresa por este concepto?

        $$
        \begin{array}{cc}
            &200  &200     \\
            &*    &*       \\
            &3500 &3550    \\
            &=    &=       \\
            &350000 &355000
        \end{array} \\[10 pt]

        B = 350000 \quad G = 5000 \quad n = 12 \quad i = 0.49\%
        $$

        - Gradiente aritmético ($P_0/(350000,5000)_{0 - 12}$)

            $$
            P_A = 350 \left (\frac{(1 + 0.49\%)^{12} - 1}{0.49\%(1 + 0.49\%)^{12}} \right ) \approx 4069 \\[10 pt]


            P_G = 5 \left (\frac{(1 + 0.49\%)^{12} - 1 - 0.49\% * 12}{{0.49\%}^2(1 + 0.49\%)^{12}} \right ) \approx 316 \\[10 pt]

            P = P_A + P_G \approx 4069 + 316 = 4385 * 10^3
            $$

3. Suponga que usted hace una serie de depósitos anuales en un banco que paga un interés del 3% anual, el depósito inicial al final del primer año es de $600.000. La cantidad depositada cada año se reduce en $50.000 durante los próximos 5 años. ¿Cuánto dinero tendrá al final del quinto año?


    - Gradiente aritmético ($P_0/(600,-50)_{0 - 5} \rightarrow F_5/P_0$)

        $$
        P_A = 600 \left (\frac{(1 + 3\%)^5 - 1}{3\%(1 + 3\%)^5} \right ) \approx 2748\\[10 pt]

        P_G = -50 \left (\frac{(1 + 3\%)^5 - 1 - 3\% * 5}{{3\%}^2(1 + 3\%)^5} \right ) \approx -444 \\[10 pt]

        P_0 \approx 2748 - 444 = 2303 \quad F_5 \approx 2303(1 + 3\%)^5 \approx 2670 * 10^3
        $$

4. Un artículo al contado cuesta $15.400.000 y financiado se adquiere con una cuota inicial de $350.000 y el resto en 15 cuotas mensuales que aumentan cada mes en $58.000; la primera cuota debe pagarse al cabo de cinco meses; el interés es del 0.05% mensual durante los cuatro primeros meses y del 0.1% mensual de ahí en adelante. Hallar el valor de la primera de las cuotas mensuales que hace que ambos planes sean equivalentes.

    - Gradiente aritmético ($F_4/(350,58)_{4 - 20} \rightarrow F_4/P_0$)

        $$
        F_A = 350 \left (\frac{(1 + 0.1\%)^{16} - 1}{0.1\%(1 + 0.1\%)^{16}} \right ) \approx 5553 \\[10 pt]

        F_G = 58 \left (\frac{(1 + 0.1\%)^{16} - 1 - 0.1\% * 16}{{0.1\%}^2(1 + 0.1\%)^{16}} \right ) \approx 6882 \\[10 pt]

        F_4 \approx 5553 + 6882 = 12435 \quad P_0 \approx \frac{12435}{(1 + 0.05\%)^4} \approx 12410 * 10^3

        $$

5. Un empleado empieza a trabajar en una empresa el 1 de enero con un salario mensual de $2.200.000 y decide depositar cada año la mitad del sueldo de diciembre en una cuenta de ahorros que paga un interés del 2.7% anual. Suponiendo que le reajustan el salario cada año en un 9%. Averiguar cuánto tendrá acumulado en la cuenta de ahorros al cumplir 10 años
de trabajo.

    - Gradiente geométrico ($P_0/(1100,2.7\%)_{0 - 10} \rightarrow F_{10}/P_0$)

        $$
        P = 1100 \left (\frac{ 1 - \left (\frac{1100(1 + 2.7\%)}{(1 + 9\%)} \right )^{10}}{(9\% - 2.7\%)} \right )
        $$

​