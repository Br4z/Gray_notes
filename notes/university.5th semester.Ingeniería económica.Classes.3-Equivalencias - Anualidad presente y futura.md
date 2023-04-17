---
id: bthqfbmkjdl3u44lhgu7u20
title: 3-Equivalencias - Anualidad presente y futura
desc: ''
updated: 1681009586042
created: 1681004747109
---

# Objetivos

- Determinar la suma futura equivalente a una serie de ingresos o egresos **periódicos y uniformes**.

- Determinar el monto de una serie de ingresos o egresos **periódicos y uniformes** equivalente a una suma futura.

$$
F = A(1 + i)^{n - 1} +  A(1 + i)^{n - 2} + \dots + A(1 + i) + A \quad (1) \\[10 pt]

\text{multiplicamos por $(1 + i)$ en ambos lados} \\[5 pt]

F(1 + i) = A(1 + i)^n +  A(1 + i)^{n - 1} + \dots + A(1 + i)^2 + A(1 + i) \quad (2) \\[10 pt]

\text{restamos $(1)$ a $(2)$} \\[5 pt]

F * i = A(1 + i)^n - A \\[10 pt]

F = A \left (\frac{(1 + i)^n - 1}{i} \right ) \quad A = F \left (\frac{i}{(1 + i)^n - 1} \right ) \quad (3)
$$

> La primera igualdad de $F$ representa una anualidad en la que los pagos iguales se invierten a interés compuesto y se acumulan para generar un valor futuro total.

> La fórmula de valor futuro de una anualidad asume que los pagos se reciben al final de cada período.

# Ejemplos

- Una familia con un hijo recién nacido decide iniciar un fondo de ahorros para cubrir los costos de la educación universitaria de su hijo. Para esto ahorrarán su dinero en una cuenta que les ofrece un pago del **30% anual**.

    Si se espera que el hijo inicie su vida universitaria a los **18 años** y que el dinero requerido en ese momento sea de $45000000, ¿cuál debe ser el valor de la **cuota anual uniforme** que debe depositar la familia?

    $$
    A = 45000000 \left (\frac{0.3}{(1 + 0.3)^{18} - 1} \right ) \approx 121125
    $$

- Una persona próxima a ingresar a la universidad se da cuenta de que requerirá $6000000 semestrales al final de cada uno de los semestres para poder continuar con sus estudios. Cierta entidad crediticia le ofrece cubrir su necesidad de dinero con una tasa del **4% semestral**.

    La persona acude a usted como analista con las siguientes preguntas

    - ¿A cuánto ascenderá la deuda una vez transcurran los **10 semestres** de la carrera?

        $$
        F = 6000000 \left (\frac{(1 + 0.04)^{10} - 1}{0.04} \right ) \approx 72036643
        $$

    - ¿Cuál sería el valor de la deuda al final del décimo semestre, si recibiera los $6000000 al **inicio** de cada semestre?


        > Podemos usar la fórmula de valor futuro de una anualidad anticipada.

        $$
        F = A \left (\frac{(1 + i)^n - 1}{i} \right ) (1 + i)
        $$


        $$
        F = 6000000 \left (\frac{(1 + 0.04)^{10} - 1}{0.04} \right ) (1 + 0.04)\approx 74918
        $$

---

Para $(3)$ podemos hallar otras fórmulas sabiendo que $F_n = P(1 + i)^n$

$$
P(1 + i)^n = A \left (\frac{(1 + i)^n - 1}{i} \right ) \quad P = A \left (\frac{(1 + i)^n - 1}{i(1 + i)^n} \right ) \quad A = P \left (\frac{i(1 + i)^n}{(1 + i)^n - 1} \right )
$$

# Ejemplos

- Una persona recibió el día de hoy un premio de lotería por $20000000 y decidió depositarlo en una cuenta de ahorros que le garantiza el **26% anual**.

    - ¿Qué cantidad de dinero anual podría retirar al final de cada uno de los próximos **20 años**, de manera tal que al hacer el retiro número 20 su cuenta quede en cero?

        $$
        A = 20000000 \left (\frac{26\%(1 + 26\%)^{20}}{(1 + 26\%)^{20} - 1} \right ) \approx 5251628
        $$

- Una empresa desea conocer cuál es el monto máximo que puede invertir hoy para reparar una de sus máquinas.

    - Si la máquina es reparada, esta mejoraría su rendimiento y generaría ingresos adicionales de $20000 **anuales** durante **5 años**.

    - Si en lugar de reparar la máquina el dinero se invirtiera otro negocio, se podría obtener una rentabilidad de **15% anual**.

    ¿Cuál es el valor máximo a invertir en la reparación de la máquina?

    $$
    P = 20000 \left (\frac{(1 + 15\%)^5 - 1}{15\%(1 + 15\%)^5} \right ) \approx 67043
    $$