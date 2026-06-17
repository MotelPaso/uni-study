# Automatas Pushdown (PDA)
A diferencia de los automatas finitos, poseen una memoria limitada, ademas de poder representar gramatica de mayor nivel. Puede recibir vacio ($\epsilon$)
Es equivalente a un automata finito + una pila.
>[!IMPORTANT]
>Una pila es una estructura de datos que ordena los datos de forma que el primero que entra, primero que sale. Solo se puede acceder al primer elemento de la pila. Funciona como un tarro de papas fritas (?)

Para crear un automata pushdown, necesitamos un input, una unidad de control y un stack "infinito", retornando si la cadena es valida o invalida con respecto al lenguaje.
### Definicion Formal
Se toma una tupla de 7 elementos:
$$
P = (Q, \Sigma, \Gamma, \delta, q_0, z_0, F)
$$
Los elementos nuevos son el stack $(\Gamma)$ y $z_0$, donde $z_0$ va a ser el primer elemento del stack.
La funcion de transicion funciona:
$$
\delta(q, a, X)
$$
Donde q es el estado actual, $a\in \Sigma \cup \epsilon$, y $X \in \Gamma$
Esta función retorna un conjunto de pares (p,y), donde p es el nuevo estado y $y$ es el string que reemplaza a X en la cima del stack.
#### Reglas:
Si es que $y == \epsilon$, se hace un pop
Si es que y == x, no se hace nada
si es que y == YZ, Z reemplaza a X e Y es un push, y se retorna Y

Se tiene que agregar un valor auxiliar (z_0) al inicial el ejercicio, esto es para comprobar si la pila esta vacia o no.
