<h1 align='center'>Ayudantía 1  - Fundamentos de la Computación</h1>
<h5 align='center'>Profesor: Cristobal Montaño<br>  Ayudante: Paulo Araya</h5>
<h6 align='center'>13 de Septiembre de 2026</h6>

## Tecnicas de Demostración:

> Demuestre (o refute) los siguientes enunciados utilizando inducción:

A. Para todo $n \geq 0 \land n \in N$, se cumple la siguiente formula: $n^4 -4n^2 \bmod 3 = 0$. 
Es decir, cualquier numero generado por esta formula es un multiplo de 3.

B. La siguiente formula funciona para cualquier $n \geq 0 \land n \in N$:	
$$
1\cdot 2 \cdot 3 + 2\cdot 3 \cdot 4 + \cdots + n \cdot (n + 1) \cdot (n+2) = \frac{n \cdot (n + 1) \cdot (n + 2) \cdot (n + 3)}{4}
$$

C. Para todo $n \geq 0 \land n \in N$, se cumple que el resultado de $n^2 + n + 41$ es primo.

> Demuestre los siguientes enunciados utilizando el argumento de diagonalización de Cantor:

A. Demuestre que el conjunto de todos los números reales en el intervalo $(0, 1)$ representados en base 10 es no numerable.

B. Demuestre que el conjunto de todas las secuencias infinitas formadas por el alfabeto $\Sigma = \{a, b, c\}$ es no numerable.
## Lenguajes:

A. Defina por extension el siguiente lenguaje:
$$
L_2 = \{x\in \{0,1\}^* : \text{x termina en 1} \land |x| \leq 4\}
$$
$$
L_2 = \{1,\ 01,\ 11,\ 001,\ 011,\ 101,\ 111,\ 0001,\ 0011,\ 0101,\ 0111,\ 1001,\ 1011,\ 1101,\ 1111\}
$$
B. Del siguiente alfabeto, escriba, por extension, los siguientes alfabetos derivados:
$$
\begin{aligned}
&a.\Sigma = \{o, d ,u\}\\
&b.\Sigma^0 =\{\epsilon\}\\
&c.\Sigma^1 =\{o, d ,u\} \\
&d.\Sigma^2 =\{oo, od ,ou, do, dd,du,uo,ud,uu\}\\
&e.\Sigma^3 =\\
\end{aligned}
$$
C. Decida cuales strings pueden ser formadas desde el alfabeto $\Sigma = \{a,b\}$, justifique su respuesta: 
$$
\begin{aligned}
&a.n\\
&b.abba\\
&c.\{a\}\\
&d.\epsilon\\
&e.baaaab\\
\end{aligned}
$$
## Expresiones Regulares:

> Para el alfabeto $\Sigma = \{0, 1\}$, escriba la expresión regular que describa cada uno de los siguientes lenguajes:

A. $L_1 = \{w \in \{0, 1\}^* : w \text{ contiene al menos un '0' y termina exactamente en '11'}\}$.

B. $L_2 = \{w \in \{0, 1\}^* : w \text{ contiene una cantidad impar de ceros}\}$.

C. $L_3 = \{w \in \{0, 1\}^* : w \text{ no contiene la subcadena } 00\}$.

D. $L_4 = \{w \in \{0, 1\}^* : w \text{ tiene longitud menor o igual a 3}\}$.

> Describa con palabras el lenguaje denotado por las siguientes expresiones regulares sobre $\Sigma = \{a, b\}$:

E. $R_1 = (a \mid b)^* abba (a \mid b)^*$

F. $R_2 = b^*(a b^* a b^*)^*$


$$
\begin{aligned}

\end{aligned}
$$