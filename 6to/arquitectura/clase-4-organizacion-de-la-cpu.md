# Clase 4: Organizacion de la CPU   
## Registros:   
Un registro es una seccion pequeña de memoria de acceso muy rapido, donde se almacenan temporalmente los datos de las operaciones actuales de la CPU, pueden ser tanto visibles para el usuario o de control/estado.   
Para el usuario es optimo tener entre 8 y 32, sacado por prueba y error; solo se necesitan tantos como variables tenga mi programa, con demasiados no reducen las referencias y hacen la arquitectura y programacion compleja.   
   
### Componentes de la CPU:   
1. Contador de programa   
2. Registro de direcciones   
3. Registro de datos   
4. Buses.   
5. Registro de instrucciones   
6. Acumulador   
7. Unidad aritmetico logica   
8. Unidad de Control   
9. Otros registros   
   
### Ciclo de Instruccion   
El computador esta siempre haciendo "algo", ejecutando algún programa en el fondo, puede estar haciendo una de dos cosas, buscando una instrucción en la memoria principal y ejecutando la instrucción.   
Las instrucciones tienen un formato especifico, tal que:   

$$
\text{<codigo de operacion>}[\text{<operando>}, [\text{<operandos>}]]
$$
Siendo guardados en hexadecimal, usando el formato Big Endian, donde el dato más importante queda primero.   
   
   
   
### Tipos de Buses:   
Los buses de datos llevan datos, los buses de direcciones direccionan la memoria RAM y ROM, y el bus de control lleva las señales de comando a toda la CPU.   
   
- Unidad aritmetico logica:   
    Realiza operaciones aritmeticas y logicas binarias y unarias (con un solo componente; ej a = -a), versioes avanzadas permites multiplicar, dividir y punto flotante.   
       
   
### Unidad de Control:   
   
