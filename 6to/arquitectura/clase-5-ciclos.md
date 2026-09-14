# Clase 5: Ciclos   
## Fetch:   
Su proposito es identificar la siguiente instruccion a ejecutar.   
```
BUS = PC # Enviar el PC a el bus de datos
MAR <- BUS # Saca del bus la direccion del PC y la guarda en el memory address register
MDR <- M[MAR] # Eligiendo esa memoria guardada, se lee en el memory data register
BUS = MDR # Se pasa al bus para transportarla
IR <- BUS # Desde el bus, ingresar en el intruction register
PC <- PC + 1 # Avanzar uno en el program counter
```
Se puede obviar el uso del bus, haciendo esto:   
```
MAR <- PC;
MDR <- M[MAR];
IR <- MDR;
PC <- PC + 1;
```
Esto es un ciclo al usar un programa.   

$$
\sqrt{\frac{1}{T_1 - T_2} \int^{T_2}_{T_1}[f(t)^2dt]}
$$
