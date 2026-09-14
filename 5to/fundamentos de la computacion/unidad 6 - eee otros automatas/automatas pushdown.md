# Autómatas Pushdown (PDA)
A diferencia de los autómatas finitos, poseen una memoria limitada, además de poder representar gramática de mayor nivel. Puede recibir vacío ($\epsilon$)
Es equivalente a un automata finito + una pila.
>[!IMPORTANT]
>Una pila es una estructura de datos que ordena los datos de forma que el primero que entra, primero que sale. Solo se puede acceder al primer elemento de la pila. Funciona como un tarro de papas fritas.

Para crear un automata pushdown, necesitamos un input, una unidad de control y un stack "infinito", retornando si la cadena es valida o invalida con respecto al lenguaje.
## Definición Formal
Se define una tupla de 7 elementos:
$$
P = (Q, \Sigma, \Gamma, \delta, q_0, z_0, F)
$$
Los elementos son iguales a los de un automata epsilon, los nuevos son la pila que usaremos $(\Gamma)$ y $\text{Z}_0$ que va a ser el elemento inicial del stack.

La función de transición funciona:
$$
\delta(q, a, X)
$$
Donde $q$ es el estado actual, $a\in \Sigma \cup \epsilon$, y $X \in \Gamma$

Esta función retorna un conjunto de pares (p,y), donde p es el nuevo estado y $y$ es el string que reemplaza a X en la cima del stack.
Se dibuja de esta forma en el diagrama de estados:
$$
\begin{aligned}
\text{I, top} \rightarrow \text{accion}
\end{aligned}
$$
Donde $\text{I}$ es el carácter recibido del input, $\text{top}$ es el elemento superior de la pila, y $\text{accion}$ es la acción que se tomará con respecto a la pila.
### Reglas:
1. $i,\text{top} \rightarrow \epsilon$ 
	  Se saca (*elimina*) el elemento superior de la pila.
2. $i, \text{top} \rightarrow X\ top$
	  Se inserta X a la pila.
#### Aplicación:
Para crear un automata pushdown, se tiene que agregar un valor auxiliar $\text{Z}_0$ al inicial el ejercicio, esto es para comprobar si la pila esta vacía o no. Se puede escribir un estado especifico para esto o omitirse y especificar que se omitio.
