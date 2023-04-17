---
id: sehfz3ivw998icktnr6tghd
title: 3-Equivalencias GA anualidad- GG presente
desc: ''
updated: 1681701640852
created: 1681681862218
---

1. De acuerdo con la siguiente serie anual y considerando una tasa de interés del 12% anual

    !1


    Identificamos

    - Anualidad $160_{0 - 3}$

    - Gradiente aritmético $(230,40)_{3 - 8}$

    - Presente $P_9 = 500$

    - Presente $P_{10} = 625$

    encuentre

    - El valor presente de los flujos

        - Anualidad

            $$
            P = 160 \left (\frac{(1 + 12\%)^3 - 1}{12\%(1 + 12\%)^3} \right ) \approx 385 \\[10 pt]
            $$

        - Gradiente aritmético

            $$
            P_A = 230 \left (\frac{(1 + 12\%)^5 - 1}{12\%(1 + 12\%)^5} \right ) \approx 8291\\[10 pt]


            P_G = 40 \left (\frac{(1 + 12\%)^5 - 1 - 12\% * 5}{{12\%}^2(1 + 12\%)^5} \right ) \approx 256 \\[10 pt]

            P = P_A + P_G \approx 8291 + 256 = 8547
            $$

            Como necesitamos llevar a presente el flujo usamos $P/F_3$

            $$
            P = \frac{8547}{(1 + 12\%)^3} \approx 772
            $$

        - Presente $P_9 = 500$

            $$
            P = \frac{500}{(1 + 12\%)^9} \approx 180
            $$

        - Presente $P_{10} = 625$

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

        - Gradiente aritmético $(3500,50)_{0 - 12}$

3. Suponga que usted hace una serie de depósitos anuales en un banco que paga un interés del 3% anual, el depósito inicial al final del primer año es de $600.000. La cantidad depositada cada año se reduce en $50.000 durante los próximos 5 años. ¿Cuánto dinero tendrá al final del quinto año?


    - Gradiente aritmético $(600,-50)_{0 - 5}$

        $$
        P_A = 600 \left (\frac{(1 + 3\%)^5 - 1}{3\%(1 + 3\%)^5} \right ) \approx 2748\\[10 pt]

        P_G = -50 \left (\frac{(1 + 3\%)^5 - 1 - 3\% * 5}{{3\%}^2(1 + 3\%)^5} \right ) \approx -444 \\[10 pt]

        P \approx 2748 - 444 = 2303
        $$

4. 

​