---
id: 8v8scrq4poi38e6cr57y2qg
title: 7-Ordenes estadisticos
desc: ''
updated: 1682124519772
created: 1681772522536
---

# i-ésimo orden estadístico

El i-ésimo orden estadístico de un conjunto de $n$ elementos
es el i-ésimo elemento más pequeño.

---

- Mínimo: primer orden estadístico de un conjunto.

- Máximo: n-esimo orden estadístico de un conjunto de $n$
elementos.

- Mediana: $\frac{(n + 1)}{2}$ orden estadístico si $n$ es impar, en caso contrario se tienen dos medianas ($\left \lfloor \frac{(n + 1)}{2} \right \rfloor$ y $\left \lceil \frac{(n + 1)}{2} \right \rceil$).

---

El problema de encontrar el i-ésimo orden estadístico se
conoce como el **problema de selección**.

- Entrada: un conjunto $A$ de $n$ números diferentes y un
número $i$, tal que $1 \leq i \leq n$.

- Salida: el elemento $x \in A$, tal que es mayor que $i - 1$ elementos de $A$.

---

Para solucionar el problema en tiempo lineal esperado, se
utiliza la técnica de dividir y conquistar. Se utiliza el procedimiento [[`RANDOMIZED-PARTITION` |university.5th semester.Análisis y diseño de algoritmos I.Classes.6-Quick sort###versiones-aleatorias]] del Quicksort.

```
RANDOMIZED_SELECT(A, p, r, i)

    if p == r
        then return A[p]

    q <- RANDOMIZED-PARTITION(A, p, r)
    k <- q - p + 1

    if i <= k
        then return RANDOMIZED-PARTITION(A, p, q, i)
    else return RANDOMIZED-PARTITION(A, q + 1, r, i - k)
```

> A diferencia del Quicksort no se procede sobre ambos
lados de la partición, esto hace que se logre un tiempo de $\Theta(n)$ en lugar de $\Theta(n\lg n)$

## Complejidad

- Peor caso

    $$
    T(n) = T(n - 1) + \Theta(n) \quad T(n) = \Theta(n^2)
    $$


- Caso promedio

    $$
    T(n) = O(n)
    $$

    Aplicando análisis de esperanza utilizando variables aleatorias para los posibles subarreglos que se generan con las particiones.

Para hacer que en el pero caso la complejidad sea lineal, usamos el siguiente algoritmo sobre el procedimiento `PARTITION` modificado (para que reciba como parámetro el valor sobre el cual se hará la partición):

1. Dividir los n elementos del arreglo en $\left \lceil \frac{n}{5} \right \rceil$ grupos de 5 elementos y un grupo de $n % 5$ elementos.

2. Calcular la mediana de cada uno de los $\left \lceil \frac{n}{5} \right \rceil$ grupos (ordenar cada grupo y tomar el de la mitad).

3. Usar el algoritmo de selección recursivamente para calcular la
mediana $x$, de las $\left \lceil \frac{n}{5} \right \rceil$ medianas calculadas en 2.

4. Dividir el arreglo de entrada en 2 subarreglos utilizando
`PARTITION` modificado, para que el "pivote" sea $x$. La parte
izquierda de la partición tendrá $k$ elementos y la derecha $n - k$.

5. Utilice el algoritmo recursivamente para calcular el i-esimo orden estadístico de la parte izquierda de la partición si $i \leq k$ o el ($i - k$)-esimo de la parte derecha si $i > k$.

> El algoritmo termina cuando se haga un llamado para seleccionar un orden estadístico sobre un conjunto que tiene un solo elemento.

### Análisis

Suponga el caso en el que se tiene 29 elementos

- Número de grupos: $\left \lceil \frac{n}{5} \right \rceil = 6$

![Algorithm example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_7-1%20Algorithm-example.jpg)

![Algorithm example](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_7-2%20Algorithm-example.jpg)

Al menos la mitad de las medianas son menores o iguales a $x$. Por lo tanto, al menos la mitad de los grupos (2) contribuyen 3 elementos que son mayores que $x$, exceptuando el grupo donde está $x$ y el último grupo que puede no estar completo.

Se tiene entonces que el número de elementos mayores que $x$ es

$$
3 \left \lceil \frac{1}{2} \left \lceil \frac{n}{5} \right \rceil - 2 \right \rceil \geq 3\frac{n}{10} - 6
$$

#### Peor caso

$$
n - \frac{n}{10} - 6 = 7\frac{n}{10} + 6 \\[10 pt]

T(n) = T \left ( \left \lceil \frac{n}{5} \right \rceil \right ) + T \left (7\frac{n}{10} + 6 \right ) + O(n)
$$

Probando por sustitución $T(n) = T (\frac{n}{5}) + T(7\frac{n}{10}) + n$

![Recurrence expansion](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_7-3%20Recurrence-expansion.jpg)

vemos que la profundidad la marca el $7\frac{n}{10}$, además de que el término $n$ es el 90% del término anterior.

$$

\text{profundidad del árbol} \\[5 pt]

j = \log_{\frac{10}{7}} n \\[10 pt]

T(n) = \sum_{i = 0}^{j} n \left (\frac{9}{10} \right )^i = n \sum_{i = 0}^{j} \left ( \frac{9}{10} \right )^i = n * -10 \left ( \left (\frac{9}{10} \right )^{j + 1} - 1 \right ) \quad T(n) = O(n)
$$

Ahora debemos probar que

$$


$$