---
Object type:
    - Apuntes
Backlinks:
    - teoria-de-conjuntos
    - Apuntes
Creation date: "2026-01-25T22:35:02Z"
Links:
    - operaciones-de-un-conjunto
    - teoria-de-conjuntos
---
# Demostraciones   
Para realizar demostraciones, se debe seguir el lenguaje matemático de las demostraciones y la teoría de conjuntos.   
### Símbolos importantes:   
[[ operaciones-de-un-conjunto | Operaciones de un Conjunto ]]    
$\forall$: Para todos   
$\in$: Esta en "algo"   
$\notin$: No esta en "algo"   
$\land$: Y   
$\lor$: O   
$\cap$: Interseccion   
$\cup$: Union   
$\subseteq$: "Algo" es subconjunto de "Algo"   
$\forall$: Para todo   
## Relación entre dos conjuntos.   
Para demostrar que se cumple una relación entre dos conjuntos, como:   

$$
\overline{A\cup B} \subseteq \overline{A}\cap \overline{B}
$$

Se empieza definiendo un "caso base" desde un lado de la igualdad:   

$$
\forall x : x \in \overline{A\cup B}
$$

Desde aquí, empezamos a trabajar empleando las definiciones de cada operación posible en los conjuntos.   
> Cada definición que usemos nos sirve para "validar" nuestro trabajo.   
$$
\begin{aligned}
\forall x : x \in \overline{A\cup B} \qquad \text{/ def. complemento}\\
\forall x : x \notin {A\cup B} \qquad \text{/ def. unión}\\
\forall x : x \notin A \land x \notin B  \ \text{/ def. complemento}\\
\forall x : x \in \overline{A} \land x \in \overline{B} \ \text{/ def. intersección}\\
\forall x : x \in \overline{A} \cap \overline{B}
\end{aligned}
$$
Si la relación entre los conjuntos es un $=$, se tiene que realizar el trabajo dos veces, una empezando por la izquierda, y otra empezando por la derecha, el procedimiento es igual.   
## Tipos de demostraciones:   
### Demostración Directa:   





