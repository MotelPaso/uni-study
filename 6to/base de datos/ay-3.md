# Normalizacion

Es un proceso util para minimizar la redundancia y garantizar la integridad de los datos.

> Basicamente, necesitamos un solo lugar de donde buscar los datos, no deben repetirse, nuestros objetos deben ser independientes entre si.
### Problemas que resuelve.
No puedo agregar una nueva caracteristica si no tengo nadie que lo contrate, alta cohecion.
No puedo borrar un unico atributo de una entidad.
Tablas con elementos repetidos.

## Como normalizar
Para que se cumplan, deben estar todas hacia arriba, 2FN no puede ser si no esta primero 1FN.
#### 0 FN - Sin formalizar
#### 1 FN - Forma Normal
##### Definicion:
Una tabla se encuentra en 1FN $\Rightarrow$ todos los atributos son datos atomicos.
##### Como arreglar:
Se dividen todos los datos en una lista en objetos (tablas) diferentes.

#### 2FN
##### Definicion:
Una tabla se encuentra en 2FN $\Rightarrow$ cada atributo no clave depende solo de la clave principal importante.
##### Como arreglar:
Separar los objetos de una tabla que tienen poca cohesion entre ellos, a la tabla *turnos* se puede dividir en | *empleados*  | *horarios* |, en lugar de tener todo junto en una tabla.

#### 3FN
##### Definicion:
Una tabla se encuentra en 3FN $\Rightarrow$ ningun atributo no clave depende transitivamente de otro no clave de otra tabla.
##### Como arreglar:
Dividir los objetos de una tabla en diferentes tablas, llamandose entre ellas por ID.
A la tabla *turnos* se puede separar en *empleados* | *horarios* | quedando en 2FN.
Para llegar a 3FN, se puede separar en *empleados* | *sueldo_turno* | *horarios*.
Esto es para si se quiere saber el sueldo en un turno, se va directamente a sueldo turno, y no se pasa a empleados y desde empleados se "infiere" el sueldo desde un empleado X.
#### BCFN

> Es un poco rebuscada, asi que no se usa demasiado.
##### Conceptos:
###### Super llave:
Conjunto de llaves posibles para "llamar" a la tabla y que devuelva los datos que necesitamos, pueden ser muchas llaves para las tablas.
###### Llave candidata:
Super llaves minimas, que al quitarle atributos perderian su significado o perderian precision.
Desde las llaves candidatas se elige la clave primaria para la tabla.
###### Atributos primos:
Son parte de una llave candidata.
##### Definicion:
Una tabla se encuentra en BCFN $\Rightarrow$ no existen dependencias funcionales no triviales de los atributos no sean un conjunto de la clave cantidata
##### Como arreglar:
Cuando llegamos a BCNF, nuestra tabla ya esta casi lista, pero nos puede quedar algunas redundancias de tener 3 claves primarias en una tabla.
Cuando ocurre esto, podemos dividir esa tabla en dos, para separar sus dependencias.
