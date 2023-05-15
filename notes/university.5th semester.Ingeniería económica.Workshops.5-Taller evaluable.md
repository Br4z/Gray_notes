---
id: f9oy09qlz0pbho74zk1lztw
title: 5-Taller evaluable
desc: ''
updated: 1683913877683
created: 1683499022629
---

1. Se ha realizado una inversión que produce beneficios por $230000 mensuales durante año y medio, los cuales se han ido depositando en una cuenta de ahorros que reconoce una tasa de interés del 1.2% mensual. Se planea realizar un retiro de $850000 al finalizar el segundo año y un año después retirar el capital restante en cuatro (4) cuotas anuales iguales. ¿Cuál es el valor de estos 4 retiros?

    ![1 problem](./assets/University/Ingenieria%20economica/2_5-1%201_problem.jpg)

    > $1.5 \text{ años} = 18 \text{ meses}$

    - $F_{18}/A_{-1 - 18}$

        $$
        F = 230 \left (\frac{(1 + 1.2\%)^{18} - 1}{1.2\%} \right ) \approx 4591
        $$

    - $F_{24}/F_{18}$

        $$
        F = 4591(1 + 1.2\%)^6 \approx 4932
        $$

    - $S_{24}$

        $$
        S = F_{24} - 850 \approx 4082
        $$

    > $i_a = (1 + 1.2\%)^{12} - 1 \approx 15\%$

    - $A/P$

        $$
        A \approx 4082 \left (\frac{15\%(1 + 15\%)^4}{(1 + 15\%)^4 - 1} \right ) \approx 1430 * 10^3

2. Se depositan $100000 en una cuenta de ahorros que paga un interés del 7% trimestral; dentro de tres (3) años retira la tercera parte del total acumulado en su cuenta hasta ese momento, dos (2) años más tarde hace un depósito igual a la mitad del saldo existente en ese momento y dos años después retira la totalidad del dinero existente en esa fecha, en una serie de 6 retiros trimestrales iguales. Hallar el valor de estos últimos 6 retiros.

    ![2 problem](./assets/University/Ingenieria%20economica/2_5-2%202_problem.jpg)

    > $3 \text{ años} = 12 \text{ trimestres}$

    - $F_3/P$

        $$
        F = 100(1 + 7\%)^{12} \approx 225
        $$

    - $S_3$

        $$
        S = F_3 \frac{1}{3} \approx 150
        $$

    > $2 \text{ años} = 8 \text{ trimestres}$

    - $F_5/S_3$

        $$
        F = 150(1 + 7\%)^8 \approx 257
        $$

    - $S_5$

        $$
        S = F_5 + F_5 \frac{1}{2} \approx 386
        $$

    > $5 \text{ años} = 20 \text{ trimestres}$

    - $S_{27 \text{ trimestres}}/S_5$

        $$
        S = S_5(1 + 7\%)^7 \approx 620
        $$

    - $A/S_{27 \text{ trimestres}}$

        $$
        A \approx 620 \left (\frac{7\%(1 + 7\%)^6}{(1 + 7\%)^6 - 1} \right ) \approx 130 * 10^3
        $$

3. Una fábrica planea comprar un aditamento para un equipo que reduce la producción defectuosa en un 4.2%, lo que representa un ahorro de $1320000 anuales durante cinco (5) años. Luego de este tiempo el aditamento mejorará la producción defectuosa solo en un 1.8% durante otros 5 años. Se celebra un contrato para vender toda la producción por diez (10) años consecutivos, al cabo de este tiempo el aditamento será totalmente inservible, es decir, no se obtienen ahorros por su uso. Si se requiere un retorno sobre la inversión (tasa de interés) del 14.4% anual. ¿Cuánto estaría dispuesto a pagar por el aditamento?

    ![3 problem](./assets/University/Ingenieria%20economica/2_5-3%203_problem.jpg)

    > ¿Cuánto estaría dispuesto a pagar? = **hoy**

    > Vamos a llevar todo al presente ($P_0$), para poder concluir si el proyecto es rentable.

    - Hallamos el valor que se ahorra en el "segundo" periodo.

        $$
        \frac{1320}{4.2} * 1.8 \approx 566 * 10^3
        $$

    - $P/A_{0 - 5}$

        $$
        P = 1320 \left (\frac{(1 + 4.2\%)^5 - 1}{4.2\%(1 + 4.2\%)^5} \right ) \approx 5843
        $$

    - $P/A_{5 - 10}$

        $$
        P \approx 566 \left (\frac{(1 + 1.8\%)^5 - 1}{1.8\%(1 + 1.8\%)^5} \right ) \approx 2683
        $$

    - $P_0/F_5$

        $$
        P \approx \frac{2683}{(1 + 1.8\%)^5} \approx 2454

    - $P_\text{total}$

        $$
        P \approx 2683 + 2454 = 5137 * 10^3
        $$

    Estaría dispuesto a pagar una cantidad $x \leq 5137000$.

    > Cualquier cantidad que cumpla esa restricción, representan ganancias.