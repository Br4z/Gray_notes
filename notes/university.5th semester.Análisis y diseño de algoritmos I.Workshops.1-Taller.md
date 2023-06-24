---
id: 6hcxyqh7qqvama9ratymseq
title: 1-Taller
desc: ''
updated: 1687223593735
created: 1682868818070
---

1. .

    > La operación básica en los siguientes algoritmos son las líneas `print("Hola Mundo")`.

    - `funcion1(n)`

        ```
        for(i = 2; i <= 4; i = i * i)
            print("Hola Mundo")

        for(i = 1; i <= n; i = i * 4)
            print("Hola Mundo")
        ```

        El primer `for` tiene un costo asociado de 2. Si no hubiera, sido constante sino acotado por `n`, es decir, `for(i = 2; i <= n; i = i * i)`, la expresión que retorna las veces que se imprimiría el "Hola Mundo" es:

        $$
        n^{\frac{1}{2^i}} = 2 \quad \frac{1}{2^i}\lg n = 1 \quad 2^i = \lg n \quad i = \lg \lg n \\[10 pt]

        T(n) = \lg \lg n + 1
        $$

        El costo del segundo `for`está dado por la expresión:

        $$
        1 * 4^i = n \quad 4^i = n \quad i = \log_4 n
        $$

        $$
        T(n) = \left (\log_4 n + 1 \right ) + 2 = \Theta(\log n)
        $$

        - $\log_4 n + 1$: veces que se imprime el "Hola Mundo".
        - $2$: costo constante asociado.

    - `funcion2(n)`

        ```
        for(i = 1; i <= n; i = i * 2)
            for(j = 1; j <= n; j = j + j)
                print("Hola Mundo")
        ```

        Las veces que se itera sobre el primer `for` está dada por la expresión:

        $$
        1 * 2^i = n \quad 2^i = n \quad i = \log_2 n
        $$

        Las veces que se itera sobre el segundo `for` está dada por la expresión:

        > Sabiendo que `for(j = 1; j <= n; j = j + j)` es igual a `for(j = 1; j <= n; j = j * 2)`.

        $$
        1 * 2^i = n \quad 2^i = n \quad i = \log_2 n
        $$

        Como los bucles están anidados, terminamos con la sumatoria:

        $$
        \sum_{i = 1}^{\log_2 n + 1} (\log_2 n + 1) = (\log_2 n + 1) (\log_2 n + 1 - 1) = (\log_2 n + 1) (\log_2 n)
        $$

        $$
        T(n) = (\log_2 n + 1) (\log_2 n) = \Theta((\log_2 n)^2)
        $$

        - `funcion3(n)`

            ```
            if (n == 1)
                print("Hola Mundo")
            else
                print("Hola Mundo")
                funcion3(n / 2)
                funcion3(n / 2)
            ```

            $$
            T(n) = 2 \left (\frac{n}{2} \right ) + 1 \quad T(1) = 1 \\[10 pt]

            n^{\log_2 2} = n^1 = n \quad \text{Caso 1 del método maestro} \\[10 pt]

            T(n) = \Theta(n)
            $$

        - `funcion4(n)`

            ```
            if (n == 1)
                print("Hola Mundo")
            else
                print("Hola Mundo")
                for(j = 1; j <= 3; j = j + 1)
                    funcion4(n / 3)
            ```

            $$
            T(n) = 3T \left (\frac{n}{3} \right ) + 2 \quad T(1) = 1 \\[10 pt]

            n^{\log_3 3} = n^1 = n \quad \text{Caso 1 del método maestro} \\[10 pt]

            T(n) = \Theta(n)
            $$

