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
Es importante señalar que cada estado en string vacío va a si mismo, exceptuando los casos donde exista una flecha a otro estado.

## Conversion de automata epsilon a AFND.
1. Revisamos estado por estado, aplicando a que estado podemos llegar utilizando solo epsilon.
2. Luego, desde los estados resultantes, revisamos los elementos del alfabeto para ver a que estado llegamos desde ellos.
3. Finalmente, aplicamos solo epsilon a los resultantes para ver los estados futuros.
-------0------- 1
A    {A,B,C} {B,C}
B   {C} ------{B,C}
C   {C} ------{C}
>[!INFO]
>Recordar que los estados finales van a ser todos los estados que incluyan el estado final inicial.

#### Ejemplo:
Transformar el siguiente autómata epsilon a NFA:

|     | $\epsilon*$ | 0              | 1           | $\epsilon*$ |
| --- | ----------- | -------------- | ----------- | ----------- |
| A   | A           | B              |             | B,C         |
| B   | B,C         | $\emptyset$, C |             | B,C         |
| C   | C           | C              |             | C           |
| D   | D           | $\emptyset$    |             | D           |
| A   | A           |                | $\emptyset$ | A           |
| B   | B,C         |                | B,D         | B,C,D       |
| C   | C           |                | D           | D           |
| D   | D           |                | $\emptyset$ | D           |
La ultima fila son las conexiones entre los estados, donde los estados finales del nuevo autómata serán todos los estados que tengan un camino hacia el antiguo estado final.
> Si se llega a un estado vacío, se mantiene el estado anterior al vacío.