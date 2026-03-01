---
Object type:
    - Apuntes
Backlinks:
    - teoria-de-conjuntos
    - Apuntes
Creation date: "2026-02-10T21:45:48Z"
Links:
    - Fundamentos de la Computacion
---
## Propiedades:   
### Reflexiva:   

$$
\forall\ a\in A \mid (a,a) \in R
$$

Un conjunto sera reflexivo si todo elemento de $a$ se relaciona con si mismo.   

$$
A = \{1,2,3\}\hspace{1cm} R = \{ (1,1),(2,2),(3,3), \cdots  \}
$$

### Simétrica:   

$$
(a,b) \in R \rightarrow (b,a) \in R
$$

Una relación sera simétrica si todo par de elementos $(a,b)$ existe relacionado con el mismo par con orden invertido $(b,a)$. Esto tiene que mantenerse para todos los pares en la relación, excepto los pares reflexivos.   

$$
A = \{1,2,3\}\hspace{1cm} R = \{ (1,2),(2,1),(3,2),(2,3) \}
$$

> Pueden faltar ambos pares, faltando en el ejemplo anterior $(3,1), (1,3)$. Solo se rompe si solo hay uno de los dos en la relacion.   

### Antisimétrica:   

$$
(a,b) \in R \land a \neq b \rightarrow (b,a) \notin R
$$

Una relación será antisimétrica si existe un par de elementos $(a,b)$ donde $a$ no es igual a $b$, y su orden invertido **no** existe en la relación.   

$$
\begin{aligned}
A = \{1,2,3\}\hspace{29px} &R_1 = \{ (1,2),(3,2) \}\  \text{Antisimétrica}\\
&R_2 = \{(1,2),(2,1)\}\ \text{No Antisimetrica}
\end{aligned}
$$

### Transitiva:   

$$
(a,b) \in R \land (b,c) \in R \rightarrow (a,c) \in R
$$

Una relación será transitiva si existen dos pares entre 3 elementos diferentes $(a,b), (b,c)$, entonces $(a,c)$ también debe ser parte de la relación.   

$$
A = \{1,2,3\}\hspace{1cm} R = \{ (1,2),(2,3),(1,3) \}
$$

> El orden **si** importa aquí, el elemento $(3,1)$ no nos va a servir.    





