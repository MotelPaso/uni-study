1. Crear el automata basado en el problema, puede ser de Mealy o Moore
2. Pasar los datos del automata a una tabla de este estilo:

	| Moore |  | |
	|--------|------|---|
	| Estado | Estados Futuros | Salidas |
	| Mealy |
	| Estado | Estados Futuros |

3. Revisar si existen estados equivalentes.
4. Si no existen estados equivalentes, realizar la siguiente tabla con los datos del paso 2:

	| Estados | $\Large{q_1\  q_0}$ | 0 | 1 | Salidas |
	|---|---|---|---|---|

5. Convertir las columnas $q_1\ q_0 \land \text{Salidas}$ en una tabla de verdad y calcular su función booleana de salida.
6. Elegir un biestable a usar, se puede usar cualquiera, pero se recomienda Flip-Flop JK.
7. Armar nuevas tablas utilizando los datos de la tabla 4, tanto para JK1 como para JK2.
	Para armar estas tablas, se tiene que revisar 
8. Juntar todos los datos en una sola tabla.
9. Crear una tabla de verdad con los datos y reducir a función booleana utilizando mapas de karnaugh.
10. Finalmente, crear el circuito.
