---
id: e5g8bu0xj64sfs2osjso70v
title: 1-Equivalencias
desc: ''
updated: 1681672685249
created: 1679887301950
---

1. Suponga que cuenta con una cantidad de dinero $P$ para invertir a $n$ años, para lo cual tiene a disposición un instrumento financiero con una tasa de interés simple anual $i^s$. Determine una expresión para calcular una tasa de interés compuesta anual equivalente.

    $$

    \text{Sabiendo que} \quad F_n = P(1 + i)^n \\[10 pt]

    i = \left (\frac{F_n}{P} \right )^\frac{1}{n} - 1
    $$

    Por ejemplo

    - $P = 1000$
    - $n = 3 \text{ años}$
    - $i = 5\% \text{ anual}$

    $$
    I = 1000 * 0.05 * 3 = 150
    $$

    Con las condiciones anteriores, un interés simple generaría 150 (terminando con 1150) de interés. Usando la formula

    $$
    i = \left (\frac{1150}{1000} \right )^\frac{1}{3} - 1 \approx 0.0477
    $$

    Entonces, con un interés compuesto del 4.77% anual, terminamos con el mismo dinero que con un interés simple del 5% anual.

    $$
    F_3 = 1000(1 + 0.0477)^3 \approx 1150.03
    $$

2. Una entidad bancaria le ofrece a usted pagarle por sus depósitos de efectivo un interés simple del 5.56% anual.

    - ¿En cuánto tiempo se duplica su inversión?

        > Si duplica su inversión significa que el interés generado es el mismo monto inicial ($P$).

        $$
        P = P * i * n \quad P = P * 0.0556 * n \quad n = \frac{1}{0.0556} \approx 18
        $$

        La inversión se duplicará aproximadamente en 18 años.

    - ¿Cuál es la tasa anual compuesta equivalente?

        > Usando la fórmula del anterior punto.

        $$
        i = \left (\frac{2P}{P} \right )^\frac{1}{18} - 1 \approx 0.04 \\[10 pt]

        \text{Comprobando la respuesta} \quad F_{18} = P(1 + 4\%)^{18} = P * 2.02 \approx 2P
        $$

3. Determine la tasa de interés simple **anual** aplicada a un préstamo de $1.500.000 (presente) del cual se recibirá un valor de $3.300.000 en 20 **semestres**

    > $20 \text{ semestres} = 10 \text{ años}$

    $$
    I = 3300000 - 1500000 = 1800000 \\[10 pt]

    1800000 = 1500000 * i * 10 \quad i = \frac{6}{50} = 0.12 \\[10 pt]

    \text{Comprobando la respuesta} \quad F_{10} = 1500000(1 + 0.12 * 10) = 1500000(2.2024) = 3300000
    $$

    - ¿Cuál sería el monto recibido al final de los 10 años si esa tasa anual fuese de interés compuesto?

        $$
        F_{10} = 1500000(1 + 12\%)^{10} \approx 4658772
        $$

4. El banco A le ofrece un CDT al 3.5% anual, mientras que el banco B le oferta un rendimiento del 3.8% anual para su CDT. La tasa de inflación proyectada para el próximo año es del 4% anual. ¿Cuál sería su decisión?

5. Usted decide ahorrar su dinero en una cuenta que le renta una tasa compuesta del 6% anual y espera recibir en 36 meses la suma de $30.000.000

    - ¿Cuál fue el monto ahorrado inicialmente?

        > $36 \text{ meses} = 3 \text{ años}$

        $$
        \text{Despejando $P$ en la fórmula general de interés compuesto} \quad P = \frac{F_n}{(1 + i)^n} \\[10 pt]

        P = \frac{30000000}{(1 + 6\%)^{3}} \approx 25188578.5
        $$

    - ¿Cuál es el monto correspondiente a los intereses?

        $$
        I = 30000000 - 25188578.5 = 4811421.5
        $$
6. ¿Es mejor invertir en un proyecto que garantiza triplicar la inversión al cabo de tres años y medio, o depositar el dinero en una cuenta que paga el 2.8% mensual?

    > Cuando el tipo de interés no se menciona es compuesto.

    $$
    F_{42} = P(1 + 0.028)^{42} = P(3.19) \\[10 pt]

    \text{Como $3.19P > 3P$ la mejor opción es la segunda}
    $$


    Otra forma de abordar el problema es comparando las tasas

    $$
    i = \left (\frac{3P}{P} \right )^{\frac{1}{42}} - 1 \approx 0.026 = 2.6\% \quad {\color{Green} 2.8\% > 2.6\%}
    $$

