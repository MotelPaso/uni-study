#### Demostrar que: $A \subseteq B \Longleftrightarrow A \cap B = A$
##### Resolución:
Como es una implicancia doble, tenemos que probar que ambas partes implican a la otra.
$$A\subseteq B \implies A\cap B = A $$
Si $A \subseteq B$, entonces $A\cap B = A$
Como es una igualdad, tenemos que probar que ambas partes funcionan:
1. $A \cap B \subseteq A$
$$
\begin{aligned}
& x \in A\cap B \quad ||\quad   \text{def. interseccion}\\
&x \in A \land x \in B \implies x \in A
\end{aligned}
$$
2. $A \subseteq A \cap B$
$$
\begin{aligned}
&x \in A\\
&\text{Como } A \subseteq B \text{, entonces } x\in B
\end{aligned}
$$
Si $A \cap B = A$, entonces $A\subseteq B$
$$
\begin{aligned}
x \in A\\
\text{Como: } A \cap B = A \implies x \in B
\end{aligned}
$$
### Demostrar que: $A\cup (B\cap C) = (A\cup B) \cap (A\cup C)$
##### 1.  $A\cup (B\cap C) \subseteq (A\cup B) \cap (A\cup C)$
1.1: $x \in A$
$$
\begin{aligned}
&x \in A \implies x\in (A \cup B) \land x\in (A\cup C)\\
&\text{Por def de interseccion:}\\
&x\in (A \cup B) \lor x\in (A\cup C) \rightarrow x \in (A\cup B) \cap (A\cup C)
\end{aligned}
$$
1.2: $x \in B\cup C$
$$
\begin{aligned}
&x\in B \cup C \implies x \in B \land x \in C\\
&\text{Podemos asumir que: } x \in A \cup B \land x\in A \cup C\\
&\text{Por def de interseccion: } x \in (A \cup B) \cap (A \cup C)
\end{aligned}
$$
##### 2. $(A\cup B) \cap (A\cup C)\subseteq A\cup (B\cap C)$
2.1: $x \in A\cup B$
$$
x \in A\cup B \implies x\in A \lor x \in B 
$$
2.2: $x\in A\cup C$
$$
x\in A\cup C \implies x\in A \lor x\in C\\ 
$$
$$
\begin{aligned}
\text{Caso 1: } x \in A &\rightarrow x\in A \cup (B \cap C)\\
\text{Caso 2: } x \notin A &\rightarrow x\in B \lor x\in C\\
x\in B \cap C &\implies x\in A \cup (B \cap C)
\end{aligned}
$$
En el caso 1, si esta en A, se demuestra directamente,
si NO esta en A, tiene que estar en B y en C
#### Demostrar que: $(A \cup B) - C = (A - C) \cup (B-C)$
##### 1. $(A \cup B) - C \subseteq (A - C) \cup (B-C)$
1. $x \in A\cup B \implies x\in A \lor x\in B$
2. $x \notin C$
	1. $x \in A \land x \notin C = A - C$
	2. $x \in B \land x \notin C = B - C$
Como es un $\lor$, se tiene que $x \in (A-C) \cup (B-C)$
##### 2. $(A - C) \cup (B-C)\subseteq (A \cup B) - C$
1. $x\in A-C \implies x\in A \land x\notin C$
2. $x\in B-C \implies x\in B \land x \notin C$
3. Se puede extraer que $(x \in A \lor x \in B)$ pero $x \notin C$
Finalmente, por def de diferencia, se puede escribir como:
$x\in (A\cup B) -C$