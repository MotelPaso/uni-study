# Ay 1   
|        Empleado<br>rut unique<br>nombre<br>correo<br>fecha\_contrato   <br> | Desarrollador<br>lenguaje<br>experiencia   <br> |  Diseñadores<br>herramienta<br>especialidad   <br> |                                     Empleado tiene varios proyectos<br>Empleado tiene un equipo X   <br> |   |
|:----------------------------------------------------------------------------|:------------------------------------------------|:---------------------------------------------------|:---------------------------------------------------------------------------------------------------------|:--|
| Proyectos<br>codigo unique<br>nombre<br>presupuesto<br>fecha\_inicio   <br> |                                                 |                                                    | proyecto tiene varios empleados<br>proyecto tiene un cliente<br>proyecto tiene varias tecnologias   <br> |   |
|                           Equipo<br>nombre<br>desc<br>fecha\_ini<br>   <br> |                                                 |                                                    |                                                                     Equipo tiene varios empleados   <br> |   |
|                           Cliente<br>rut<br>nombre<br>correo<br>pais   <br> |                                                 |                                                    |                                                                    cliente tiene varios proyectos   <br> |   |
|                              Tecnologia<br>nombre<br>tipo<br>version   <br> |                                                 |                                                    |                                                                 tecnologia tiene varios proyectos   <br> |   |

Relaciones   
| Equipo tiene empleados   <br> |    Proyecto tiene cliente   <br> |   |
|:------------------------------|:---------------------------------|:--|
|                               | Proyecto tiene tecnologia   <br> |   |
|                               |                                  |   |

