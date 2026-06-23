# Expresiones Regulares
Se definen como:
$$
\begin{aligned}
\emptyset \rightarrow L= \{\}\\
\lambda \rightarrow L= \{\lambda\}\\
\alpha \rightarrow L= \{\alpha\}\\
\end{aligned}
$$
Lambda es una cadena vacía!
## Operadores
$\mid$ or
+, union
Si definimos un $a$ y $b$ como expresiones regulares, entonces, $a + b$ también es denotado como por la union de $L(a) \cup L(b)$.
$\cdot$, concatenación
Si definimos un $a$ y $b$ como expresiones regulares, entonces un $L(ab)$ es igual a $L(a)L(b)$.
$*$, clausula de kleene, potencia
$L(A*)$ es igual a $(L(A))*$
$()$, parentesis de toda la vida
$L((A)) = L(A)$
Su prioridad es igual a su orden de escritura, es decir, (), * , $\cdot$, +, |
### Propiedades$
Sea una expresión regular cualquiera:
1. $\alpha \lambda = \alpha$
2. $\emptyset * = \lambda$
3. $\alpha * = \lambda + \alpha\cdot \alpha*$
#### Union:
$A(\alpha) = (Q, \Sigma, \delta, q_0, F),  A(\beta) = (Q, \Sigma, \delta, q_0, F)$ 
1. La nueva Q, sera la union de los estados, pero quitando los estados iniciales de cada automata.
2. la funcion delta seran todos los estados
3. los estados finales va a ser la union de ambos solo si los estados iniciales son parte de los estados finales de cada uno.
4. Si no, sera la union de los estados finales menos los estados finales, agregando el estado inicial de la union creada. 
## Ejemplo:
1. $A(A\mid B)$
	Podemos ver que existe una concatenacion y un operador or.
	Entonces, primero solo acepta A.
	Luego, acepta tanto A como B.
	En forma de diagrama de estados:
	$q_0$ -A> $q_1$ $\cdot$ $(q_0$ --A,B> $q_1)$
2. $A\cdot A\cdot B*$
	Son dos concatenaciones y una clausula de kleene.
	Primero, acepta dos A.
	Luego, cualquier cantidad de B.
	$q_0$ - A > $q_1 \cdot q_0$ - A > $q_2 \cdot q_3$ - B > $q_3$... 
3. A + B
	Tenemos dos automatas iniciales:
	q_0 -A> q_1
	q_0 -B> q_1
	Ahora, los unimos creando un nuevo automata.
	q_0 -A> q_1
	||----B> q_2
	Los estados finales son todos los estados agregando el estado inicial q_0
4. $q_0$-A> $q_1$-B> $q_2!$
	B           A