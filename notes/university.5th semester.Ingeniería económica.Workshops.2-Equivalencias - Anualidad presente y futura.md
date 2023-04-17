---
id: fgw4ro8ooc3lof48qbqv00y
title: 2-Equivalencias - Anualidad presente y futura
desc: ''
updated: 1681682148935
created: 1681065360659
---

1. Una empresa decide ahorrar $2100000 mensualmente durante 2 años en una entidad bancaria que le ofrece una tasa del 5.7% mensual para el primer año y del 3.9% mensual para el segundo año. Determine el valor que recibirá la empresa en el mes 24.

    > $1 \text{ año} = 12 \text{ meses}$


    - 1er año

        $$
        F_1 = 2100 \left (\frac{(1 + 5.7\%)^{12} - 1}{5.7\%} \right ) \approx 34812
        $$

    - 2do año

        $$
        F_1 = 2100 \left (\frac{(1 + 3.9\%)^{12} - 1}{3.9\%} \right ) \approx 31373
        $$

    Ahora tenemos que llevar $F_1$ a los 12 meses que le faltan ($F/P_{12}$).

    $$
    F_1 = 34812(1 + 3.9\%)^{12} \approx 55096
    $$

    La suma final $F_1 + F_2 = 86469 * 10^3$

2. El dueño de un restaurante desea saber la diferencia, luego de un año, entre el valor futuro de los ingresos y el de los egresos para un año de funcionamiento de su restaurante, con los siguientes datos: paga un arriendo de $990000 por mes anticipado, un seguro al principio del año por un valor de $500000, por mano de obra $2500000 mensuales, por materias primas para la preparación de los alimentos $13942000 cada mes, por ingresos mensuales de $21450000, y la tasa de rentabilidad del dueño del restaurante es del 3% mensual.

    > Para convertir todo usamos el interés propuesto.

    - Arriendo ($F_{11}/A_1 \rightarrow F/P_{11}$)

        $$
        A_1 \rightarrow 990_{-1,11} \text{ (E)} \\[10 pt]

        F_{11} = 990 \left (\frac{(1 + 3\%)^{12} - 1}{3\%} \right ) \approx 14050 \quad F = 14050(1 + 3\%)^1 = 14472
        $$

    - Seguro ($F/P_0$)

        $$
        P_0 \rightarrow 500 \text{ (E)} \quad F = 500(1 + 3\%)^{12} \approx 713
        $$

    - Mano de obra ($F/A_2$)

        $$
        A_2 \rightarrow 2500_{0,12} \text{ (E)} \quad F = 2500 \left (\frac{(1 + 3\%)^{12} - 1}{3\%} \right ) \approx 35480
        $$

    - Materia prima ($F/A_3$)

        $$
        A_3 \rightarrow 13942_{0,12} \text{ (E)} \quad F = 13942 \left (\frac{(1 + 3\%)^{12} - 1}{3\%} \right ) \approx 197865
        $$

    - Ingresos ($F/A_4$)

        $$
        A_4 \rightarrow 21450_{0,12} \text{ (I)}
        $$

    $$
    F_{12} = 21450 \left (\frac{(1 + 3\%)^{12} - 1}{3\%} \right ) \approx 304419 \\[10 pt]


    \text{Ingresos} = 304419 - (14472 + 713 + 35480 + 197865) = 55889 * 10^3
    $$

3. Usted es dueño de un camión que opera realizando despachos para cierta compañía. Después de 12 años el camión demanda mayores costos de mantenimiento y reemplazo de piezas desgastadas, por lo que usted decide que en ese periodo reemplazará el camión por uno nuevo. El precio a hoy de ese camión es de $95000000. Para comprarlo dentro de 12 años usted decidió hacer un ahorro semestral en una entidad bancaria que le paga el 4.8% semestral. Si se considera que el precio del camión crece a una tasa del 3% anual, ¿cuál debe ser el monto de las cuotas semestrales del ahorro para comprar el vehículo de contado una vez pasen los 12 años?

    El precio del camion en 12 años ($F/P_0$) corresponde a

    $$
    F_{12} = 95000(1 + 3\%)^{12} \approx 135447
    $$

    > $12 \text{ años} = 24 \text{ semestres}$

    $$
    A = 135447 \left (\frac{4.8\%}{(1 + 4.8\%)^{24} - 1} \right ) \approx 3124 \text{ mil}
    $$

4. Una obligación que consta de tres pagarés así: $1200000 para hoy, $2000000 para dentro de 8 meses y $2350000 para dentro de un año, con una tasa de interés del 1.9% mensual.¿Cuál debe ser el valor de los pagos mensuales?

    > Debe sustituirse por su equivalente en pagos mensuales iguales durante el año.

    > Tenemos que llevar todo a los 12 meses.

    > $1 \text{ año} = 12 \text{ meses}$

    Monto total de la deuda

    - $F/P_0$

        $$
        F = 1200(1 + 1.9\%)^{12} \approx 1504
        $$

    - $F/P_8$

        $$
        F = 2000(1 + 1.9\%)^4 \approx 2156
        $$

    - $F/P_{12}$

        > Como ya está en el mes doce, no tenemos que hacer nada.

    $$
    F_{total} \approx 1504 + 2156 + 2350 = 6010 \\[10 pt]


    A = 6010 \left (\frac{1.9\%}{(1 + 1.9\%)^{12} - 1} \right ) \approx 450 * 10^3
    $$

