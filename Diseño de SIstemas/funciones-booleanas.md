# Puertas Lógicas
### Ejercicios:
#### 1.
$$
\begin{aligned}
F_{(A,B,C)} =& AB + B\overline{C} + A\overline{B}C \mid A = 1 ;B = 1;C = 0\\
&11 + 11 + 100\\
&1 + 1 + 0 \implies 1
\end{aligned}
$$
Graficamente:
![[Pasted image 20260407110130.png]]
#### 2.
$$
\begin{aligned}
F_{(A,B,C)} = &\overline{AB} + AC + B\overline{C} \mid A = 0; B = 1; C = 0\\
&\overline{01} + 0\,0+ 1\,1\\
&0 + 0 + 1 \implies 1
\end{aligned}
$$
Graficamente:
![[Pasted image 20260407111003.png]]

## Algebra de Boole
### Teoremas:
Conmutabilidad: Orden no importa
Asociatividad: Se puede factorizar 
Distribucion: Se pueden distribuir terminos.
### Simplificacion | Manipulacion:
El 0 no inside en una puerta OR, y el 1 no inside en una puerta AND.
A + A = A
Si existe un 1 en una puerta OR, los demas valores no importan.
Si existe un 0 en una puerta AND, los demas valores no importa.
##### Opuesto:
$$
A + \overline{A} = 1 \qquad A\cdot \overline{A} = 0
$$
>[!NOTE]
>El opuesto tiene relacion con la fuerza, ya que independientemente del valor de A, existira un 0 y un 1 en la relacion.

Doble Negacion

### Ejemplo:
$$
\begin{aligned}
F_{A,B,C} &= A + \overline{A}B + AB + A\overline{B}& \text{Asociatividad} \\
&= A (1 + B) + \overline{A}B + \overline{B}A & \text{fuerza}\\
&= AB + \overline{A}B + \overline{B}A & \text{Asociatividad}\\
&= B (A + \overline{A}) + \overline{B}A &\text{diferencia}\\
&= B + \overline{B}A &\mid A+\overline {A}B = A+B \\ 
&= B + A \implies A + B
\end{aligned}
$$