# Autómata Finito No Deterministico:
Un AFND es una maquina similar a un AFD, la principal diferencia es la forma en la que cambian de estado, donde el AFND depende tanto de las reglas y de los estados anteriores, cambiando la función que determina el resultado.
#### Definición formal:
Se define como un quintuple de la siguiente forma:
$$
\begin{aligned}
A = (Q, \Sigma, \delta, q_0, F) 
\end{aligned}
$$
$Q$ = Conjunto de los estados posibles de la maquina.
$\Sigma$ = Alfabeto de entrada, todas las entradas posibles y aceptables.
$\delta$ = Función de transición, que se define como: $\delta : \Sigma \times Q \rightarrow Q$
$q_0$ = Estado inicial.
$F$ = Conjunto de estados finales, donde $F\subseteq Q$, son los únicos estados donde el *input* se considera valido.

>[!WARNING]
>Siempre se puede pasar de un AFND a un AFD, pero no siempre a la inversa.
## Conversion de AFND a AFD
Se tiene el siguiente AFND que trabaja sobre este 