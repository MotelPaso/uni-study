Podemos usar equivalencias para reducir formulas complejas a versiones reducidas.
Para esto, debemos usar **Tautologias** y **Contradicciones**.
- Tautologia: Siempre verdadero. Se denota con una T.
- Contradiccion: Siempre falso. Se denota con una F.
## Propiedades:
Se mantiene la asociatividad, conmutabilidad, distributividad y Leyes de Morgan en la semántica lógica, pero se añaden algunas nuevas:
###### Contraposición:
$$
(P\implies Q)\iff (\lnot Q \implies \lnot P)
$$
###### Eliminación de la implicación o Condicional:
$$
(P\implies Q) \iff (\lnot P \lor Q) 
$$
##### Ley de la identidad:
$$
\begin{aligned}
P \land T \iff P\\
P \lor F \iff P
\end{aligned}
$$
##### Dominación:
$$
\begin{aligned}
P \lor T \iff T\\
P \land F \iff F
\end{aligned}
$$
##### Ley inversa:
$$
\begin{aligned}
P \land \lnot P \iff F\\
P \lor \lnot P \iff V
\end{aligned}
$$

#### Ejemplo:
$$
\begin{aligned}
&(P \lor F) \land (Q\lor T)& \text{Identidad}\\
&P \land (Q\lor T)& \text{Dominacion}\\
&P \land T& \text{Identidad}\\
&P \iff (P \lor F) \land (Q\lor T)&
\end{aligned}
$$
##### Doble negacion:
$$
\lnot(\lnot p) \iff p
$$
##### De Morgan:
$$
\begin{aligned}
\lnot (p \land q) \iff \lnot p \lor \lnot q\\
\lnot (p \lor q) \iff \lnot p \land \lnot q
\end{aligned}
$$
#### Ejemplo 2:
$$
\begin{aligned}
&\lnot (\lnot p \land \lnot q) & \text{Morgan laws}\\
&\lnot (\lnot(p\lor q)) & \text{Doble neg}\\
& p \lor q\\
\end{aligned}
$$

##### Ley de absorcion:
$$
\begin{aligned}
P \land (P \lor Q) \iff P\\
P \lor (P \land Q) \iff P
\end{aligned}
$$

#### Ejemplo 3:
$$
\begin{aligned}
&\lnot\lnot P \lor ((P\lor F) \land \lnot\lnot Q) & \text{Doble negacion}\\
&P \lor ((P \lor F) \land Q) & \text{Identidad}\\
&P \lor (P \land Q) &\text{Absorcion}\\
&P
\\
\end{aligned}
$$