2. ```program misterio(a[1,...,n])```

    ```
    1  - n = a.length;
    2  - aux1 = a[1];
    3  - aux2 = a[1];
    4  - k = 2

    5  - while (k <= n)
    6  -   if (a[k] > (aux1 + a[k]))
    7  -        aux1 = a[k];
    8  -    else
    9  -       aux1 = aux1 + a[k]

    10 -    if (aux2 > aux1)
    11 -        aux2 = aux1;

    12 - k++;
    13 - return aux2;
    ```

    > Asuma que la entrada es una arreglo de `n` enteros, ordenados descendentemente y negativos.

    - ¿Cuál es el número máximo(mínimo) de veces que se podría ejecutar la asignación de la línea 7?

        Por la naturaleza de la entrada, el programa nunca entrará en el `else`, por lo que siempre se hará $n - 1$ veces.

        La razón por la que pasa esto, es que al ser un arreglo de la forma:

        $$
        [a_1,a_2,\dots,a_n] \text{ donde } a_1 > a_2 > \dots > a_{n - 1} > a_n
        $$

        con un estado inicial:

        $$
        a_k = a_2 \quad \text{aux}_1 = a_1 \quad \text{aux}_2 = a_1
        $$

        podemos demostrar que siempre se cumple la condición de la línea 8

        $$
        a_k > \text{aux}_1 + a_k \quad a_2 > a_1 + a_2 \text{ para el estado inicial}
        $$

        lo que asegura la siguiente trasformación:

        $$
        a_k = a_{k + 1} \quad \text{aux}_1 = a_k \quad \text{aux}_2 = a_{k - 1} \\[10 pt]

        \text{para el estado inicial} \\[5 pt]

        a_3 = a_{2 + 1} \quad \text{aux}_1 = a_2 \quad \text{aux}_2 = a_2 \\[10 pt]

        \text{como $\text{aux}_1$ es negativo podemos asegurar } a_3 > \text{aux}_1 + a_3 \\[10 pt]

        \text{por lo anterior podemos asegurar que siempre } a_k > \text{aux}_1 + a_k
        $$

        > El - 1 es porque `k` empieza en 2.

    - ¿Cuál es el número máximo de veces que se podría ejecutar la asignación de la línea 11?

        Su número máximo de ejecuciones es $n - 1$ veces, porque:

        $$
        \text{aux}_1 = a_k \quad \text{aux}_2 = a_{k - 1} \quad a_{k - 1} \leq a_k
        $$

        > Como la condición no contempla el caso en el que sean iguales, no se ejecuta la asignación.

    - ¿El valor que retornar el programa a qué corresponde según el arreglo de entrada?

        Corresponde al último ($n$) elemento del arreglo, porque la condición enunciada en el punto anterior nos asegura que $\text{aux}_2$ sea igual $a_k$ al final de una iteración.

        > En términos estrictos no sería el último elemento, pero no haremos esa diferenciación.

