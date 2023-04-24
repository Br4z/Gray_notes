---
id: tg0avgf47zow7x54q8ts639
title: 4-Funciones - Notación asintótica
desc: ''
updated: 1682216735184
created: 1679770959863
---

# Crecimiento de funciones

Siempre que se cumpla que $f(x) \geq g(x) \quad \forall x$ decimos que $f(x)$ es **cota superior** de $g(x)$.

> Como nuestro interés está en funciones $T(n)$ que retornan instrucciones **positivas** (de otra forma no tendrían sentido), solo tendremos en cuenta el primer cuadrante del plano cartesiano.

Dado que puede haber algunos valores (acotados) para los cuales $g(x) > f(x)$, ampliaremos la primera definición: para que una función sea cota superior de otra, debe serlo para **todos** los valores $x \geq k$ (pueden existir valore $x < k$ para los cuales no sea cota superior).

Ejemplo

- $f(x) = 2x \quad g(x) = x \rightarrow f(x) \text{ es cota superior de } g(x)$

---

Dadas dos funciones $f(x)$ y $g(x)$, se dice que $f(x) \; \text{es} \; O(g(x))$ si existen constante $c$ y $k$ tales que:

- $f(x) \leq c * g(x) \quad \forall x \geq k$

> Tanto $k$ como $c$ son constantes.

---

Ejemplo

- Tenemos las funciones $g(x) = x^2 \; f_1(x) = x \; f_2(x) = x^{\frac{1}{2}} \; f_3(x) = \log x$, podemos decir que

    - $f_1,f_2 \text{ y } f_3 \text{ son } O(g)$

    - $f_1 \text{ y } f_2 \text{ son } O(f_3)$

    - $f_1 \text{ es } O(f_2)$

---

Formalmente, la notación $O$ representa un conjunto de funciones

$$
O(g(x)) = \{f(x) \; | \text{ existen constantes positivas $c$ y $k$, tales que $0 \leq f(x) \leq c * g(x) \quad \forall x \geq k$}\}
$$

Ejemplo

- $O(x^2) = \{x,x^{\frac{1}{2}},\log x\}$

---

- Muestre que $7x^2 = O(x^3)$

    Esta igualdad la podemos traducir a $7x^2 \leq x^3 \rightarrow 7 \leq x$, por lo tanto, se cumple que $f(x) \leq 1 * g(x) \quad \forall x \geq 7$.

    > En este caso $c = 1 \; k = 7$

- Muestre que $x^3 \neq O(7x^2)$

    $x^3 \leq c * 7x^2 \rightarrow x \leq 7c$, no se cumple porque $\exists x \; | \; x > 7c$.

---

Que una función sea $O(1)$ significa que su cota superior es una constante.

## Cota superior asintótica

Cuando se determina que el tiempo de cómputo de un algoritmo es $O(g(x))$ se establece una **cota superior**.

Dentro del análisis para obtener la cota superior, se debe considerar el peor caso, de esta forma se consigue tener una cota que no puede resultar peor.

---

- Considere $T_1(n) = O(n^2) \quad T_2 = O(n\log n)$

    - ¿Qué se puede esperar en cuanto al tiempo de ejecución de los algoritmos?

        > Aunque formalmente un $O(n^2)$ incluya funciones de la forma $n\log n$, esperamos (como humanos) que describa el peor caso (aunque formalmente pueda ser una función de menor crecimiento).

        Esperamos que $T_2$ sea más rápido (haga menos instrucciones) que $T_1$.

    - ¿Se puede asegurar que siempre es mejor el algoritmo 2 que el 1?

        No

        > Por la anotación que di en la repuesta anterior.

Ejemplo

> [[Insertion sort|university.5th semester.Análisis y diseño de algoritmos I.Classes.2-Insertion sort]]

- Es una generalización decir que el tiempo de ejecución del insertion sort es $O(n^2)$, esto se puede asegurar, para el peor caso y caso promedio. Para el mejor caso se podría decir que es $O(n)$ (aunque $O(n)$ es $O(n^2)$).

## Cota inferior

$$
\Omega (g(x)) = \{ f(x) \; | \text{ existen constantes positivas $c$ y $k$, tales que $0 \leq c * g(x) \leq f(x) \quad \forall x \geq k$}\}
$$

---

- Considere $T_1 = \Omega (n^2) \quad T_2 = \Omega (n\log n)$

    - ¿Qué se puede esperar en cuanto al tiempo de ejecución de los algoritmos?

        Esperamos que $T_2$ sea más rápido (haga menos instrucciones) que $T_1$ (formalmente no es una condición).

## Notación $\theta(f(x))$

$$
f(x) = \theta(g(x)) \text{ si y solo si } f(x) = O(g(x)) \text{ y } f(x) = \Omega (g(x))
$$

## Notación $o$

$$
0(g(x)) = \{f(x) \; | \text{ para toda constante positiva $c$, existe una constante positiva $k$, tal que $0 \leq f(x) < c * g(x) \quad \forall x \geq k$}\}
$$

Ejemplo

- $2n^2 = O(n^2)$, pero $2n^2 \neq o(n^2)$

    > Se dice que la primera es asintóticamente ajustada.

## Notación $\omega$

$$
\omega (g(x)) = \{f(x) \; | \text{ para toda constante positiva $c$, existe una constante positiva $k$, tal que $0 \leq c * g(x) < f(x) \quad \forall x \geq k$}\}
$$

---

| **Complejidad** | **Terminología** |
|:---------------:|:----------------:|
| $O(1)$          | constante        |
| $O(\log n)$     | logarítmica      |
| $O(n)$          | lineal           |
| $O(n\log n)$    | $n \log n$       |
| $O(n^b)$        | polinomial       |
| $O(b^n)$        | exponencial      |
| $O(n!)$         | factorial        |

> $n$ es la entrada y $b$ una constante.

## Complejidades de los algoritmos

Existen problemas que no se pueden resolver, en el peor caso en tiempo polinomial, pero que dada alguna solución, se puede comprobar que es efectivamente una solución. Estos problemas se llaman **NP** (Polinómico – No determinista).

Existe un conjunto de problemas **NP**, que si se llegase a encontrar una solución en tiempo polinómico, daría solución a un conjunto de problemas relacionados. Este tipo de problema se conoce como **NP-completos**.

Ejemplo

- El problema de la **satisfactibilidad**

    Dada una asignación de valores de verdad, se puede verificar en tiempo polinómico si tal asignación satisface, o no, una fórmula proposicional. Sin embargo, no existe un algoritmo que en tiempo polinómico pueda encontrar la asignación de valores de verdad para que una fórmula cualquiera se satisfaga. Además, si se encontrara un programa que lograra hallar la solución en tiempo polinómico, se podría solucionar un conjunto de problemas relacionados con la lógica proposicional

    > Por lo que es un **NP-completo**.