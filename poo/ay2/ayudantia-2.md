<h1 align='center'>Ayudantía 2 - POO Invierno</h1> <h5 align='center'>Profesor: Cristhian Rabi<br> Ayudante: Paulo Araya</h5>
<h6 align='center'>28 de Julio de 2026</h6>

Una empresa necesita una forma más rápida de administrar a sus empleados. Haremos una simulación en Java de cómo se podría ver un sistema real para manejar y mostrar los datos. 

La empresa se divide en Proyectos y Departamentos y trabajan Empleados.
Los Empleados poseen ID, Nombre, Rol y Sueldo.
Cada Departamento tiene un jefe (que es un empleado más) y 7 empleados a su cargo. 
Cada Proyecto tiene un líder (un empleado) y un equipo de trabajo, compuesto por 10 empleados.
Un Empleado puede trabajar en más de un Proyecto o Departamento.

Escribe un programa en Java que permita cargar una empresa de ejemplo y reporte los siguientes datos:
1. Mostrar todos los departamentos de la empresa.
2. Mostrar todos los proyectos de la empresa.
3. Aumentar el sueldo de un empleado, buscándolo por nombre.
	- No se puede hacer un aumento negativo.
4. Buscar un empleado por nombre y mostrar en qué departamento(s) y proyecto(s) aparece.
5. Eliminar un Proyecto por su ID.
6. Eliminar un Departamento por su ID.
7. Despedir un empleado.
	- Para proteger los datos, se deberá ingresar una contraseña antes de poder eliminar algo o despedir un empleado.
	- Al eliminar un dato, se debe buscar y eliminar toda referencia.

<h2 align='center'>Restricciones </h2>

- Ningún método debe sobrepasar las 30 líneas, apliquen abstracción donde sea necesario.
- Se debe hacer un buen manejo de memoria, procurando no duplicar objetos, no deben existir dos empleados con los mismos datos.
- Deben aplicar control de errores: si buscan un empleado que no existe, o ingresan una opción inválida, el programa no se debe detener.
- No pueden usar la librería List. Únicamente arreglos de tamaño fijo.
- No tienen que usar herencia.
- Dispondrán de una colección de archivos .csv para cargar los datos, estan conectados mediante IDs.

```text title:"Ejemplo de salida"
=== Sistema de Gestión de Empresa ===
Cargando empresa...
Empresa cargada!

Menu:
1. Mostrar departamentos.
2. Mostrar proyectos.
3. Aumentar sueldo a un empleado.
4. Buscar empleado por nombre.
5. Eliminar Proyecto.
6. Eliminar Departamento.
7. Despedir empleado.
Opcion: X

// Opcion 1
--- Departamentos ---
Departamento: Ingeniería
  Jefe: Ana Torres - $55000.0
  Empleados:
    - Ana Torres - Backend Developer - $55000.0
    - Pedro Soto - Frontend Developer - $48000.0

Departamento: Ventas
  Jefe: Marcos Díaz - $52000.0
  Empleados:
    - Marcos Díaz - Jefe de Ventas - $52000.0

// Opcion 2
--- Proyectos ---
Proyecto: Payments API
  Presupuesto: $20000.0
  Lider: Ana Torres - $55000.0
  Equipo:
    - Ana Torres - Backend Developer - $55000.0
    - Pedro Soto - Frontend Developer - $48000.0

// Opcion 3
Ingrese el nombre del empleado: Ignacio Pasten
Ingrese el monto del aumento: 60000
Sueldo actualizado. Ignacio Pasten ahora gana $120000.0

// Opcion 4
Ingrese el nombre a buscar: Ana Torres

Ana Torres encontrada:
  - Departamento: Ingeniería (Jefe) - $55000.0
  - Proyecto: Payments API (Lider) - $55000.0

// Opcion 5, 6, 7
Accion destructiva, se necesita permisos de administrador.
Ingrese su contraseña: ASdwxcn"2Sdbnn3SdhjkaQ

Ingrese el ID a eliminar: 1

Proyecto: Payments API
Está seguro que quiere eliminar este proyecto? (s/n): s
Proyecto eliminado...



```