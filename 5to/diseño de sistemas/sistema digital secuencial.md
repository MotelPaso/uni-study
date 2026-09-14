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
### Ejemplo:
#### Con dos:
Es un circuito con Moore, ingresamos cada cambio de estado en una tabla junto a su salida emitida.

|  Q  |  0  |  1  |  Z  |
| :-: | :-: | :-: | :-: |
| Q0  | Q1  | Q0  |  0  |
| Q1  | Q2  | Q0  |  0  |
| Q2  | Q3  | Q0  |  0  |
| Q3  | Q3  | Q3  |  1  |
Para revisar si existen estados redundantes, se utiliza la tabla de equivalencias:
Para esto, se tienen que cumplir dos cosas:
1. Salidas iguales.
2. Estados siguientes también sean iguales.
Primero, revisaremos si las salidas son iguales.

| Q1  |   1. Q1 = Q2   |       ==       |       ==       |
| :-: | :------------: | :------------: | :------------: |
| Q2  |   2. Q3 = Q1   |   4. Q2 = Q3   |       ==       |
| Q3  | 3. dif salidas | 5. dif salidas | 6. dif salidas |
| ==  |       Q0       |       Q1       |       Q2       |
Ahora, se va de reversa, revisando si las reglas impuestas se cumplen.
Las salidas diferentes inmediatamente se ignoran.

| Q1  | 1. por 3: X |     ==      |  ==  |
| :-: | :---------: | :---------: | :--: |
| Q2  | 2. por 2: X | 3. por 1: X |  ==  |
| Q3  |    4. X     |    2. X     | 1. X |
| ==  |     Q0      |     Q1      |  Q2  |
No hay estados equivalentes.
____

Ahora que tenemos la tabla minima de estados, le asignaremos a cada estado un valor binario. Es recomendable usar codigo gray para despues pasar rapido a mapa de Karnaugh.

|  Q  | q1q0 |    0     |    1     |  Z  |
| :-: | :--: | :------: | :------: | :-: |
| Q0  |  00  | Q1 \| 01 | Q0 \| 00 |  0  |
| Q1  |  01  | Q2 \| 11 | Q0 \| 00 |  0  |
| Q2  |  11  | Q3 \| 10 | Q0 \| 00 |  0  |
| Q3  |  10  | Q3 \| 10 | Q3 \| 10 |  1  |
La función de salida de Z se calcula utilizando *solo* los valores binarios asignados a los estados (q1q0).

| q1  | q0  | Z   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 1   | 0   |
| 1   | 0   | 1   |
Por lo tanto: Z = q1.
____
La cantidad de biestables a usar se define por la siguiente formula:
$$
2^k \geq n
$$
Donde n va a ser la cantidad de estados y k la cantidad de biestables.
____
Ahora, aplicaremos la tabla de excitacion de JK.
Se tiene que reescribir la tabla de estados de esta forma:

|  Q  | q1q0 |    0     |    1     |  Z  |
| :-: | :--: | :------: | :------: | :-: |
| Q0  |  00  | Q1 \| 01 | Q0 \| 00 |  0  |
| Q1  |  01  | Q2 \| 11 | Q0 \| 00 |  0  |
| Q2  |  11  | Q3 \| 10 | Q0 \| 00 |  0  |
| Q3  |  10  | Q3 \| 10 | Q3 \| 10 |  1  |
Pasa a:

|  Q  | q1  |  0   |  1   | JK1 (0) | JK1 (1) | \|  | JK1 (0) | JK1 (1) |
| :-: | :-: | :--: | :--: | :-----: | :-----: | :-: | :-----: | :-----: |
| Q0  |  0  | `0`1 | `0`0 |  0`0`   |  0`0`   | \|  |   0X    |   0X    |
| Q1  |  0  | `1`1 | `0`0 |  0`1`   |  0`0`   | ->  |   1X    |   0X    |
| Q2  |  1  | `1`0 | `0`0 |  1`1`   |  1`0`   | \|  |   X0    |   X1    |
| Q3  |  1  | `1`0 | `1`0 |  1`1`   |  1`1`   | \|  |   X0    |   X0    |
Y

|  Q  | q0  |  0   |  1   | JK0 (0) | JK0 (1) | \|  | JK0 (0) | JK0 (1) |
| :-: | :-: | :--: | :--: | :-----: | :-----: | :-: | :-----: | :-----: |
| Q0  |  0  | 0`1` | 0`0` |  0`1`   |  0`0`   | \|  |   1X    |   0X    |
| Q1  |  1  | 1`1` | 0`0` |  1`1`   |  1`0`   | ->  |   X0    |   X1    |
| Q2  |  1  | 1`0` | 0`0` |  1`0`   |  1`0`   | \|  |   X1    |   X1    |
| Q3  |  0  | 1`0` | 1`0` |  0`0`   |  0`0`   | \|  |   0X    |   0X    |

____
Podemos armar mapas de karnaugh usando esto para sacar las funciones de transicion.
Se arman por columna, tal que J1 va a tener ambos parentesis izq y K1 ambos derechos.

