---
id: 5nzwlhvp2rt6h7fw3i7vmsh
title: 1-Sistemas formales
desc: ''
updated: 1704078741122
created: 1704050148895
---

## Introducción

- Sistema: realidad en la que ciertos elementos se agrupan por alguna razón que depende de un observador.

- Sistema formal: es un conjunto de elementos simbólicos que pueden manipularse
de manera adecuada para que reflejen una realidad deseada.

$$
\text{ Sistema formal } = \text{ lenguaje formal } + \text{ aparato deductivo }
$$

## Lenguaje formal

Con él se denotan los elementos de la realidad modelada. Consta de tres componentes:

1. Alfabeto: especifica que símbolos se utilizan en el lenguaje.

2. Sintaxis: indica como los símbolos pueden juntarse para constituir elementos del lenguaje.

	> Nos podríamos referir a estos elementos como fórmulas o palabras.

3. Semántica: significado a las palabras de un lenguaje.

### Alfabeto

Un alfabeto $A$ es un conjunto finito de símbolos, no vacío, usualmente entendido con alguna notación intuitiva.

### Sintaxis

- Una fórmula o palabra es una secuencia de $0$ o más símbolos del alfabeto.

- $A^*$ es el conjunto de todas las palabras posibles.

- $\empty$ es la fórmula sin símbolos.

- La **sintaxis** establece cuáles fórmulas están bien formadas: las que satisfacen las reglas.

### Lenguaje

Subconjunto de $A^*$, constituido por las fórmulas que la sintaxis establezca.

### Ejemplo (lenguaje)

- Alfabeto: $A = \{ x,y \}$.

- Regla sintáctica (en lenguaje natural): Una fórmula de $L$ es cualquier cadena finita de cero o más símbolos "x", seguidos por uno a tres símbolos "y", o una cadena de uno o más símbolos "x".

### Reglas sintácticas

#### Gramática BNF (Backus-Naur Form)

Una gramática BNF para $L$ es una cuádrupla $G = (A,N,\Sigma,P)$, donde:

- $A$ es el alfabeto del lenguaje $L$. Son los **símbolos terminales**.

- $N$ es un alfabeto de símbolos auxiliares, diferentes de los de $A$. Son los **símbolos no terminales**.

> $V = A \cup N$ es el alfabeto que reúne los símbolos terminales con los no terminales.

- $\Sigma$ es un elemento distinguido dentro de $N$. Se llama el **símbolo inicial**.

- $P$ es un conjunto de **producciones**.

- Una **producción** es una regla de la forma $\alpha \implies \beta$, $\alpha,\beta \in V^*$, $\alpha \notin A^*$.

- $L$ es el conjunto de fórmulas en $A^*$, derivables de $\Sigma$ por un número finito de producciones.

##### Notaciones para producciones o reglas $\alpha \implies \beta$

- $\alpha \implies \beta_1 | \beta_2 | \dots | \beta_n$ (conjunto de $n$ reglas).

	$$
	\alpha \implies \beta_1 \\[10 pt]

	\alpha \implies \beta_2  \\[10 pt]

	\vdots \\[10 pt]

	\alpha \implies \beta_n
	$$

- $\alpha \implies \beta_1[\gamma]$ (elementos opcionales).

	$$
	\alpha \implies \beta \quad \alpha \implies \beta \gamma
	$$

- $\alpha \implies \gamma^n$ (elementos repetidos $n$ veces).

	$$
	\alpha \implies \underbrace{ \gamma \gamma \dots \gamma }_n
	$$

- $\empty$ es la fórmula vacía.

- $\alpha \implies \gamma^*$ (elementos repetidos $0$ o más veces).

	$$
	\alpha \implies \empty \\[10 pt]

	\alpha \implies \gamma \alpha
	$$

- $\alpha \implies \gamma^+$ (elementos repetidos $1$ o más veces).

	$$
	\alpha \implies \gamma \\[10 pt]

	\alpha \implies \gamma \alpha
	$$

> Los símbolos no terminales diferentes de $\Sigma$ se distinguen porque se enmarcan en paréntesis angulares ($\langle \rangle$).

##### Ejemplo (gramática BNF)

Retomando el ![[ejemplo anterior |university.2nd semester.Matemáticas discretas I.Classes.1-Sistemas formales#ejemplo-lenguaje]], usando una gramática BNF podría modelarse de la siguiente forma:

$$
L \implies x^* y | x^* y y | x^* y y y | x^+
$$

Lo que es lo mismo que:

$$
P_1 : L \implies \langle L_1 \rangle \\[10 pt]

P_2 : L \implies \langle L_2 \rangle \\[10 pt]

P_3 : L \implies \langle L_3 \rangle \\[10 pt]

P_4 : L \implies \langle L_4 \rangle \\[10 pt]

P_5 : \langle L_1 \rangle \implies y \\[10 pt]

P_6 : \langle L_1 \rangle \implies x \langle L_1 \rangle \\[10 pt]

P_7 : \langle L_2 \rangle \implies y y \\[10 pt]

P_8 : \langle L_2 \rangle \implies x \langle L_2 \rangle \\[10 pt]

P_9 : \langle L_3 \rangle \implies y y y \\[10 pt]

P_{ 10 } : \langle L_3 \rangle \implies x \langle L_3 \rangle \\[10 pt]

P_{ 11 } : \langle L_4 \rangle \implies x \\[10 pt]

P_{ 12 } : \langle L_4 \rangle \implies x \langle L_4 \rangle \\[10 pt]
$$
