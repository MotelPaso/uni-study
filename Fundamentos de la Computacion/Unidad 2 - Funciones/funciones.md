---
Object type:
  - Unidad
Backlinks:
  - Fundamentos de la Computacion
Creation date: 2026-01-31T20:03:22Z
Links:
  - Fundamentos de la Computacion
---
# Definición:
$$
f : x \rightarrow y
$$
$$
\forall x \in X, y\in Y \mid \exists f(x) = y
$$

Para todo $x \in X$, se le llamara Pre-Imagen.
Para todo $y \in Y$, se le llamara Imagen o Rango.

# Funciones Características:

### Ejemplo:
$$
\begin{aligned}
\begin{array}
&f(x) = &0\ \text{if } x \notin A\\ &1 \text{ if } x \in A
\end{array}\\
f: Z \rightarrow \{0,1\}
\end{aligned}
$$
## Composición de funciones:
#### Ejemplo:
$$
\begin{aligned}
&f: x \rightarrow y \\
&g: y \rightarrow z \\
&h: x \rightarrow z \\
&h = g\ (\ f\ (x)\ ) \implies x \rightarrow z
\end{aligned}
$$
# Propiedades:   
## Inyectiva:   
Se le dice inyectiva a las funciones que, al evaluar cualquier valor dentro de una función definida, la imagen que retorna es unica para ese valor.   
> No existen valores repetidos.   
### Definición:   
Para todo $a, b$ en $X$, si $a$ no es igual a $b$, entonces una función evaluada en $a$, no es igual a la misma función evaluada en $b$.   

$$
\begin{aligned}
&\forall\ a,b \in X, a \neq b \Longrightarrow f(a) \neq f(b)\\
&\text{Equivalente a:}\\
&\forall\ a,b \in X, a=b \Longrightarrow f(a) = f(b)
\end{aligned}
$$
### Ejemplos:   

$$
\begin{aligned}
&f(x) = 2x + 5 \\
\text{Forma 1 (Definición):} && \text{Forma 2 (Derivada): }\\
f(x) = f(y) \longrightarrow 2x + 5 = 2y + 5\  && f'(x) = 2 \rightarrow \text{Constante} \\
2x = 2y\ \big / :2 &&\therefore \text{Inyectiva}\\
x = y  \therefore \text{Inyectiva}
\end{aligned}
$$

$$
\begin{gathered}
f(x) = x^2\\ 
f(x) = f(y) \rightarrow x^2 = y^2 \big/ \verb=^= 1/2\\
\pm x = \pm y \therefore \text{No inyectiva.}
\end{gathered}
$$
## Sobreyectiva:   
Las funciones sobreyectivas son las funciones que para toda imagen, exista, como mínimo, una pre-imagen.   
### Definición:   
Para todo $y$ perteneciente al conjunto $Y$, existe un $x$ de $X$, que cumple que una función evaluada en $x$, es igual a $y$.   

$$
\forall\ y \in Y \quad \exists\ x \in X : f(x) = y
$$

>[!NOTE]
>En palabras simples, que el codominio sea igual al rango.
### Ejemplo:   

$$
\begin{aligned}
f : \mathbb{R} \rightarrow \mathbb{R} \quad f(x) = 3x-6\\
y = 3x -6\\
\frac{y+6}{3} = x \\y\in \mathbb{R} \therefore \text{Sobreyectiva}
\end{aligned}
$$
> Se tiene que considerar los conjuntos de **dominio**, **codominio** y el **rango** de la función.
## Biyectiva:   
Son las funciones que son tanto inyectivas como sobreyectivas, se demuestran trivialmente al demostrar sus dependencias.

## Inversa:
Dado $f:X \rightarrow Y$, se define la inversa como:
$$
f^{-1} : Y \rightarrow X
$$
Logica.
Automatas finitos.
Maquinas de Turing






