# Alfabetos
### Definición:
#### 1.
Se define como cualquier conjunto finito no vacío, y se denota como $\Sigma$.
> [!WARNING]
> No confundir con sumatorias.

Los elementos de un alfabeto se llaman **Símbolos o Caracteres**.
##### Ejemplo:
Los computadores tienen un alfabeto de $\{0,1\}$, 
#### 2. Cadena (String)
Un string es una secuencia finita de símbolos pertenecientes a un alfabeto $\Sigma$.
$$
\Large{\Sigma ^* = \Sigma ^0 \cup \Sigma^1 \cup \cdots}
$$
##### Ejemplo 1: Alfabeto
$$
\begin{aligned}
\Sigma &= \{a,b\}\\
\Sigma^0 &= \{\epsilon\}\\
\Sigma^1 &= \{a,b\}\\
\Sigma^2 &= \{aa,ab,ba,bb\}\\
\end{aligned}
$$
##### Ejemplo 2: Cadena
$$
\begin{aligned}
x &= ab\\
x^0 &= \epsilon\\
x^1 &= ab\\
x^2 &= abab\\
|x| &= 2
\end{aligned}
$$
>[!NOTE]
>Epsilon $\epsilon$ no es lo mismo que un conjunto vacio $\emptyset$, representa una **cadena** vacia.
### Definición Formal de String:
$\Sigma^*$ denota el conjunto de todas las secuencias finitas de simbolos de $\sum$.
El conjunto $\Sigma^0$ es especial y contiene solo un elemento llamado $\epsilon$.
Si una cadena $x \in \Sigma^k$, entonces decimos que su largo sera $|x| = k$, *véase ejemplo  es1*.
Un ultimo conjunto relevante es $\Sigma^+ = \Sigma^* - \{\epsilon\}$

Dadas cadenas $x, y, z$, diremos que x es un prefijo de $xy$, y es un sufijo de $yx$.
Tambien es una subcadena de ambos.

##### Ejemplo 3:
Para $w = abaab$, calcular los prefijos, los sufijos y las subcadenas.
Prefijos = $\{ a, ab, aba, abba, abaab, \epsilon\}$
Sufijos = $\{\epsilon, b, ab, aab, baab, a\}$
Subcadenas = $\{a, ab, baa, aab, baab, \cdots\}$
> Las subcadenas son cualquier combinacion (ordenada) de caracteres que exista en la cadena. Es como sacarle una parte.
# Lenguajes
Un lenguaje sobre un alfabeto \Sigma es cualquier subconjunto de \Sigma^*
##### Ejemplo:
$$
L_1 = \{a,ab,bbb\}\\
L_2 = \{x\in \{0,1\}^* : \text{x termina en 1}\}
$$
Se puede definir el lenguaje como un conjunto de cadenas.

> [!IMPORTANT]
> Cualquier operacion sobre conjuntos puede realizarse sobre lenguajes, añadiendo la concatenacion, la potencia, la clausula de Kleene y el complemento.
#### Concatenacion:
$L1 \cdot L2 = \{xy \mid x\in L1 \land x\in L2\}$
#### Potencia:
$L^0 = \{\epsilon\}, L^k = L \cdot L^{k-1}$
#### Clausula de Kleene:
$L^* = U_{K \geq 0} L^k$
#### Complemento:
$L^c = \Sigma^* - L$
### Ejemplos:
$$
\begin{aligned}
&\text{Se define un alfabeto como los elementos:}\\
&\Sigma = \{a,b\}\\
&L_1 = \{a,b\}\\
&L_2 = \{aa,bb\}\\
&L_1 \cdot L_2 = \{aaa, abb, baa, bbb\}\\
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
