### Transformar decimal a binario:

Para transformar decimal ($n$) a binario, se siguen los siguientes pasos:
##### Signo
El signo del numero se traduce literalmente, si es negativo, 1, si es positivo, 0.
##### Exponente
1. Sacar el $\log_2 n$, que se puede traducir en:
	$$
	\log_2 n = \frac{\log n}{\log 2}
	$$
2. Al resultado se le quitan los decimales, ese resultado es tu exponente.
	$$
	\log_2 n = 1.958 \rightarrow \exp =1
	$$
3. A tu exponente se le suma $127$, el resultado de la suma se convierte en binario.
	$$
	\exp = 7 \rightarrow 127+7 = 134 \rightarrow 1000'0110
	$$
	> Un truco para ver el numero rápidamente es restarle 1 a tu exponente, es decir:
	> $\exp = 7 \rightarrow 7 - 1 = 6 \rightarrow 0110 \rightarrow 1000'0110$
	> Aunque segun la 'teoria', la parte de arriba es más correcta.

##### Mantisa
1. Dividir el numero en 2 elevado a tu exponente.
	$$
	\exp = 6 \rightarrow \frac{n}{2^6}
	$$
2. A este numero, se le quita la parte decimal y se convierte en binario usando la formula de multiplicaciones repetidas.
$$
\begin{aligned}
0.46875 &\cdot 2 = 0\\
0.9375 &\cdot 2 = 1\\
0.875 & \cdot 2 = 1\\
0.75 & \cdot 2 = 1 \\
0.5 & \cdot 2 = 1 \\
0 & \cdot 2 = 0\\
&\cdots
\end{aligned}
$$
	Esto se repite 23 veces...

3.  El 'resto' encontrado se llena de arriba a abajo, creando la mantisa:
	$$
	01111000\dots
	$$
Finalmente, se junta todo en el siguiente orden:
$$
\text{signo|exponente|mantisa}
$$
Deben ser si o si 32 digitos.

### Transformar Binario a Decimal:

Para el signo y el exponente, es el mismo proceso, pero inverso.

##### Mantisa
La mantisa representa el numero completo, el exponente nos dice cuantas veces movemos la coma hacia la izquierda, agregando un 1 implicito al principio.
$$
0111'1000 \cdots \rightarrow \exp =3 \rightarrow 1011.1'000
$$
Ahora, se puede pasar este numero a decimal descomponiendo y multiplicando por 2 elevado a la posición:
$$
1011.1000 = 2^3 + 2^1 + 2^0. 2^{-1}
$$
Los valores con 0s se cuenta solo su posicion, no se suman
