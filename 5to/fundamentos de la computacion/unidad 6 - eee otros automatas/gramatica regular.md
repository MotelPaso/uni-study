# Gramatica
La gramática regular rige los autómatas de estados finitos y acepta un lenguaje regular.
Un lenguaje regular es el lenguaje normal que hemos estado viendo a lo largo del curso.
#### Definición:
La gramática puede ser definida formalmente usando cuatro tuplas de la forma
$$
G = (V, T, S , P)
$$
V = conjunto de variables o símbolos no terminales
T = conjunto de símbolos terminales
S = símbolo inicial
P = reglas de terminales y no terminales.
#### Ejemplo:
$$
G = (\{S,A,B\}, \{a,b\}, S, \{S\rightarrow AB, A \rightarrow a, B \rightarrow b\})
$$
Esto sirve para formar strings que sean automáticamente aceptados por un lenguaje, como por ejemplo:
$$
\begin{aligned}
x &= S\\
&= AB\\
&= ab \rightarrow x = ab
\end{aligned}
$$
Se va "transformando" desde el símbolo inicial a los símbolos no terminales, si se llega a un símbolo terminal, se termina el string.
### AFD a Gramática Regular:
Para transformar un AFD a una gramatica regular, se utiliza un simbolo por estado:
##### Ejemplo:
Se tiene la siguiente tabla de estados de un AFD:

| $\delta$ | 0   | 1   |
| -------- | --- | --- |
| q0       | q1  | q2  |
| q1       | q1  | q2  |
| q2       | q2  | q0  |
Definiremos una gramática tal que:
$$
\begin{aligned}
G = &\,(V, T, S , P)\\
V = &\,\{S,A,B,C\}\\
T = &\,\{0, 1\}\\
S = &\,S\\
P = &\,\{S\rightarrow 0A \mid 1B,\\
&\,\{A \rightarrow 0A \mid 1B\mid \epsilon, \\
&\, \{B \rightarrow 0B \mid 1S\}
\end{aligned}
$$
Donde se le asigna una letra a cada estado y en las reglas, se inserta antes el input de transición a ese estado. 
A los estados finales, se les agrega una regla de $\epsilon$ para terminar la string.
> Mientras que las letras asignadas no tienen que tener un orden fijo, es bueno iniciar con una S para mantener el orden de la definicion.

>[!INFO]
>Para un AFND es el mismo proceso, solo que con más reglas.