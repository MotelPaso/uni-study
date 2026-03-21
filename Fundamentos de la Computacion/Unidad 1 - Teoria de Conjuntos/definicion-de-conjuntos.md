---
Object type:
    - Apuntes
Backlinks:
    - teoria-de-conjuntos
    - Apuntes
Creation date: "2026-01-25T03:35:08Z"
Links:
    - teoria-de-conjuntos
---
# Definición de Conjuntos   
Conjuntos, subconjuntos, cardinalidad y conjuntos potencia.   
### Resumen:   
Son una coleccion de elementos $\infty$ o no.
Sin orden, ni repeticiones.   
Cardinalidad = len(set), solo cuentan los objetos "grandes"
Existe un conjunto vacio, con len 0.   
Un subconjunto tiene que estar en el conjunto grande, con $\subseteq$.
Conjunto vacio siempre es subconjunto.   
Conjunto potencia son todos los subconjuntos posibles.      
   
# Conjuntos / Sets   

Un conjunto es una colección de objetos llamados **elementos**. 
##### Propiedades:
- Pueden ser finitos o infinitos.   
$$
A = \{ 1,2,3,4,5,6,7,8,9\} \hspace{1cm} Z^+ =\{1, 2,3,4, \dots \}  
$$

- Los elementos se pueden repetir, pero solo se listan una vez.   
$$
\{a,b,b,a,c\} = \{a,b,c\}
$$

- No importa el orden.   
$$
\{3,2,1\} = \{1,2,3\}
$$
> Los conjuntos numéricos $\mathbb{N, Z, Q }$ son también conjuntos.   
## Conjunto vacío: $\emptyset$   
Se define como un conjunto sin ningún elemento con las siguientes propiedades.   
$$
\emptyset = \{\ \} \hspace{16px} |\,\emptyset \, | = 0 \hspace{16px} \left| \{ \emptyset\}\right| = 1
$$

## Subconjuntos:   
Para que un conjunto $A$ se considere como un subconjunto de $B$, todos los elementos de $A$ **tienen** que estar en $B$.
Se denota con $\subset$ o $\subseteq$, dependiendo del caso.   
Escrito: $A \subseteq B$, A es un subconjunto de B.    
$$
\begin{aligned}
\{a, b, a, a\} \subseteq \{a,b,c\} &\longrightarrow \{ a,b\} \subseteq \{a,b,c\} \text{True}\\
\{a\} \subseteq \{\{a\}\} \text{False}  &\longrightarrow \{a\} \nsubseteq \{\{a\}\}
\end{aligned} 
$$
Falso, porque tiene que ser exactamente el mismo elemento, estamos preguntando si "a" esta en el conjunto { "{a}" } y no lo está, no importa si hay un conjunto dentro que tenga "a".  

$$
\emptyset \subseteq \{x,y,z\} \hspace{10px} \text{True}
$$

No hay nada en el conjunto vacío, así que si o si esta en el conjunto.   
## Elementos y cardinalidad   
Un elemento es cualquier objeto que este dentro de un set, esto puede ser tanto un numero como otro conjunto.   
La cardinalidad de un set es su **longitud**, contando cada elemento que forma parte de este.   
> Un conjunto dentro del conjunto solo cuenta como un elemento para la cardinalidad, sus elementos interiores no cuentan.   
### Ejemplo:   
> Se tiene el set $A = \{1,2,3, \{ 5, 6\}\}$, podríamos decir que:   
> "1" es un elemento de A, $1 \in A$.   
> "4 no es un elemento de A, $4 \notin A$   
> La cardinalidad de A es 4, $|A| = 4$   
## Conjunto Potencia:   
El conjunto potencia es aquel conjunto que contiene todos los posibles subconjuntos de un conjunto determinado. 
$$
\begin{aligned}
A = \{a,b\}\\
p(A) = \{ \{a,b\}, \{a\}, \{b\}, \{\emptyset\} \}
\end{aligned}
$$
- Un conjunto potencia siempre contiene el conjunto inicial y el conjunto vacío.   
- El conjunto inicial no siempre es un subconjunto del conjunto potencia.   
- La cardinalidad de un conjunto potencia es igual a dos elevado a la cardinalidad del conjunto inicial.
$$
|A| = n  \Rightarrow \left|p(A)\right| = 2^n
$$

