# Alfabetos
### Definición:
Se define como cualquier conjunto finito no vacío, y se denota como $\Sigma$.
> [!WARNING]
> No confundir con sumatorias.

Los elementos de un alfabeto se llaman **Símbolos o Caracteres**.
##### Ejemplo:
Los computadores tienen un alfabeto de $\{0,1\}$, es decir, solo tienen un acceso base a esos caracteres.
##### Ejemplo 1: Alfabeto
$$
\begin{aligned}
\Sigma &= \{a,b\}\\
\Sigma^0 &= \{\epsilon\}\\
\Sigma^1 &= \{a,b\}\\
\Sigma^2 &= \{aa,ab,ba,bb\}\\
\end{aligned}
$$
# Cadena (String)
Un string es una secuencia finita de símbolos pertenecientes a un alfabeto $\Sigma$.
$$
\Large{\Sigma ^* = \Sigma ^0 \cup \Sigma^1 \cup \cdots}
$$

Una cadena $x$ sobre $\Sigma$ se ensamblara agregando caracteres uno luego del otro, es decir:
$$
a_1a_2a_3 \cdots a_{k}
$$
Donde $k =$ a la longitud de la cadena. $|x|$
>[!NOTE]
>Epsilon $\epsilon$ no es lo mismo que un conjunto vacio $\emptyset$, representa una **cadena** vacía.

La concatenación de dos cadenas $x = a_1a_2a_3\cdots a_{n}$ e $y= b_1b_2b_3\cdots b_{m}$ se escribe como:
$$
xy = a_1 \cdots a_n b_1\cdots b_m
$$
Finalmente usaremos $x^k$ para denotar $k$ concatenaciones sucesivas de x, es decir:
$$
x^0 = \epsilon \qquad
x^k = x x^{k-1}
$$
##### Ejemplo 2: Cadena
$$
\begin{aligned}
&x = ab \qquad \qquad \qquad y = cd\\
&x^0 = \epsilon\\
&x^1 = ab\\
&x^2 = abab\\
&xy  = abcd\\
&y^3x^2 =cd|cd|cd|ab|ab \rightarrow cdcdcdabab\\
&|x| = 2
\end{aligned}
$$
### Algunas propiedades:
1. $\Sigma^*$ denota el conjunto de todas las secuencias finitas (cadenas) de símbolos de $\sum$.
2. El conjunto $\Sigma^0$ es especial y contiene solo un elemento llamado $\epsilon$.
3. Si una cadena $x \in \Sigma^k$, entonces diremos que el largo de cada cadena será $|x| = k$, *véase ejemplo 1*.
4. Un ultimo conjunto relevante es $\Sigma^+ = \Sigma^* - \{\epsilon\}$, que la clausura positiva del alfabeto.
5. Existen las **subcadenas**, que son cualquier cadena que exista dentro de una cadena.
		Una cadena $x = adhew$, tiene como subcadenas a $\{ad, hew, dhew, ew, adhe, w, \dots\}$, más no $\{aw\}$, por estar fuera de orden.
6. Por su definición, $\epsilon$ es una subcadena de cualquier cadena.
7. Dadas cadenas $x, y, z$, diremos que $x$ es un *prefijo* de $xy$, e $y$ es un *sufijo* de $xy$.
##### Ejemplo 3:
Para $w = abaab$, calcular los prefijos, los sufijos y las subcadenas.
Prefijos = $\{ a, ab, aba, abaa, abaab, \epsilon\}$
Sufijos = $\{\epsilon, b, ab, aab, baab, abaab\}$
Subcadenas = $\{a, ab, baa, aab, baab, \cdots\}$
# Lenguajes
Un lenguaje sobre un alfabeto $\Sigma$ es cualquier subconjunto de $\Sigma^*$, se puede expresar tanto señalando sus elementos uno a uno o definiendo una regla que todos sus elementos deben cumplir.
Se puede definir el lenguaje como un conjunto de cadenas de un alfabeto determinado.
##### Ejemplo:
$$
\begin{aligned}
&L_1 = \{a,ab,bbb\}\\
&L_2 = \{x\in \{0,1\}^* : \text{x termina en 1}\}
\end{aligned}
$$
> [!IMPORTANT]
> Cualquier operacion sobre conjuntos puede realizarse sobre lenguajes, añadiendo la concatenacion, la potencia, la clausula de Kleene y el complemento.
#### Concatenación:
La concatenación de lenguajes es similar a las relaciones entre conjuntos, donde se debe respetar el orden definido.
$L_1 \cdot L_2 = \{xy \mid x\in L_1 \land x\in L_2\}$
##### Ejemplo 4:
$$
\begin{aligned}
&\text{Se tienen los siguientes lenguajes:}\\
&L_1 = \{ab, bc\} \qquad L_2 = \{xd, ba\}\\
&L_1 \cdot L_2 = \{ab|xd, ab|ba,bc|xd,bc|ba\}
\end{aligned}
$$
> Los | están para separar un poco las concatenaciones y se entienda, no se ponen formalmente.
> $xd|ab$ no forma parte de $L_1 \cdot L_2$.
#### Potencia:
La potencia define que, tomando los elementos que están en el lenguaje, creemos todas las combinaciones de elementos (concatenación de strings) posibles con el largo $k$.
$L^0 = \{\epsilon\}, L^k = L \cdot L^{k-1}$
#### Clausula de Kleene:
Es una potencia "infinita", son todas las combinaciones de elementos posibles de cualquier largo.
$L^* = U_{K \geq 0} L^k$
#### Complemento:
El complemento de un lenguaje se define como todos los elementos que son parte del alfabeto inicial, menos los elementos que están en el lenguaje.
$L^c = \Sigma^* - L$
### Ejemplos:
$$
\begin{aligned}
&\text{Se define un alfabeto como los elementos:}\\
&\Sigma = \{a,b\}\\
&L_1 = \{a,b\}\\
&L_2 = \{aa,bb\}\\
&L_1 \cdot L_2 = \{a|aa, a|bb, b|aa, b|bb\}\\
&L_1^0 = \{\epsilon\}\\
&L_1^2 = \{aa,ab,ba,bb\}\\
&L_1^* = \Sigma^*
\end{aligned}
$$
$$
\begin{aligned}
&\text{Si: } L = \{x \in \Sigma^* \mid \text{x tiene numeros pares de a}\}\\
& L^c = \{x\in \Sigma^*\ \mid \text{x tiene numeros impares de a}\}\\
\end{aligned}
$$
