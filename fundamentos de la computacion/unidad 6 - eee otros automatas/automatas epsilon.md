# Autómata Epsilon
Son iguales a los AFND, pero estos pueden aceptar strings vacíos como parte del alfabeto.
#### Definición formal:
Se define como un quintuple de la siguiente forma:
$$
\begin{aligned}
A = (Q, \Sigma, \delta, q_0, F) 
\end{aligned}
$$
$Q$ = Conjunto de los estados posibles de la maquina.
$\Sigma$ = Alfabeto de entrada, todas las entradas posibles y aceptables.
$\delta$ = Función de transición, que se define como: $\delta : \Sigma \cup \epsilon \times Q \rightarrow Q$
$q_0$ = Estado inicial.
$F$ = Conjunto de estados finales, donde $F\subseteq Q$, son los únicos estados donde el *input* se considera valido.
Es importante señalar que cada estado en string vacío va a si mismo.

## Conversion de AFND-epsilon a AFND.
1. Revisamos todos los estados para hallar la e-clausula de cada uno.
> Son todos los estados alcanzables usando solo movimientos epsilon.
2. Luego, revisar todas sus transiciones para "eliminar" las transiciones epsilon.
3. Determinar estados finales del nuevo automata.

>[!INFO]
>Recordar que los estados finales van a ser todos los estados que incluyan el estado final del automata inicial.
##### Ejemplo: Convierta el siguiente AFND-e a AFND.

|          | $\epsilon$ | 0   | 1   |
| -------- | ---------- | --- | --- |
| q0       | {q1, q2}   | X   | X   |
| q1       | X          | q1  | q3  |
| q2       | X          | q4  | q2  |
| q3 final | X          | X   | X   |
| q4 final | X          | X   | X   |
Primero, encontramos la e-clausura de cada estado:
$$
\begin{aligned}
\epsilon \text{-clausura }(q_0) &= \{q_1, q_2, q_0\}\\
\epsilon \text{-clausura }(q_1) &= \{q_1\}\\
\epsilon \text{-clausura }(q_2) &= \{q_2\}\\
\epsilon \text{-clausura }(q_3) &= \{q_3\}\\
\epsilon \text{-clausura }(q_4) &= \{q_4\}
\end{aligned}
$$
> Esto es recursivo, por ejemplo, si en $q_1$ hubieran transiciones epsilon, también podríamos llegar a ellas desde $q_0$.

Ahora, comparamos cada clausura con cada input:

|          | 0         | 1        |
| -------- | --------- | -------- |
| q0       | {q1 , q4} | {q3, q2} |
| q1       | q1        | q3       |
| q2       | q4        | q2       |
| q3 final | X         | X        |
| q4 final | X         | X        |
En q0, podemos ir a q1, q2 y q0, así que si revisamos sus transiciones en 0, nos da que podemos ir a $q_1 \rightarrow q_1 \mid q_2 \rightarrow q_4$.