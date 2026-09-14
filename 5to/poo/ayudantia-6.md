<h1 align='center'>Ayudantía 6  - POO Invierno</h1>
<h5 align='center'>Profesor: Cristhian Rabi<br>  Ayudante: Paulo Araya</h5>
<h6 align='center'>04 de Agosto de 2026</h6>

Al restaurante de la ayudantía pasada le gustó tu sistema, así que te han vuelto a llamar para que resuelvas dos problemas que tienen:
#### 1. Ordenar Pedidos
Mientras que con el sistema anterior que hiciste los pedidos funcionan, necesitan un sistema con más restricciones para forzar un orden fijo de los pedidos, el pedido más viejo debe tener prioridad sobre los nuevos.

#### 2. Deshacer Pedidos
Muy seguido ocurren accidentes en la cocina y los clientes no quedan satisfechos, necesitan una forma de deshacer el pedido más reciente para que no lleguen a la mesa.

Para resolver estos problemas, implementaremos dos nuevas estructuras de datos, Pilas y Colas, una para cada uno.

<h2 align='center'>Restricciones </h2>

- No se puede usar las librerías de Java de Stack y Queue.
- Deben usar genéricos al implementar las estructuras.

```text title:"Ejemplo de Salida"
Se cargaron 5 Pedidos desde pedidos.txt

=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 5
Pedidos procesados: 0
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 1

Pedido procesado:
===
Pedido
Precio: $12.50
Platos: [hamburguesa, papas, fanta]
===
=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 4
Pedidos procesados: 1
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 1

Pedido procesado:
===
Pedido
Precio: $8.90
Platos: [ensalada, agua]
===

=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 3
Pedidos procesados: 2
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 2

Pedido deshecho: ===
Pedido
Precio: $8.90
Platos: [ensalada, agua]
===

=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 3
Pedidos procesados: 1
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 2

Pedido deshecho: ===
Pedido
Precio: $12.50
Platos: [hamburguesa, papas, fanta]
===

=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 3
Pedidos procesados: 0
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 2

No hay Pedidos para deshacer.

=== SISTEMA DE PEDIDOS ===
Pedidos pendientes: 3
Pedidos procesados: 0
1. Procesar siguiente pedido
2. Deshacer ultimo pedido
3. Salir
Seleccione una opcion: 3

Saliendo del sistema...

```
