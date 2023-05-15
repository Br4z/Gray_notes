---
id: uatu1g57sxlustxl5t0uawn
title: '5-Ecuaciones diferenciales: fundamentos y aplicaciones'
desc: ''
updated: 1684092309200
created: 1684082306107
video_title: ECUACIONES DIFERENCIALES - Fundamentos y Aplicaciones | El Traductor
date: 2023-05-13
source: https://www.youtube.com/watch?v=MdKOjS8-oNw&t
---

# EDO 1er orden de variables separables

$$
{y}' - y = 0 \quad \frac{dy}{dx} = y \quad \frac{1}{y} dy = dx \\[10 pt]

\int \frac{1}{y} dy = \int dx \quad \ln y = x + c \quad e^{\ln y } = e^{x + c} \\[10 pt]

y = e^x * e^c \quad e^c = k \; k > 0 \quad y = ke^x \\[10 pt]
$$

Encontramos la familia de soluciones para la ecuación diferencial dada, si no hubieran impuesto una condición específica (como las condiciones iniciales) hubiéramos hallado una solución particular, por ejemplo:

$$
y(0) = 1 = ke^0 = k \quad y = e^x \text{ para la condición dada}
$$

## Ejemplo

Si tenemos que la tasa de crecimiento de una población es proporcional al tamaño de la población:

$$
\text{tasa de crecimiento} = c * \text{tamaño de la población} \\[10 pt]

\text{siendo un $P(t)$ el tamaño de la población en un instante $t$ tenemos} \\[5 pt]

\frac{dP}{dt} = \mu * P \quad \frac{1}{P} dP = \mu dt \quad \int \frac{1}{P} dP = \int \mu dt \\[10 pt]

\ln P = \mu (t + c) \quad e^{\ln P} = e^{\mu t + \mu c} \quad P = e^{\mu t} * e^{\mu c} \quad e^{\mu c} = k \; k > 0 \\[10 pt]

P = ke^{\mu t} \quad P(0) = ke^0 = k \text{ corresponde a la población inicial}
$$

# EDO homogénea

Decimos que una EDO ($g(x,y)$) es homogénea si cumple lo siguiente:

$$
g(tx,ty) = t^n g(x,y)
$$

> Donde $n$ corresponde al orden de homogeneidad.

## Ejemplo

- $g(x,y) = x^2 + xy$

    $$
    g(tx,ty) = (tx)^2 + (tx)(ty) = t^2 x^2 + t^2 xy = t^2(x^2 + xy) = t^2 g(x,y)
    $$

---

Si tenemos una ecuación de la forma:

$$
M(x,y) dx + N(x,y) dy = 0 \quad (1) \\[10 pt]

M(tx,ty) = t^n M(x,y) \quad N(tx,ty) = t^n N(x,y)
$$

y tanto $M$ como $N$ son ecuaciones homogéneas del mismo orden, diremos que la EDO es homogénea.

De la expresión $(1)$ podemos llegar a:

$$
\frac{dy}{dx} = -\frac{M(x,y)}{N(x,y)} = f(x,y) \quad (2) \\[10 pt]

f(tx,ty) = t^0 f(x,y) \; \forall t
$$

Ahora supongamos que nuestra $t$ es igual a $\frac{1}{x}$:

$$
f \left (\frac{1}{x}x,\frac{1}{x}y \right ) = f \left (1,\frac{y}{x} \right ) \quad (3) \\[10 pt]

z = \frac{y}{x} \quad xz = x\frac{y}{x} \quad xz = y \quad {xz}' = {y}' \\[10 pt]

dx z + x dz = dy \quad \frac{dx z + x dz}{dx} = \frac{dy}{dx} \quad z + x \frac{dz}{dx} = \frac{dy}{dx} \quad (4) \\[10 pt]

\text{igualando $(3)$ con $(4)$} \\[5 pt]

z + x \frac{dz}{dx} = f(1,z) \quad \frac{1}{f(1,z) - z} dz = \frac{1}{x} dx
$$

Una vez encontremos el valor de $z$ reemplazamos en el cambio de variable que hicimos para hallar $y$.

## Ejemplo

- $(x^2 - 2y^2) dx + xy dy = 0$

    Comprobamos que $M$ y $N$ sean homogénea del mismo orden:

    $$
    M(tx,ty) = (xt)^2 - 2(ty^2) = t^2 (x^2 - 2y^2) = t^2 M(x,y) \\[10 pt]

    N(tx,ty) = (tx)(ty) = t^2 (xy) = t^2 N(x,y)
    $$

    Como son homogénea, procedemos a solucionarla como una:

    $$
    \frac{dy}{dx} = -\frac{x^2 - 2y^2}{xy} \quad f(1,z) = \frac{2z^2 - 1}{z} \\[10 pt]

    z + x \frac{dz}{dx} = \frac{2z^2 - 1}{z} \quad x \frac{dz}{dx} = \frac{z^2 - 1}{z} \\[10 pt]

    \frac{z}{z^2 - 1} dz = \frac{1}{x} dx \quad \int \frac{z}{z^2 - 1} dz = \int \frac{1}{x} dx \\[10 pt]

    u = z^2 - 1  \quad du = 2z dz \quad z dz = z \frac{du}{2} \quad \int \frac{\frac{1}{2}du}{u} \\[10 pt]

    \frac{1}{2} \int \frac{1}{u} du = \frac{1}{2}\ln u = \frac{1}{2}\ln (z^2 - 1) + c_1 \\[10 pt]

    \frac{1}{2}\ln (z^2 - 1) + c_1 = \ln x + c_2 \quad \frac{1}{2}\ln (z^2 - 1) = \ln x + c_2 - c_1 \quad k = c_2 - c_1 \\[10 pt]

    \ln (z^2 - 1) = 2\ln x + 2k \quad z^2 - 1 = x^2 * e^{2k} \quad e^{2k} = k \; k > 0 \\[10 pt]

    z^2 = kx^2 + 1 \quad \left ( \frac{y}{x} \right )^2 = kx^2 + 1 \quad y^2 = kx^4 + x^2
    $$

    > Llegamos a una función implícita.

    Si reemplazamos en ${y}' = -\frac{x^2 - 2y^2}{xy}$, la ecuación debería cumplirse.

