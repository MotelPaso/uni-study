# Ay 2   
|                     Torneos<br>titular<br>suplentes   <br> |                 Valorant<br>5 <br>3    <br> |                  Rocket<br>3<br>2   <br> |                      Dota<br>5<br>3   <br> |   |
|:-----------------------------------------------------------|:--------------------------------------------|:-----------------------------------------|:-------------------------------------------|:--|
|                         Equipos<br>nombre<br>Torneo   <br> |                                             |                                          |                                            |   |
| Alumnos<br>nombre<br>rut unico<br>carrera<br>Equipo   <br> |                                             |                                          |                                            |   |
|            Evento<br>fecha\_inicio<br>fecha\_cierre   <br> | Partida<br>modalidad<br>fase<br><br>   <br> | Presentacion<br>nombre\_banda<br>   <br> |                                            |   |
|                    Entradas<br>Persona<br>stock<br>   <br> |       Diaria<br>dia<br>cant<br>valor   <br> |            Doble<br>cant<br>valor   <br> | VIP<br>cant<br>valor<br>estado\_kit   <br> |   |
|                            Persona<br>nombre<br>rut   <br> |                                             |                                          |                                            |   |

Relaciones   
|     Equipo N alumnos   <br> |      Alumno 1 equipo   <br> |    alumno integra a equipo   <br> |
|:----------------------------|:----------------------------|:----------------------------------|
|  Partida 2<br>Equipo   <br> | Equipo N<br>Partidas   <br> |    Equipo juega<br>partida   <br> |
|   Equipo 1<br>Torneo   <br> |  Torneo N<br>equipos   <br> | Equipo participa en torneo   <br> |
| Persona 1<br>Entrada   <br> | Entrada 1<br>Persona   <br> |        Persona usa Entrada   <br> |

