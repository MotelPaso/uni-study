---
Object type:
    - Unidad
Backlinks:
    - Fundamentos de la Computacion
Creation date: "2026-01-31T20:03:22Z"
Links:
    - Fundamentos de la Computacion
---
# Funciones   
# Tipos de Funciones:   
## Inyectiva:   
Se le dice inyectiva a las funciones que, al evaluar cualquier valor dentro de una función definida, la imagen que retorna es unica para ese valor.   
> No existen valores repetidos.   

### Definición:   
Para todo $a, b$ en $X$, si $a$ no es igual a $b$, entonces una función evaluada en $a$, no es igual a la misma función evaluada en $b$.   

$$
\begin{aligned}
\forall\ a,b \in X, a \neq b \Longrightarrow f(a) \neq f(b)\\
\text{Equivalente a:}\\
\forall\ a,b \in X, a=b \Longrightarrow f(a) = f(b)
\end{aligned}
$$

### Ejemplos:   

$$
\begin{aligned}
f(x) = 2x + 5 \\
\text{Forma 1 (Definición):}\\
f(x) = f(y) \longrightarrow 2x + 5 = 2y + 5\ \big / -5\\
2x = 2y\ \big / :2\\
x = y  \therefore \text{Inyectiva}\\
\\
\text{Forma 2:}\\
f'(x) = 2 \rightarrow \text{Constante} \therefore \text{Inyectiva}
\end{aligned}
$$

$$
\begin{aligned}
f(x) = x^2\\ 
f(x) = f(y) \rightarrow x^2 = y^2 \big/ \verb=^= 1/2\\
\pm x = \pm y \therefore \text{No inyectiva.}
\end{aligned}
$$

## Sobreyectiva:   
Las funciones sobreyectivas son las funciones que para toda imagen, exista, como mínimo, una preimagen.   
### Definición:   
Para todo $y$ perteneciente al conjunto $Y$, existe un $x$ de $X$, que cumple que una función evaluada en $x$, es igual a $y$.   

$$
\forall\ y \in Y \quad \exists\ x \in X : f(x) = y
$$

### Ejemplo:   

$$
\begin{aligned}
f : \R \rightarrow \R \quad f(x) = 3x-6\\
y = 3x -6\\
\frac{y+6}{3} = x \\y\in \R \therefore \text{Sobreyectiva}
\end{aligned}
$$

## Biyectiva:   
Son las funciones que son tanto inyectivas como sobreyectivas.   





