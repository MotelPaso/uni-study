<h1 align='center'>Pauta - Ayudantía 1</h1>

## Técnicas de Demostración

### Inducción

**A.** Para todo $n \geq 0 \land n \in \mathbb{N}$: $n^4 - 4n^2 \bmod 3 = 0$.

Caso base ($n=0$): $0^4 - 4\cdot0^2 = 0$, que es múltiplo de 3. Se cumple.

Hipótesis: asumimos que $n^4-4n^2 = 3k$ es verdadero para algun $k \in \mathbb{Z}$.

Paso inductivo: debemos mostrar que $(n+1)^4 - 4(n+1)^2$ es múltiplo de 3.
$$(n+1)^4 - 4(n+1)^2 = (n^4-4n^2) + \left(4n^3+6n^2-4n-3\right)$$
Por nuestra hipotesis, el primer término es múltiplo de 3. Asumiendo un numero $x \in \mathbb{Z}$:
$$ 3x + 4n^3+6n^2-4n-3$$
Factorizando por $3$ y por $4n$:
$$
3(x + 2n^2 - 1) + 4(n^3-n)
$$

Y $n^3-n = (n-1)\,n\,(n+1)$ es el producto de tres enteros consecutivos, por lo que siempre es divisible por 3 (uno de los tres factores es múltiplo de 3). Como el primer término también es múltiplo de 3, $(n+1)^4-4(n+1)^2$ es múltiplo de 3. $\square$

---

**B.** $1\cdot2\cdot3 + 2\cdot3\cdot4 + \cdots + n(n+1)(n+2) = \dfrac{n(n+1)(n+2)(n+3)}{4}$

Caso base ($n=1$): Izq $= 1\cdot2\cdot3 = 6$. Der $= \dfrac{1\cdot2\cdot3\cdot4}{4} = 6$. Se cumple.

Hipotesis: asumimos verdadero $\displaystyle\sum_{i=1}^{k} i(i+1)(i+2) = \frac{k(k+1)(k+2)(k+3)}{4}$.

Paso inductivo ($n=k+1$):

$$\sum_{i=1}^{k+1} i(i+1)(i+2) = \frac{k(k+1)(k+2)(k+3)}{4} + (k+1)(k+2)(k+3)$$

Factorizando $(k+1)(k+2)(k+3)$:

$$= (k+1)(k+2)(k+3)\left(\frac{k}{4}+1\right) = \frac{(k+1)(k+2)(k+3)(k+4)}{4}$$

que corresponde exactamente a la fórmula con $n=k+1$. $\square$

---

**C.** "$n^2+n+41$ es primo para todo $n \geq 0$". **Es falso, se refuta con un contraejemplo.**

Basta un caso donde falle. Con $n=40$:

$$40^2+40+41 = 1600+40+41 = 1681 = 41^2$$

$1681$ no es primo (es $41\times41$), por lo tanto la afirmación es falsa.

### Diagonalización de Cantor

**A.** El conjunto de reales en $(0,1)$ es no numerable.

Demostración por contradicción: supongamos que $(0,1)$ es numerable. Entonces existe una enumeración $x_1, x_2, x_3, \dots$ que cubre todos los reales del intervalo, cada uno escrito en su expansión decimal:

$$x_1 = 0.d_{11}d_{12}d_{13}\dots \quad x_2 = 0.d_{21}d_{22}d_{23}\dots \quad x_3 = 0.d_{31}d_{32}d_{33}\dots \quad \dots$$

Construimos un nuevo número $y = 0.e_1e_2e_3\dots$ definiendo cada dígito $e_i$ de forma que difiera del dígito diagonal $d_{ii}$ (por ejemplo, $e_i = 5$ si $d_{ii}\neq 5$, y $e_i=4$ si $d_{ii}=5$, evitando además los casos $0$ y $9$ para no toparse con representaciones decimales ambiguas).

Por construcción, $y \in (0,1)$ pero $y \neq x_i$ para todo $i$, ya que difiere de $x_i$ en el dígito $i$-ésimo. Esto contradice que la enumeración cubría **todos** los reales de $(0,1)$. Por lo tanto, $(0,1)$ no es numerable. $\blacksquare$

**B.** El conjunto de secuencias infinitas sobre $\Sigma=\{a,b,c\}$ es no numerable.

