# Clase 3: CPU   
# Arquitectura de una CPU   
Principalmente, un computador almacena datos/programar, ejecuta instrucciones predefinidas, y devuelve resultados calculados, a una velocidad asociada a su "clock" principal, medido en hercios *hz*, ahora llegando a los *Ghz*.
## Modelo de Von Neumann:   
Divide las tareas del computador en 3 partes, memoria, CPU y Input/Output, se comunican mediante buses (canales), que son sistemas de comunicaciones dentro del computador, siendo basados en tanto en hardware (cables) como en software (drivers, protocolos como ASCII).   
Los datos e instrucciones del sistema residen en memoria y su alfabeto es el binario.   
La maquina analítica fue creada usando este modelo, y podía realizar varios cálculos complejos, como logaritmos o integrales definidas, usaba tarjetas perforadas como input.   
## Harvard:   
Utiliza dos memorias independientes, una para los datos y otra para las instrucciones, permitiendo memorias de distinto largo, tamaño o hasta distinta tecnologia.   
Comparando con el modelo de Von Neumann, tenia una arquitectura más simple, pero no peor, la CPU podía ser más flexible y hacer menos operaciones para el mismo problema.   
## Multiprocesadores:   
Dividen el trabajo en multiples procesadores, cada uno con una memoria local, conectados tanto a una memoria principal como un I/O.   
El mayor problema de esta arquitectura fue la coherencia entre maquinas, causando race conditions, donde no se podia definir una verdad clara sin tener que consultar a la memoria principal, además de existir problemas no paralelizables, como el calculo de números Fibonacci, requiriendo un solo procesador.   
Desde aqui nacen los:   
## Sistemas distribuidos:   
Siendo estos maquinas basadas en el modelo de Von Neumann o Harvard, teniendo su propia memoria o I/O, pero que conversaban entre ellas mediante una red de interconexion, funcionando como nodos independientes.   
Los problemas son los mismos que en los multiprocesadores, pero la diferencia es que es más fácil de incorporar nodos y quitarlos del sistema, facilitando mejoras horizontales.    
# Unidad Central de Procesammiento:   
Es el cerebro de la computadora, es responsable de ejecutar operaciones, controlar el flujo del programa y los circuitos internos del sistema.   
## Responsabilidades:   
### 1. Ejecucion de Algoritmos:   
Los algoritmos son escritos secuencialmente en memoria, tal que asi: 

| 1101110111   <br> | LOAD(07)   <br> |      Carga a memoria el dato en la posicion 7.   <br> |
|:------------------|:----------------|:------------------------------------------------------|
| 1100011001   <br> |  ADD(09)   <br> |           Le agrega el dato en la posicion 9.    <br> |
| 1110001010   <br> | MOVE(0A)   <br> | Mueve el dato en memoria a la posicion 10 (A).   <br> |
| 1110000000   <br> | GOTO(08)   <br> |              Salta el puntero a la posicion 8.   <br> |

Funciona en base a un instruction pointer, que lleva el control de donde estamos en función al mapa.   
> Los ciclos while infinitos pasan por esto, acciones GOTO() que se llaman en bucle.   
> También por esto es O(1) acceder a elementos dentro de una lista, debido a que es solo un GOTO().   

### Registros Control/Estado:   
Controlan el funcionamiento de la CPU:   
- program counter o instruction pointer.   
- instruction register, memory address register, memory buffer register.   
- tambien existe un PSW, que contiene el estado de la operacion actual.   
   
> El comando SUDO caeria dentro de esto.   

   
   
