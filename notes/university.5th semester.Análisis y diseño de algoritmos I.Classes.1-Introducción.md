---
id: e746wt81joca7ycv8m00xp7
title: 1-Introducción
desc: ''
updated: 1681502746772
created: 1679698445716
---

# Conocimientos previos

1. Un algoritmo es un **procedimiento computacional** que toma un valor o conjunto de valores como entrada y **produce** un valor o conjunto de valores como salida.

2. Un algoritmo es una secuencia de instrucciones precisas (no ambiguas) para resolver un problema.

- El rango de entradas del algoritmo debe ser definido cuidadosamente.

- El mismo algoritmo puede ser implementado de diferentes formas

- Pueden existir diferentes algoritmos para el mismo problema.

- Algoritmos para el mismo problema puede ser muy diferentes con respecto a la eficiencia.

![Design and analysis flow](./assets/University/An%C3%A1lisis%20y%20dise%C3%B1o%20de%20algoritmos%20I/1_1-1%20Design_and_analysis_flow.png)

En el análisis nos va a importar responder las siguientes preguntas

- ¿Cuánto espacio requiere?
- **¿Cuántas operaciones requiere?**

> Haremos más hincapié en la segunda.

# Pasos para el análisis de eficiencia de un algoritmo

1. Determinar el(los) parámetros(s) que indican el tamaño de la entrada.

2. Identificar la operación básica del algoritmo.

3. Verificar si el número de veces que se ejecuta la operación básica depende exclusivamente del tamaño de la entrada. En caso contrario, se tendrán que analizar el peor (mejor) caso o el caso promedio.

4. Definir una expresión matemática que represente el número de veces que la operación básica se ejecuta en el algoritmo.

5. Determinar una solución explicita para la expresión del punto anterior, y determinar su orden de crecimiento.

# Ejercicios

- 1
    ```
    Algoritmo Misterio (A[0 .. n-1])
    // Entrada: Un arreglo A[0..n-1]
    S ← 0
    for i ← 0 to n-1 do
        S ← A [i] + S
    return S
    ```

    |                              **Criterio**                               |         **valor**         |
    |:-----------------------------------------------------------------------:|:-------------------------:|
    | Tamaño de entrada                                                       | $n$                       |
    | Operación Básica                                                        | Línea 3                   |
    | Depende exclusivamente del tamaño de entrada                            | Si                        |
    | Expresión correspondiente al # veces que se ejecuta la operación básica | $\sum_{i = 0}^{n - 1} 1$  |
    | Forma explícita de la expresión                                         | $n$                       |
    | Orden de crecimiento                                                    | $O(n)$                    |

- 2

    ```
    Algoritmo ElementosUnicos (A[0 .. n - 1])
    // Determina si todos los elementos en un arreglo
    // son diferentes
    // Entrada: Un arreglo A[0..n - 1]
    // Salida: Retorna verdadero si todos los elementos
    // de A son diferentes, falso en caso contrario.
    diferentes ← verdadero
    for i ← 0 to n - 2 do
        for j ← i + 1 to n - 1 do
            if A[i] == A[j]
                diferentes ← falso
    return diferentes
    ```

    |                              **Criterio**                               |                     **valor**                     |
    |:-----------------------------------------------------------------------:|:-------------------------------------------------:|
    | Tamaño de entrada                                                       | $n$                                               |
    | Operación Básica                                                        | Línea 4                                           |
    | Depende exclusivamente del tamaño de entrada                            | Si                                                |
    | Expresión correspondiente al # veces que se ejecuta la operación básica | $\sum_{i = 0}^{n - 2} \sum_{j = i + 1}^{n - 1} 1$ |
    | Forma explícita de la expresión                                         | $\frac{n(n - 1)}{2} = \frac{n^2 - n}{2}$          |
    | Orden de crecimiento                                                    | $O(n^2)$                                          |


    Para hallar la forma explícita de la expresión podemos reemplazar en la sumatoria o hallar el comportamiento, encontraremos que las veces que se hace la comparación está dada por la sumatoria $\sum_{i = 1}^{n - 1} i$, reemplazando el límite superior en la fórmula para la sumatoria de Gauss tenemos finalmente que $f(n) = \frac{n(n - 1)}{2}$, también pudimos hallar esta expresión resolviendo la sumatoria

    > $f(n)$ es una función que dada una entrada de tamaño $n$ retorna cuantas instrucciones va a realizar el algoritmo.

    $$
    \sum_{j = i + 1}^{n - 1} 1 = (n - 1) - (i + 1) + 1 = n - i - 1 \quad \text{Reemplazando en la primera sumatoria} \\[10 pt]

    \sum_{i = 0}^{n - 2} n - i - 1 = (n - 0 - 1) + (n - 1 - 1) \dots (n - (n - 2) - 1)
    $$

- Una instancia es una entrada válida para el algoritmo.

- Correctitud
    Se dice que un algoritmo es **correcto**, si para cada instancia, el algoritmo termina con la salida correcta.

# Algoritmos

- 1

    ```
    primo(int n){
        if (n == 1)
            return 0;
        if (n % 2 == 0)
            return 0;
        else
            return 1;
    }
    ```

    Este algoritmo no es correcto, lo podemos demostrar con un contra ejemplo (para el 21 retorna que si es primo, pero este número es divisible por 3).

- 2

    ```
    primo(int n) {
        if (n == 1)
            return 0;
        else {
            int c = 0;
            for (int i = 2; i < n; i++)
                if (n % i == 0) c++;
            if (c == 0) return 1;
            else return 0;
        }
    }
    ```

    Este algoritmo es correcto, puesto que prueba con todos los números anteriores al número ingresado, para ver si lo dividen. Si llega hasta el final sin que lo haga algún número, el contador será 0, la definición de un número primo.

    > Obviamente, lo ideal es que la demostración sea formal.

# Tipos de problemas solucionados utilizando algoritmos eficientes

- Bioinformática: Identificar genes en secuencias de ADN (genoma humano 3200000000pb). Se almacena la información observada hasta el momento en bases de datos y se analizan con algoritmos que debe ser eficientes.

- Búsquedas en Internet: Dada la cantidad de información indexada, responder de forma correcta la solicitud de una búsqueda en Internet.

- Tratamiento de colisiones de objetos: Detectar una colisión entre dos cuerpos en un espacio 3D.

# Nuestra meta

**Comparar algoritmos que resuelven un mismo problema**.

- Correctitud

- Eficiencia

    - Tiempo

    - Espacio

- Estructuras de datos utilizadas

- Modelo computacional

- El tipo y número de datos con los cuales trabaja (escalabilidad)