Mismo argumento: si existiera una enumeración $s_1, s_2, s_3,\dots$ de todas las secuencias infinitas, construimos $t$ tomando en la posición $i$ un símbolo distinto al que aparece en la posición $i$ de $s_i$ (hay 3 símbolos disponibles, así que siempre se puede elegir uno distinto). La secuencia $t$ así construida es infinita sobre $\Sigma$, pero difiere de cada $s_i$ en al menos una posición, por lo que $t$ no está en la enumeración. Contradicción. Por lo tanto el conjunto es no numerable. $\blacksquare$

## Lenguajes

**A.** $L_2 = \{x\in\{0,1\}^* : x \text{ termina en 1} \land |x|\leq 4\}$

$$L_2 = \{1,\ 01,\ 11,\ 001,\ 011,\ 101,\ 111,\ 0001,\ 0011,\ 0101,\ 0111,\ 1001,\ 1011,\ 1101,\ 1111\}$$

**B.** $\Sigma=\{o,d,u\}$

- $\Sigma^0 = \{\varepsilon\}$
- $\Sigma^1 = \{o,\ d,\ u\}$
- $\Sigma^2 = \{oo,\ od,\ ou,\ do,\ dd,\ du,\ uo,\ ud,\ uu\}$
- $\Sigma^3$ =

$$\begin{aligned}
&\{ooo,\ ood,\ oou,\ odo,\ odd,\ odu,\ ouo,\ oud,\ ouu,\\
&doo,\ dod,\ dou,\ ddo,\ ddd,\ ddu,\ duo,\ dud,\ duu,\\
&uoo,\ uod,\ uou,\ udo,\ udd,\ udu,\ uuo,\ uud,\ uuu\}
\end{aligned}$$

**C.** Decida cuales strings pueden ser formadas desde el alfabeto $\Sigma = \{a,b\}$, justifique su respuesta: 

| Elemento | ¿Es un string válido sobre $\Sigma$? | Justificación |
|---|---|---|
| a. $n$ | **No** | $n \notin \Sigma$, no es un símbolo del alfabeto. |
| b. $abba$ | **Sí** | Secuencia finita formada solo por símbolos de $\Sigma$. |
| c. $\{a\}$ | **No** | Es notación de *conjunto*, no un string; un string es una secuencia de símbolos, no una colección. |
| d. $\varepsilon$ | **Sí** | El string vacío siempre pertenece a $\Sigma^*$ para cualquier alfabeto. |
| e. $baaaab$ | **Sí** | Secuencia finita formada solo por símbolos de $\Sigma$. |

## Expresiones Regulares

**A.** $L_1$: contiene al menos un '0' y termina exactamente en '11'.
$$R_1 = (0\mid1)^*\cdot\,0\,\cdot(0\mid1)^*\,\cdot11$$
**B.** $L_2$: cantidad impar de ceros.

$$R_2 = 1^*\,(0\,1^*\,0\,1^*)^*\,0\,1^*$$

Cada bloque $01^*01^*$ agrega ceros de a pares (no cambia la paridad), y el $0\,1^*$ final asegura que la cantidad total de ceros sea impar.

**C.** $L_3$: no contiene la subcadena '00'.

$$R_3 = (1\mid01)^*(\varepsilon\mid0)$$

Cada '0' debe ir seguido de un '1' (bloque $01$), excepto posiblemente el último carácter del string, que puede ser un '0' suelto.

**D.** $L_4$: strings de largo menor o igual a 3.

$$R_4 = (0\mid1\mid\varepsilon)(0\mid1\mid\varepsilon)(0\mid1\mid\varepsilon)$$

Genera todas las combinaciones de largo 0, 1, 2 y 3 sobre $\{0,1\}$.

**E.** $R_1 = (a\mid b)^*\,abba\,(a\mid b)^*$

Describe el lenguaje de todos los strings sobre $\{a,b\}$ que **contienen la subcadena "abba"** en algún lugar (con cualquier cosa antes y después).

**F.** $R_2 = b^*(ab^*ab^*)^*$

Describe el lenguaje de todos los strings sobre $\{a,b\}$ que tienen una **cantidad par de símbolos 'a'** (incluyendo cero apariciones de 'a'). Cada bloque $ab^*ab^*$ agrega exactamente dos 'a', y las 'b' pueden aparecer libremente en cualquier posición.