5. Su hermana desea comprar un apartamento dentro de 10 años el cual tendrá un costo de $85600000. Para ayudarla, usted hoy le va a depositar en su cuenta una suma de $2500000 y dentro de 5 años le depositará el valor de $3100000 Adicionalmente su hermana decide hacer depósitos anuales empezando al final del año 1 y terminando al final del año 10. Si la tasa que paga el banco por los depósitos es del 15% anual, ¿cuánto debe ser el valor del ahorro anual que su hermana debe hacer para poder comprar el apartamento?

    - $F/P_0$

        $$
        F = 2500(1 + 15\%)^{10} \approx 10114
        $$

    - $F/P_5$

        $$
        F = 3100(1 + 15\%)^5 \approx 6235
        $$

    - $F_{total}$

        $$
        F \approx 85600 - (10114 + 6235) = 69225
        $$

    $$
    A = 69225 \left (\frac{15\%}{(1 + 15\%)^{10} - 1} \right ) \approx 3409 * 10^3

    $$

6. Determine la cuota anual fija que se pagaría por un crédito de $6800000 a 3 años en el cual se cobra una tasa del 16% anual el primer año, 18% anual el segundo año y 21% anual el tercero.

    $$
    A_1 = A_2 = A_3
    $$

    Vamos a llevar todo al presente

    $$
    6800 = A \left (\frac{1}{1.16} + \frac{1}{1.18 * 1.16} + \frac{1}{1.21 * 1.18 * 1.16}\right ) \quad A \approx \frac{6800}{2.2} \approx 3090  * 10^3
    $$

7. Su empresa desea adquirir los derechos de una mina de carbón cuya reserva geológica inicial se estima en 1.700.000 toneladas. Suponga que la tasa de extracción es de 170.000 $\frac{\text{ton}}{\text{año}}$. Se espera que la utilidad por tonelada de carbón durante cada año sea de $80.000. ¿Cuánto pagaría por dicha mina si usted desea obtener una rentabilidad del 22% anual en el negocio?

    La reserva se vaciaría en 10 años y cada año se generaría $170 * 80 = 13600$.

    $$
    P = 13600 \left (\frac{(1 + 22\%)^{10} - 1}{22\%(1 + 22\%)^{10}} \right ) \approx  53355 * 10^3
    $$

8. Construya la tabla de amortización para un crédito de $65000000 con las siguientes condiciones: pago de cuotas semestrales iguales durante 5 años a una tasa del 17.5% semestral.

    Una tabla de amortización tiene la siguiente estructura


    | Periodo  |             Saldo              |               Capital               |    Intereses    |  Cuota   |
    |:--------:|:------------------------------:|:-----------------------------------:|:---------------:|:--------:|
    |    1     |             $S_0$              |                                     |                 |          |
    |    2     | $S_{t - 1} - \text{Capital}_t$ | $\text{Cuota} - \text{Intereses}_t$ | $S_{t - 1} * i$ |          |
    | $\vdots$ |            $\vdots$            |              $\vdots$               |    $\vdots$     | $\vdots$ |
    |   $n$    |               0                |                                     |                 |          |


    Antes de empezar a hacer la tabla debemos hallar la anualidad

    > $5 \text{ años} = 10 \text{ semestres}$

    $$
    A = 65000 \left (\frac{17.5\%(1 + 17.5\%)^{10}}{(1 + 17.5\%)^{10} - 1} \right ) \approx 14207 * 10^3
    $$


    | Periodo |   Saldo   | Capital  | Intereses | Cuota |
    |:-------:|:---------:|:--------:|:---------:|:-----:|
    |    1    |   65000   |          |           | 14207 |
    |    2    |   62118   |   2832   |   11375   | 14207 |
    |    3    |  58790.4  |  3327.6  |  10879.4  | 14207 |
    |    4    | 54871.72  | 3918.68  | 10288.32  | 14207 |
    |    5    | 50267.271 | 4604.449 | 9602.551  | 14207 |
    |    6    |  44857.1  | 5410.23  |  8796.78  | 14207 |
    |    7    |  38500.1  |   6357   |   7850    | 14207 |
    |    8    |  31030.6  |  7469.5  |  6737.5   | 14207 |
    |    9    |  58790.4  |  3327.6  |   5430    | 14207 |
    |   10    | 54871.72  | 3918.68  | 10288.32  | 14207 |

9. Un artículo tiene un valor de contado de $585000 y puede adquirirse financiado con el siguiente plan: cuota inicial del 20% del valor del precio al contado, 18 cuotas mensuales iguales que se inician a pagar al final del mes 8 y un último pago por $80000 tres meses después de la última cuota mensual. Si la tasa de interés es del 2.28% mensual, hallar el valor de las cuotas uniformes mensuales.

    - cuota inicial del 20% del valor del precio al contado

        $$
        585000 * 20\% = 117000
        $$

    - un último pago por $80000 tres meses después de la última cuota mensual

        $$
        80000
        $$


    Entonces lo que queda por pagar es

    $$
    585000 - (117000 + 80000) = 388000
    $$

    - 18 cuotas mensuales iguales que se inician a pagar al final del mes 8

        $$
        A = 388000 \left (\frac{2.28\%}{(1 + 2.28\%)^{18} - 1} \right ) \approx 
        $$