---
id: ljsoptep3rgso5dw5rhzku0
title: Logarithms
desc: ''
updated: 1680307868518
created: 1680033150761
---

# Implicación fundamental

$$
\log_b a = c \rightarrow b^c = a \quad b,a \in \mathbb{R} > 0
$$

# Propiedades

$$
{\color{Yellow} b} \; {\color{Green} a} \; {\color{Red} c} \\[20 pt]

\log_b b = 1 \rightarrow b^1 = b \quad (1)\\[20 pt]

\log_b 1 = 0 \rightarrow b^0 = 1 \quad (2) \\[20 pt]

{\color{Yellow} b}^{\color{Red} {\log_b a}} = {\color{Green} a} \rightarrow \log_b a = \log_b a \quad (3) \\[20 pt]

\log_{\color{Yellow} b} {\color{Green} a^n} = {\color{Red} n * \log_b a} \quad (4) \\[10 pt]

b^{n\log a} = a^n \quad a^n = (b^{\log a})^n \quad a^n = a^n \\[20 pt]

\log_b ac = \log_b a + \log_b c \quad (5) \\[10 pt]

\begin{array}{lr}
    p = \log_b a & q = \log_b c \\[5 pt]
    a = b^p      & c = b^q
\end{array} \\[10 pt]

\log_b b^p * b^q = \log_b b^{p + q} \\[10 pt]

(p + q)\log_b b = p + q = \log_b a + \log_b c \\[20 pt]

\log_b \frac{a}{c} = \log_b a - \log_b c \quad (6) \\[10 pt]

\log_b ac^{-1} = \log_b a + \log_b c^{-1} = \log_b a - \log_b c \\[20 pt]


\log_b a = \frac{\log_c a}{\log_c b} \quad b \neq 1 \quad (7) \\[10 pt]

\log_c a = \log_c b^c \text { se puede hacer porque $\log$ es una función inyectiva} \\[10 pt]

\log_c a = c\log_c b \quad \log_c a = \log_b a\log_c b \quad \log_b a = \frac{\log_c a}{\log_c b} \\[20 pt]


n^{\log_y x} = x^{\log_y n} \quad \{n,x,y\} \in \mathbb{N} \; \land \; y \neq 1 \quad (8) \\[10 pt]

\log_y(n^{\log_y x}) = \log_y(x^{\log_y n}) \quad \log_y x \cdot \log_y n = \log_y n \cdot \log_y x \\[10 pt]

\text{Dividimos ambos lados por $\log_y n \neq 0$} \\[10 pt]

\frac{\log_y x \cdot \log_y n}{\log_y n} = \frac{\log_y n \cdot \log_y x}{\log_y n} \quad \log_y x = \log_y x
$$