# Autómata Finito Deterministico:
Un AFD es una maquina abstracta con estados finitos, que lee entradas y cambia de estado siguiendo reglas deterministicas. 
Se pueden utilizar para revisar si una cadena determinada de un alfabeto es parte o no de un lenguaje. Cabe resaltar que los automatas del curso no tienen output.
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
## Tabla de transición
Es una tabla donde se define cada salida de la función de transición, es decir, cada cambio de estado y dependiendo de cada input.

| Estados | .25   | .50   |
| ------- | ----- | ----- |
| q_0     | $q_1$ | $q_2$ |
| q_1     | $q_2$ | $q_3$ |
| q_2     | $q_3$ | $q_4$ |
| q_3     | $q_4$ | $q_4$ |
| q_4     | $q_1$ | $q_2$ |
### Ejercicios:
1. Diseñe un AFD que acepta cadenas del alfabeto $\Sigma = \{ 0,1 \}$ que terminen en "01".
$$
\begin{aligned}
&A = (Q, \Sigma, \delta, q_0, F)\\
&Q = \{q_0, q_1, q_2 \}\\
&\Sigma = \{0,1\}\\
&q_0 = q_0\\
&F = \{q_2\}
\end{aligned}
$$
2. Diseñe un AFD que acepta cadenas del alfabeto $\Sigma = \{ 0,1 \}$ que terminen en "011". 
$$
\begin{aligned}
&A = (Q, \Sigma, \delta, q_0, F)\\
&Q = \{q_0, q_1, q_2, q_3 \}\\
&\Sigma = \{0,1\}\\
&q_0 = q_0\\
&F = \{q_3\}
\end{aligned}
$$
3. Diseñe un AFD que acepte cadenas del alfabeto $\Sigma = \{ 0,1 \}$ donde la cantidad de 1 sea divisible por 3.
4. 