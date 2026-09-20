<h1 align='center'>Pauta Ayudantía 2 </h1>

### 1.
**Desarrollo por tabla de verdad:**

$$
\begin{aligned}
&\begin{array}{|c|c|c|c|c|c|}
p & q & p\lor q & \lnot p & \lnot q & (\lnot p \land \lnot q) \\
T & T & T & F & F & F\\
T & F & T & F & T & F\\
F & T & T & T & F & F\\
F & F & F & T & T & T\\
\end{array}
\end{aligned}
$$

Las columnas no son iguales, por lo tanto, no son lógicamente equivalentes.

**Desarrollo por leyes:**

$$
\begin{aligned}
\lnot p \land \lnot q &= \lnot(p \lor q) &&[\text{De Morgan}]
\end{aligned}
$$
No se puede reducir más el enunciado, por lo tanto, no son lógicamente equivalentes.
### 2.
**Desarrollo por tabla de verdad:**

$$
\begin{aligned}
&\begin{array}{|c|c|c|c|c|c|c|}
p & q & p\lor q & \lnot p & \lnot q & \lnot(p\lor q) & (\lnot p \land \lnot q)\\
T & T & T & F & F & F & F\\
T & F & T & F & T & F & F\\
F & T & T & T & F & F & F\\
F & F & F & T & T & T & T\\
\end{array}
\end{aligned}
$$

Las columnas de $\lnot(p\lor q)$ y $\lnot p \land \lnot q$ coinciden en **todas** las filas. Son logicamente equivalentes.

**Desarrollo por leyes:**

$$
\begin{aligned}
\lnot (p\lor q) &= \lnot p \land \lnot q &&[\text{De Morgan}]
\end{aligned}
$$

### 3.
**Desarrollo por leyes:**

$$
\begin{aligned}
(\lnot (P\lor Q) \lor Q) &= (\lnot P \land \lnot Q) \lor Q &&[\text{De Morgan}]\\
&= Q \lor (\lnot P \land \lnot Q) &&[\text{Conmutatividad de } \lor]\\
&= (Q \lor \lnot P) \land (Q \lor \lnot Q) &&[\text{Distributividad}]\\
&= (Q \lor \lnot P) \land T &&[\text{Complemento}]\\
&= Q \lor \lnot P &&[\text{Identidad}]\\
&= \lnot P \lor Q &&[\text{Conmutatividad}]
\end{aligned}
$$

### 4.
**Desarrollo por leyes:**

$$
\begin{aligned}
(p\lor q) \implies r &\equiv \lnot(p\lor q) \lor r &&[\text{Definición de implicación}]\\
\lnot[\ (p\lor q) \implies r\ ] &= \lnot[\ \lnot(p\lor q) \lor r\ ]\\
&= \lnot\lnot(p\lor q) \land \lnot r &&[\text{De Morgan}]\\
&= (p\lor q) \land \lnot r &&[\text{Doble negación}]
\end{aligned}
$$

### 5.
**Desarrollo por leyes:**

$$
\begin{aligned}
(\lnot P \land Q) \lor (P \land Q) &= (\lnot P \lor P) \land Q &&[\text{Distributividad}]\\
&= T \land Q &&[\text{Complemento}]\\
&= Q &&[\text{Identidad}]
\end{aligned}
$$

### 6.
**Desarrollo por leyes:**

$$
\begin{aligned}
P \implies (Q \implies P) &= \lnot P \lor (Q \implies P) &&[\text{Definición de implicación}]\\
&= \lnot P \lor (\lnot Q \lor P) &&[\text{Definición de implicación}]\\
&= (\lnot P \lor P) \lor \lnot Q &&[\text{Asociatividad y conmutatividad}]\\
&= T \lor \lnot Q &&[\text{Complemento}]\\
&= T &&[\text{Dominación}]
\end{aligned}
$$

**Desarrollo por tabla de verdad:**

$$
\begin{aligned}
&\begin{array}{|c|c|c|c|}
P & Q & Q \implies P & P \implies (Q \implies P)\\
T & T & T & T\\
T & F & T & T\\
F & T & F & T\\
F & F & T & T\\
\end{array}
\end{aligned}
$$
Como es siempre verdadero, es una Tautologia.