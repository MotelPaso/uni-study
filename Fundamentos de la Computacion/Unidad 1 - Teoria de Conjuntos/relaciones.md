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

Es una manera de describir cuales elementos están conectados entre dos conjuntos:
## Definición:
Siendo $A$ y $B$ conjuntos. 
Una relación binaria desde A a B es cualquier subconjunto $R\subseteq A\times B$ 
Si $a,b\in R, \implies aRb$.
#### Ejemplo: La relación $\text{Menor-A}$ para los números reales:
Se define la relación $L$ desde $R$ a $R$ como lo siguiente:
$$
\forall x,y : xLy \Longleftrightarrow x < y
$$
1. $57L53$ ? False
2. $143L143$ ? False
3. $-17L-14$ ? True
4. $-35L1$ ? True
### La inversa de una relación:
Se define $R$ como una relación de $A$ a $B$, definimos la inversa como:
$$
\begin{aligned}
&R^{-1} = \{(y,x) \in B\times A \mid (x,y) \in R\} \\
&\forall x\in A, y\in B: (y,x) \in R^{-1} \Longleftrightarrow (x,y) \in R
\end{aligned}
$$
#### Ejemplo:
Definiremos R como la relación de division desde A a B.
$$
\begin{aligned}
&A = \{2,3,4\} \qquad B=\{2,6,8\}\\
&\forall(x,y) \in A \times B: xRy \Longleftrightarrow \frac{y}{x}\\
R &= \{(2,2), (2,6), (2,8), (3,6), (4,8) \}\\
R^{-1} &= \{(2,2), (6,2), (8,2), (3,6), (8,4)\}
\end{aligned}
$$
### Las relaciones en grafo dirigido:
Para todo punto $x$ e $y$ en $A$, tiene que existir una relación desde $x$ a $y$ $\iff$ $xRy \iff (x,y) \in R$
###### Ejemplo:
Denotamos $A= \{3,4,5,6,7,8\}$ y se define una relación R en A de la siguiente forma:
$$
\forall x,y\in A: xRy \iff \frac{(x-y)} {2}
$$
> El resultado de la division es una division entera, sin decimales.

Resumido, cada numero se relaciona con si mismo y con los números de su misma paridad (par o impar), se debe realizar un dibujo de cada elemento como un nodo "apuntando" a sus nodos relacionados.

##### Ejemplo 2:
Denotar $A=\{2,3,4,6,7,9\}$, se define una relacion $R$ en $A$ de la siguiente forma:
$$
\forall x,y \in A: xRy \iff \frac{(x-y)}{3}
$$
Los números multiplos de 3 se relacionan entre ellos.
El 4 y 7 se relacionan mutuamente.
2 se relaciona solo con si mismo.

## Propiedades:   
### Reflexiva:   
Una relación será reflexiva si todo elemento de $a$ se relaciona con si mismo.   

$$
\begin{aligned}
&\forall\ a\in A \mid (a,a) \in R\\
&A = \{1,2,3\}\hspace{1cm} R = \{ (1,1),(2,2),(3,3), \cdots  \}
\end{aligned}
$$
### Simétrica:   
Una relación sera simétrica si todo par de elementos $(a,b)$ existe relacionado con el mismo par con orden invertido $(b,a)$. Esto tiene que mantenerse para todos los pares en la relación, excepto los pares reflexivos.   
$$
\begin{aligned}
&\forall a,b\in R:(a,b) \in R \iff (b,a) \in R\\
&A = \{1,2,3\}\hspace{1cm} R = \{ (1,2),(2,1),(3,2),(2,3) \}
\end{aligned}
$$
>[!IMPORTANT]
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