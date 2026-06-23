$$
\begin{aligned}
&\omega = 2\pi f\\
&V_{rms} = \frac{V_{peak}}{\sqrt{2}}\\
&V = I \cdot R\\

\end{aligned}
$$



## Capacitores en CA
### Potencia en un Capacitor
El capacitor solo guarda potencia *reactiva*. Se utiliza la misma ecuación que para la potencia.
$$
P = \frac{V}{X_c} = V \cdot I = I^2 \cdot X_C
$$
### Reactancia Capacitiva ($X_C$)
$$
X_c = \frac{1}{\omega c}
$$
Como la reactancia de un capacitor es igual a la resistencia de un resistor, podemos hacer la siguiente formula.
$$
I = \frac V {X_C}
$$
> Ver ejemplos 12 - 18 y 12 - 19 (pag. 500)

## Inductancia
Es "similar" a la resistencia de un resistor, pero para bobinas. 
Su unidad de medida es el Henry (H).
En serie aumentan, en paralelo disminuyen.
$$
\begin{aligned}
\text{Serie: }& L_T = L_1 + L_2 + \cdots+ L_n\\
\text{Paralelo: }& L_T = \frac{1}{\Large{\frac{1}{L_1}} + \frac{1}{L_2} + \cdots+ \frac{1}{L_n}}
\end{aligned}
$$
> Ver ejemplo 13-4 y 13-5 (pag. 534)

La corriente y el voltaje aplicado en una bobina puede ser calculado usando Ley de Ohm, igual que a una resistencia.
### Potencia en una Reactancia
Tiene potencia real, pero es muy baja ($\simeq 0$), así que en la mayoría de los casos es ignorada.
La potencia reactiva se puede calcular usando las formulas de siempre.
$$
P = \frac{V}{X_L} = V \cdot I = I^2 \cdot X_L
$$

### Reactancia Inductiva ($X_L$)
$$
X_L = 2\pi f L
$$

>[!IMPORTANT]
> La reactancia inductiva y la reactancia capacitiva actuan como numeros [[Electrotecnia/Corriente Alterna/Números Complejos.md|imaginarios]], pero pueden ser sumados con la resistencia.
## Impedancia:
$$
\begin{aligned}
Z &= R -jX_c\\
V &= IZ
\end{aligned}
$$
> Ver ejemplo 15-11 (pag. 619)

## Factor de Potencia:
$$
PF = \cos\theta
$$
circuito RLC 728!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# Ejemplos
##### Ejemplo 11 - 14
Nos piden el voltaje entre los extremos de cada resistor y la corriente rms.
Mientras que podríamos usar divisor de voltaje, nos es mejor utilizar ley de Ohm debido a que nos pide también la corriente.
Para calcular la potencia total podemos utilizar cualquier formula, pero siempre tomando la resistencia total en cuenta.