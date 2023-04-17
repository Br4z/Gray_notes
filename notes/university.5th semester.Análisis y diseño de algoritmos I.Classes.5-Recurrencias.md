---
id: s73z7ehx9m2i5ujj0k36ety
title: 5-Recurrencias
desc: ''
updated: 1681672690331
created: 1679801949859
---

[[university.5th semester.Análisis y diseño de algoritmos I.Classes.2-Insertion sort#merge-sort]]

Para saber el costo computacional de estos algoritmos (divide y vencerás), tenemos que resolver recurrencias.

## Ecuaciones de recurrencia

Las ecuaciones de recurrencia permiten expresar el comportamiento computacional de un algoritmo recursivo. La solución de dichas ecuaciones permitirían determinar el costo computacional de estos algoritmos.

Existen diferentes métodos para solucionar ecuaciones de recurrencia:

### Iteración

Expandir la recurrencia y expresarla como una suma de términos que dependen de $n$ y de las condiciones iniciales.

Ejemplos

- $T(n) = n + 3T(\lfloor\frac{n}{4}\rfloor) \quad T(1) = \Theta (1)$

    > Normalmente, el argumento del llamado recursivo tiene un redondeo para asegurar que en algún momento llegue al caso base.

    $$
    n + 3 \left (\frac{n}{4} + 3T \left (\frac{n}{16} \right ) \right ) \quad (1) \\[10 pt]

    n + 3 \left (\frac{n}{4} + 3 \left (\frac{n}{16} + 3T \left (\frac{n}{32} \right ) \right ) \right ) \quad (2) \\[10 pt]

    n + 3\frac{n}{4} + 3^2\frac{n}{16} + 3^3\frac{n}{32} + 3^3T \left (\frac{n}{64} \right ) \quad (3)
    $$

    Con las 3 iteraciones anteriores ya empezamos a notar un patron.

    $$
    T(n) = n + 3\frac{n}{4} + \dots + 3^i\frac{n}{4^i} + T(1)
    $$

    > Donde $i$ en el número de la penúltima iteración.

    Ahora veamos cuando llega al caso base

    $$
    T(1) = \frac{n}{4^i} = 1 \quad n = 4^i \quad i = \log_4 n
    $$

    > $i$ en este caso significa última iteración.

    Entonces ahora sabemos cuando terminara

    $$
    T_i(n) = n + 3\frac{n}{4} + \dots + 3^i\frac{n}{4^i} + 3^{\log_4 n}\Theta(1) \\[10 pt]

    \text{$T_r \geq T_i$} \\[10 pt]

    T_i = n\sum_{j = 0}^{(\log_4 n) - 1} \left (\frac{3}{4} \right )^i + 3^{\log_4 n}\Theta(1) \\[10 pt]

    n \left (\frac{ \left (\frac{3}{4} \right )^{\log_4 n} - 1}{\frac{3}{4} - 1} \right ) + \Theta (n^{\log_4 3}) = 4n \left(1 - \left (\frac{3}{4} \right )^{\log_4 n} \right ) + \Theta (n^{\log_4 3}) \\[10 pt]

    {\color{Green} O(n)}
    $$

    > $T_r \geq T_i$ porque los redondeos originales eran al **piso**.

    > La serie se resolvió usando las propiedades de las [[series | math.Series]] geométricas.

- $T(n) = 2T(\frac{n}{2}) + 1 \quad T(1) = \Theta(1)$

    $$
    2 \left (2T \left (\frac{n}{4} \right ) + 1 \right ) + 1 \quad (1) \\[10 pt]

    2 \left (2 \left (2T \left (\frac{n}{8} \right ) + 1 \right ) + 1 \right ) + 1 \quad (2) \\[10 pt]

    T_i =  2^{i + 1}T \left (\frac{i}{2^{i + 1}} \right ) + \sum_{j = 1}^{i} 2^i + 1 \\[10 pt]

    \sum_{j = 1}^{i} 2^j + 1 = \sum_{j = 0}^{i} 2^j = \frac{2^{i + 1} - 1}{1} = 2^{i + 1} - 1 \\[10 pt]

    \text{Entonces dada el número de iteraciones ($i$) tenemos que} \\[5 pt]

    T_i = 2^{i + 1}T \left (\frac{n}{2^{i + 1}} \right ) + 2^{i + 1} - 1 \\[10 pt]

    \frac{n}{2^{i + 1}} = 1 \quad i = \log_2 n - 1 \\[10 pt]

    T(n) = nT \left (\frac{n}{2^{\log_2 n}} \right ) + n - 1 \\[10 pt]

    T(n) = n\Theta(1) + n - 1 \quad {\color{Green} O(n)}
    $$

- $T(n) = 2T(\frac{n}{2}) + n \quad T(1) = \Theta(1)$

    $$
    2 \left (2T \left (\frac{n}{4} \right ) + \frac{n}{2} \right ) + n \quad (1) \\[10 pt]

    2 \left (2 \left (2T \left (\frac{n}{8} \right ) + \frac{n}{4} \right ) + \frac{n}{2} \right ) + n \quad (2) \\[10 pt]

    T_i = 2^{i + 1}T \left (\frac{n}{2^{i + 1}} \right ) + (i + 1)n \\[10 pt]

    \frac{n}{2^{i + 1}} = 1 \quad i = \log_2 n - 1 \\[10 pt]

    T(n) = n\Theta(1) + n\log_2 n \quad {\color{Green} O(n\log_2 n)}
    $$

- $T(n) = 2T(\lceil\frac{n}{2}\rceil) + 1 \quad T(1) = \Theta(1)$

    > El argumento de $T$ se redondea al **techo**.

    La única diferencia con la primera es que como esta recurrencia está redondeada al techo, puede ser mayor o igual.

    $$
    T_i(n) = 2^{\log_2 n}T \left (\frac{n}{2^{\log_2 n}} \right ) + 2^{\log_2 n} - 1 \\[10 pt]

    T_r \geq T_i \\[10 pt]

    {\color{Green} O(T_r) \geq O(n\log_2 n)}
    $$

- Muestre que $2T(\lfloor\frac{n}{2}\rfloor) + n \quad T(1) = \Theta(1)$ es $\Omega(n\log n)$

    Usando como punto de partida la segunda recurrencia, podemos afirmar lo siguiente

    $$
    T_i(n) = 2^{\log_2 n}\Theta(1) + n\log_2 n \geq T_r \quad \text{por la función piso} \\[10 pt]

    {\color{Green} \Omega(n\log_2 n) \geq \Omega(T_r)}
    $$

- $T(n) = 2T(\frac{n}{2}) + n^2 \quad T(1) = \Theta(1)$

    $$
    2 \left (2T \left (\frac{n}{4} \right ) + \left (\frac{n}{2} \right )^2 \right ) + n^2 \quad (1) \\[10 pt]

    2 \left (2 \left (2T \left (\frac{n}{8} \right ) + \left (\frac{n}{4} \right )^2 \right ) + \left (\frac{n}{2} \right )^2 \right ) + n^2 \quad (2) \\[10 pt]

    T_i = 2^{i + 1}T \left (\frac{i}{2^{i + 1}} \right ) + \sum_{j = 0}^{i} 2^j \left ( \frac{n}{2^j} \right )^2 \\[10 pt]

    2^j \left ( \frac{n}{2^j} \right )^2 = 2^j\frac{n^2}{2^{2j}} = \frac{n^2}{2^j} = n^2\frac{1}{2^j} \quad n^2\sum_{j = 0}^{i} \left (\frac{1}{2} \right )^j =  2n^2 - \frac{n^2}{2^i} \\[10 pt]

    \frac{n}{2^{i + 1}} = 1 \quad i = \log_2 n - 1 \\[10 pt]

    T(n) = n\Theta(1) + 2n^2 - \frac{n^2}{2^i} \quad {\color{Green} O(n^2)}
    $$

- $T(n) = T(\frac{n}{3}) + T(\frac{2n}{3}) + n \quad T(1) = \Theta(1)$

    ![Recurrence expansion](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_5-1%20Recurrence-expansion.jpg)

    - $T(\frac{n}{3})$

        $$
        \left (\frac{1}{3} \right )^i n = 1 \quad \left (\frac{1}{3} \right )^i = \frac{1}{n} \quad 3^i = n \\[10 pt]

        \log_3 3^i = \log_3 n \quad i = \log_3 n
        $$

    - $T(\frac{2n}{3})$

        $$
        \left (\frac{2}{3} \right )^i n = 1 \quad \left (\frac{2}{3} \right )^i = \frac{1}{n} \quad \left (\frac{3}{2} \right )^i = n \\[10 pt]

        \log_{\frac{3}{2}} \left (\frac{3}{2} \right )^i = \log_{\frac{3}{2}} n \quad i = \log_{\frac{3}{2}} n
        $$

    Como $\log_{\frac{3}{2}} n > \log_3 n \quad n > 1$, diremos que la primera expresión define la "profundidad" del árbol, por lo que la expresión final es

    $$
    T(n) = n\log_{\frac{3}{2}} n
    $$

    Donde la primera $n$ hace referencia a la suma de los términos de cada nivel.


### Maestro

Permite resolver recurrencias de la forma

$$
T(n) = aT \left (\frac{n}{b} \right ) + f(n) \quad a \geq 0 \quad b > 1
$$

Dado que lo anterior se puede acotar asintóticamente como se comporta, tenemos las siguientes propiedades

$$

T(n) = \Theta(n^{\log_b a}) \quad (1) \\[5 pt]

\text{si } f(n) = O(n^{\log_b a - \epsilon}) \text{ para algún $\epsilon > 0$} \\[20 pt]

T(n) = \Theta(n^{\log_b a}\lg n) \quad (2) \\[5 pt]
\text{si } f(n) = \Theta(n^{\log_b a}) \\[10 pt]

T(n) = \Theta(n^{\log_b a}\lg^{k + 1} n) \quad (2) \\[5 pt]
\text{si } f(n) = \Theta(n^{\log_b a}\lg^k n) \text{ para algun $k \geq 0$} \\[20 pt]

T(n) = \Theta(f(n)) \quad (3) \\[5 pt]
\text{si } f(n) = \Omega(n^{\log_b a + \epsilon}) \text{ para algún $\epsilon > 0$ } \land \; af \left (\frac{n}{b} \right ) \leq cf(n) \text{ con } c < 1
$$

Ejemplos

- $T(n) = 9T \left (\frac{n}{3} \right ) + n$

    $$
    a = 9 \quad b = 3 \quad f(n) = n \\[10 pt]

    n^{\log_3 9} = n^3 \text{ forma $n^{\log_b a}$ que aparece en todos los casos} \\[10 pt]

    \text{si aplicamos el caso $(1)$, con $\epsilon = 1$ } n = O(n^{2 - 1}) = O(n) \\[10 pt]

    T(n) = n^2
    $$

- $T(\frac{2n}{3}) + 1$

    $$
    a = 1 \quad b = \frac{3}{2} \quad f(n) = 1 \\[10 pt]

    n^{\log_{\frac{3}{2}} 1} = n^0 = 1 \\[10 pt]

    \text{probando el caso $(1)$ nos daremos cuenta de que $\nexists(\epsilon > 0) \mid 1 = O(n^{0 - \epsilon})$} \\[10 pt]

    \text{si aplicamos el caso $(2)$} \\[5 pt]

    1 = O(1) \text{ por lo tanto } T(n) = \Theta(\lg n)
    $$

- $T(n) = 3T(\frac{n}{4}) + n\lg n$

    $$
    a = 3 \quad b = 4 \quad f(n) = n\lg n \\[10 pt]

    n^{\log_4 3} = n^{0.793} \\[10 pt]

    \text{comprobando los primeros dos casos, nos daremos cuenta de que no cumplen} \\[5 pt]

    n\lg n \neq O(n^{0.793 - \epsilon}) \quad  n\lg n \neq O(n^{0.793}) \\[10 pt]

    3 \left (\frac{n}{4} \right )\lg \frac{n}{4} \leq cn\lg n \quad \lg \frac{n}{4} = \lg n - \lg 4 = \lg n - 2 \\[10 pt]

    \left (\frac{3}{4} \right )n\lg n - 3 \left (\frac{n}{4} \right ) * 2 \leq cn\lg n \\[10 pt]

    \text{despreciamos el $3 \left (\frac{n}{4} \right ) * 2$ por tener menor tasa de crecimiento} \\[10 pt]

    \left (\frac{3}{4} \right )n\lg n \leq cn\lg n \quad c = \frac{3}{4} \quad T(n) = \Theta(n\lg n)
    $$

- $2T(\frac{n}{2}) + n\lg n$

    $$
    a = 2 \quad b = 2 \quad f(n) = n\lg n \\[10 pt]

    n^{\log_2 2} = n \\[10 pt]

    \text{aplicando el caso $(2)$} \\[5 pt]

    f(n) = \Theta(n\lg n) \text{ donde $k = 1$} \quad T(n) = \Theta(n\lg^2 n)
    $$

- $4T(\frac{n}{2}) + n$

    $$
    a = 4 \quad b = 2 \quad f(n) = n \\[10 pt]

    n^{\log_2 4} = n^2 \\[10 pt]

    \text{aplicando el caso $(1)$} \\[5 pt]

    f(n) = O(n^{2 - 1}) \quad f(n) = n \quad \epsilon = 1 \quad T(n) = n^2
    $$

- $4T(\frac{n}{2}) + n^2$

    $$
    a = 4 \quad b = 2 \quad f(n) = n^2 \\[10 pt]

    n^{\log_2 4} = n^2 \\[10 pt]

    \text{aplicando el caso $(2)$} \\[5 pt]

    f(n) = \Theta(n^2) \quad T(n) = \Theta(n^2\lg n)
    $$

- $4T(\frac{n}{2}) + n^3$

    $$
    a = 4 \quad b = 2 \quad f(n) = n^3 \\[10 pt]

    n^{\log_2 4} = n^2 \\[10 pt]

    \text{aplicando el caso $(3)$} \\[5 pt]

    f(n) = \Omega(n^{2 + 1}) = \Omega(n^3) \text{ con $\epsilon = 1$} \quad 4 \left (\frac{n}{2} \right )^3 \leq cn^3 \\[10 pt]

    \frac{1}{2}n^3 \leq cn^3 \quad c = \frac{1}{2} < 1 \quad T(n) = \Theta(n^3)
    $$

### Sustitución

Suponer la forma de la solución y probar por inducción matemática.

- Se empieza conjeturando cuál puede ser la solución de la ecuación de recurrencia a partir de la similitud de esta con otra cuya solución es conocida.

- Se demuestra por inducción matemática que la ecuación tiene dicha solución.

Ejemplo

- $T(n) = 2T \left ( \lfloor \frac{n}{2} \rfloor \right ) + n \quad T(1) = 1$

    Tengamos en cuenta un $T'(n)$ tal que

    $$
    T'(n) = 2T \left (\frac{n}{2} \right ) + n \quad T'(1) = 1 \\[10 pt]

    T'(n) = O(n\log n)
    $$

    Vamos a suponer que $T(n) = T'(n) = O(n\log n)$, en concreto vamos a demostrar (por inducción) que $T(n) \leq cn\log n$

    - Caso inductivo

        Si se cumple la propiedad para $T \left ( \lfloor \frac{n}{2} \rfloor \right )$, entonces se cumple para $T(n)$.

        > Se supone que se cumple para $\lfloor \frac{n}{2} \rfloor$ y se prueba para $n$.

        $$
        \text{Si } T \left ( \left \lfloor \frac{n}{2} \right \rfloor \right ) \leq c \left \lfloor \frac{n}{2} \right \rfloor \lg \left \lfloor \frac{n}{2} \right \rfloor \text{ entonces } T(n) \leq cn\log n
        $$

    - Hipótesis inductiva: $T \left ( \left \lfloor \frac{n}{2} \right \rfloor \right ) \leq c \left \lfloor \frac{n}{2} \right \rfloor \lg \left \lfloor \frac{n}{2} \right \rfloor$


    - Paso inductivo

        $$
        \begin{align*}
        T(n) &\leq 2 \left (c \left \lfloor \frac{n}{2} \right \rfloor \lg \left \lfloor \frac{n}{2} \right \rfloor \right ) + n \\[5 pt]

        &\leq cn\lg \left \lfloor \frac{n}{2} \right \rfloor\\[5 pt]

        &= cn\lg n - cn + n \text{ para $c \geq 1$}\\[5 pt]

        &\leq cn\log n
        \end{align*}
        $$

        > Se reemplazó $T(\lfloor \frac{n}{2} \rfloor)$ por la hipótesis.

    - Caso base

        Si $c = 1$, probar que $T(1)$ se cumple

        $$
        T(1) \leq 1 * 1\lg 1 \quad 1 \leq 0
        $$

        > No se cumplió.

        Si $c = 2$

        $$
        T(1) \leq 2 * 1\lg 1 \quad 1 \leq 0
        $$

        > Tampoco cumplió.

        Calculemos $T(2)$ para tomarlo como valor inicial

        $$
        T(2) = 2T(1) + 2 = 4
        $$

        Ahora probemos $c = 3$ con el nuevo valor inicial

        $$
        T(2) \leq 3 * 2\lg 2 \quad 4 \leq 6
        $$

        Como se demostró que $T(n) \leq cn\lg n \quad \forall n \geq 2$, se concluye que $T(n) = O(n\log n)$