# EDO lineal de 1er orden

$$
{y}' + P(x)y = Q(x) \quad (1) \\[10 pt]

\frac{d}{dx} \left [e^{\int P(x) dx}y \right ] = e^{\int P(x) dx} * P(x)y + e^{\int P(x) dx} \frac{dx}{dy} \quad (2) \\[10 pt]

e^{\int P(x) dx} \left (\frac{dx}{dy} + P(x)y\right )
$$

Convenientemente, llegamos a una expresión relacionada con $(1)$.

$$
\text{multiplicamos por $e^{\int P(x) dx}$ a ambos lados de $(1)$} \\[5 pt]

e^{\int P(x) dx} \left ({y}' + P(x)y \right ) = e^{\int P(x) dx}Q(x) \quad (3) \\[10 pt]

\frac{d}{dx} \left [e^{\int P(x) dx}y \right ] = e^{\int P(x) dx}Q(x) \\[10 pt]

d \left [e^{\int P(x) dx}y \right ] = e^{\int P(x) dx}Q(x) dx \quad \int d \left [e^{\int P(x) dx}y \right ] = \int e^{\int P(x) dx}Q(x) dx \\[10 pt]

e^{\int P(x) dx} * y = \int e^{\int P(x) dx}Q(x) dx \quad y = \frac{\int e^{\int P(x) dx}Q(x) dx}{e^{\int P(x) dx}}
$$

## Ejemplo

Suponga la siguiente situación

$$
\text{siendo $y(t)$ la cantidad de sal en un instante $t$} \\[10 pt]

\text{variación de sal en el recipiente} = \text{sal entrante} - \text{sal saliente} \\[5 pt]

{y}' = v_1 c_1 - v_2 c_2 \\[10 pt]

\text{sal entrante} = \text{litros entrantes} * \text{cantidad de sal en los litros entrantes (concentración)} \\[10 pt]

\text{sal entrante} = 2 \frac{lt}{min} * 3 \frac{kg}{lit} = 6 \frac{kg}{min} \\[10 pt]

\text{sal saliente} = 3 \frac{lt}{min} * c_2 \\[10 pt]

c_2 = \frac{\text{cantidad de sal ($y(x)$)}}{\text{cantidad total (volumen)}} \\[10 pt]

\text{cantidad total (volumen)} = (v_1 - v_2)t + \text{cantidad inicial (volumen inicial)} \\[10 pt]

c_2 = \frac{y}{(v_1 - v_2)t + v_0} = \frac{y}{-t + 40} \\[10 pt]

{y}' = 6 - 3\frac{y}{-t + 40} \quad {y}' + \frac{3}{-t + 40}y = 6
$$

La ecuación a la que llegamos tiene la forma $(1)$.

$$
P(x) = \frac{3}{-t + 40} \quad Q(x) = 6 \\[10 pt]

\int \frac{3}{-t + 40} dt = 3\int \frac{1}{-t + 40} dt
\begin{array}{l}
    &u = -t + 40 \\
    &du = -dt
\end{array} \\[10 pt]

-3\ln (-t + 40) \quad e^{-3\ln (-t + 40) } = (-t + 40)^{-3} \\[10 pt]

\text{usando $(3)$ tenemos que} \\[5 pt]

e^{\int P(x) dx} \left ({y}' + \frac{3}{-t + 40}y \right ) = 6 e^{\int P(x) dx} \\[10 pt]

\text{retornando a la igualdad de $(2)$ tenemos que} \\[5 pt]

\frac{d}{dt} \left [(-t + 40)^{-3}y \right] = 6(-t + 40)^{-3} \quad d \left [(-t + 40)^{-3}y \right] = 6(-t + 40)^{-3} dt \\[10 pt]

\int d \left [(-t + 40)^{-3}y \right] = \int 6(-t + 40)^{-3} dt \\[10 pt]

\int d \left [(-t + 40)^{-3}y \right] = (-t + 40)^{-3}y \\[10 pt]

\int 6(-t + 40)^{-3} dt
\begin{array}{l}
    &u = -t + 40 \\
    &du = -dt
\end{array} -6 \int u^{-3} du \\[10 pt]

-6 \left (\frac{u^{-2}}{-2} + c \right ) = 3u^{-2} - 6c \quad -6c = k \quad 3(-t + 40)^{-2} + k \\[10 pt]

(-t + 40)^{-3}y = 3(-t + 40)^{-2} + k \quad y(t) = 120 - 3t + k(40 - t)^3 \\[10 pt]

\text{sabiendo que $y(0) = 0$ (al inicio solo hay agua pura), hallaremos $k$} \\[5 pt]

y(0) = 120 + 40^3k = 0 \quad k = -\frac{120}{40^3} = -\frac{3}{1600} \\[10 pt]

y(t) = 120 - 3t - \frac{3}{1600}(40 - t)^3 \\[10 pt]
$$

> La solución debería cumplir ${y}' = 6 - 3\frac{y}{-t + 40}$.