3. ```program misterio(a, b)```

    ```
    if b == 0
        return 1
    if b == 1
        return a
    if even(b)
        c = misterio(a, piso(b / 2))
        return c * c
    else
        c = misterio(a, piso(b / 2))
        return c * c * a
    ```

    - Indique qué relación existe entre la salida y los parámetros de entrada del algoritmo.

        El programa retorna $a^b$.

        - Casos bases:

            - $a^0 = \text{misterio}(a, 0) \quad 1 = 1$
            - $a^1 = \text{misterio}(a, 1) \quad a = a$

        - Hipótesis:

            Diremos que nuestro programa funciona correctamente para valores enteros de $b$ desde 1 hasta $k$, entonces también diremos que funciona para un valor $n$ tal que $n = k + 1$:

            $$
            a^n = \text{misterio}(a,n) = a^{k + 1}
            $$

            Para demostrar el enunciado anterior debemos considerar los dos casos faltantes

            - `even(b)`

                $$
                c = a^{\lfloor \frac{n}{2} \rfloor} = a^{\frac{n}{2}} = a^{\frac{k + 1}{2}}
                $$

                Como $\frac{k + 1}{2} \in [1,k]$ podemos decir que calcula $c$ correctamente. Finalmente retorna:

                $$
                a^{\frac{n}{2}} * a^{\frac{n}{2}} = a^{2\frac{n}{2}} = a^n
                $$

            - `!even(b)`

                $$
                c = a^{\lfloor \frac{n}{2} \rfloor} = a^{\frac{n - 1}{2}} = a^{\frac{(n - 1) + 1}{2}} = a^{\frac{k}{2}}
                $$

                Como $\frac{k}{2} \in [1,k]$ podemos decir que calcula $c$ correctamente. Finalmente retorna:

                $$
                a^{\frac{n - 1}{2}} * a^{\frac{n - 1}{2}} * a = a^{2\frac{n}{2}} = a^{\frac{2n - 2}{2}} * a = a^{n - 1} * a = a^n
                $$

    - ¿Cuál es el mínimo número de veces que se ejecuta la línea 7? ¿En qué caso ocurre?

        0 veces en el caso de `misterio(a, 0) y misterio(a, 1)` (cuando entra en el primer y segundo condicional respectivamente).

        > En los otros casos no podemos asegurar que $\lfloor \frac{b}{2} \rfloor$ sea par o impar.

    - ¿Cuál es el máximo número de veces que se ejecuta la línea 7? ¿En qué caso ocurre?

        Con $b = 2^i \; i \in \mathbb{N}$ (potencias de 2) son los únicos números en los que podemos asegurar que $\lfloor \frac{b}{2} \rfloor$ sea par. Diremos que el número máximo de veces que se puede ejecutar la línea está dada por la expresión $i = \lg n$.

    - ¿Cuál es la complejidad del algoritmo?

        Tomaremos $n$ como $b$, puesto que dependiendo de su tamaño el algoritmo hará más o menos llamados recursivos.

        $$
        T(n) = T \left ( \left \lfloor \frac{n}{2}  \right \rfloor \right ) + O(1) \quad T(1) = 1
        $$

        > El $O(1)$ asociado a las instrucciones de la función `even`.

        A la relación encontrada no podemos aplicarle el método maestro, por lo que propondremos una parecida:

        $$
        T(n) = T \left (\frac{n}{2} \right ) + O(1) \\[10 pt]

        \text{Dada una iteración $i$ tenemos} \\[5 pt]

        T_1(n) = T_1 \left (\frac{n}{2^i} \right ) + iO(1)\\[10 pt]

        \frac{n}{2^i} = 1 \quad i = \lg n \quad T_1(n) = T_1(1) + \lg n * O(1) \\[10 pt]

        T_1(n) = O(\lg n)
        $$

        Ahora lo siguiente es demostrar la siguiente desigualdad:

        $$

        \begin{align*}
        T(n) &\leq c\lg \frac{n}{2} + O(1) \\
             &\leq c\lg n - c\lg 2 + O(1) \quad O(1) = c\\
             &\leq c\lg n
        \end{align*}
        $$

        Puesto que $T(1) \geq c * 0$ debemos cambiar el caso base

        $$
        T(2) = T(1) + 1 * O(1) = 1 \quad O(1) = 1 \\[10 pt]

        T(2) \leq 2 * \lg 2
        $$

        > Vemos que se cumple con $c = 2$.

        Como se demostró que:

        $$
        T(n) \leq c\lg 2 \quad \forall {n \geq 2} \quad \therefore T(n) = O(\lg n)
        $$

4. `sort(a[1,..., n])`

    ```
    1 - for(i = 1; i <= n - 1; i = i + 1)
    2 -     min = i

    3 -    for(j = i + 1; j <= n; j = j + 1)
    4 -        if a[j] < a[min]
    5 -            min = j

    6 -    intercambiar(a[min], a[i])
    ```

    > El algoritmo ordena ascendentemente.

    - Identifique una línea básica adecuada y determine su complejidad. Determine si existe un peor y mejor caso.

        Tomando la comparación que hace la línea 4 como operación básica tenemos:

        $$
        \sum_{i = 1}^{n - 1} \sum_{j = i + 1}^{n} 1 = \sum_{i = 1}^{n} i = \frac{n(n + 1)}{2} \quad T(n) = O(n^2)
        $$

    - Determine si este algoritmo es estable asumiendo que puede haber elementos repetidos en el arreglo de entrada

        El algoritmo no es estable, pues no se cumple para las entradas

5. Modifique el algoritmo visto en clase para determinar un orden estadístico de tal forma que se organicen en grupos de tamaño 9 (en lugar de tamaño 5). Realice el respectivo análisis de algoritmo y determine cuál sería su respectivo orden de complejidad.