7. Juan le debe a Carlos la suma de $1.000.000, y para pagarle le propone dos alternativas: la primera es desembolsarle el dinero hoy, mientras que la segunda es realizarle un pago de $1.100.000 dentro de 6 meses. Si Carlos puede obtener una rentabilidad del 1,5% mensual
en otros negocios, ¿cuál propuesta debe aceptar?

    $$
    F_6 = 1000000(1 + 1.5\%)^6 \approx 1093443
    $$

    Si espera los 6 meses, terminaría recibiendo más. Lo recomendable es escoger la segunda opción.

    > El análisis se hizo simplificando el valor del dinero a través del tiempo.

8. Usted hoy dispone en su cuenta de ahorros un valor de $3.500.000 de los cuales va a invertir $1.500.000 en un proyecto a 3 meses con una rentabilidad del 2.1% mensual. Además, usted tiene abierto un CDT al 4,3% mensual que en un año le desembolsará un valor de $3.480.000. ¿Cuál es el valor presente de su portafolio?

    > Lo único que necesitamos calcular es el dinero que tiene en el CDT.

    > $1 \text{ año} = 12 \text{ meses}$
    $$
    P = \frac{3480000}{(1 + 4.3\%)^{12}} \approx 2099750 \\[10 pt]

    P_{total} = 3500000 + 2099750 = 5.599.750
    $$

9. Manuel desea comprar una moto nueva y para ello se dirige a un concesionario en el que le ofrecen dos alternativas: la primera es pagar el valor total de la moto un año después, la segunda es obtener un descuento del 10% si paga de contado el mismo día. Calcule el costo financiero anual en que incurre el concesionario en este negocio.

    > costo financiero anual = tasa de interés

    $$
    V_c = \text{valor al contado de la moto} = 1 \quad V_d = \text{valor de la moto con descuento} = 0.9 \\[10 pt]

    1 = 0.9(1 + i)^1 \quad i = \frac{1}{0.9} - 1 \approx 11.12\%
    $$

10. Considerando el siguiente perfil de flujos en un horizonte de 10 años, y dada una tasa del 12.3% anual, determine el valor presente de los flujos.

    > Usando $P_t = P_i - P_e$ y la formula del presente ($P = \frac{F}{(1 + i)^n}$).

    $$
    n = 10 \quad i = 12.3\% \\[10 pt]

    P_1 = 520 \quad n = 0 \rightarrow P_1 \approx 520 \quad (E) \\[10 pt]

    P_2 = 480 \quad n = 2 \rightarrow P_2 \approx 381 \quad (I) \\[10 pt]

    P_5 = 470 - 100 = 370 \quad n = 5 \rightarrow P_5 \approx 207 \quad (E) \\[10 pt]

    P_7 = 300 \quad n = 7 \rightarrow P_7 \approx 133 \quad (I) \\[10 pt]

    P_8 = 300 \quad n = 8 \rightarrow P_8 \approx 118 \quad (I) \\[10 pt]

    P_9 = 300 \quad n = 9 \rightarrow P_9 \approx 106 \quad (I) \\[10 pt]

    P_{10} = 300 \quad n = 10 \rightarrow P_{10} \approx 94 \quad (I) \\[10 pt]

    P_t = (381 + 133 + 118 + 106 + 94) - (520 + 207) = 832 - 727 = 105
    $$

11. Juan tiene una cuenta de ahorros que le paga el 0.14% mensual. Hace hoy un depósito de $1300000. Dos años más tarde retira la mitad de lo acumulado hasta ese momento y un año después de este retiro, deposita $1900000. ¿Cuánto dinero tendrá en el año 5?

    > $2 \text{ años} = 24 \text{ meses} \quad 1 \text{ año} = 13 \text{ meses}$
    $$
    n_i = 1300000 \quad n_2 = \frac{1300000(1 + 0.14\%)^{24}}{2} \approx 672195 \\[10 pt]

    n_3 = 672195(1 + 0.14\%)^{12} + 1900000 \approx 2583575 \\[10 pt]

    n_5 = 2583575(1 + 0.14\%)^{24} \approx 2671795
    $$