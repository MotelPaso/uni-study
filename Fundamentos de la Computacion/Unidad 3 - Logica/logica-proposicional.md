---
Object type:
    - Apuntes
Backlinks:
    - fundamentos-de-logica
    - Apuntes
Creation date: "2026-02-07T15:51:05Z"
Links:
    - fundamentos-de-logica
---
# Lógica Proposicional   
Un enunciado es una oración que describe algún evento o cualidad de algo. Puede ser verdadera o falsa.
Las proposiciones se utilizan para "resumir" en un enunciado para su uso rápido en la lógica proposicional.
### Ejemplo:   
Tenemos estos enunciados:   
1. El cielo tiene nubes. $P$   
2. Si el cielo tiene nubes, entonces va a llover. $Q$   
3. Si el cielo no tiene nubes, entonces esta soleado. $S$   
Se escriben así en forma lógica:
$$
\begin{aligned}
1.\ &p\\
2.\ &p \implies q\\
3.\ &\lnot p \implies s\\
\end{aligned}
$$
> Las proposiciones se intentan escribir en mayúscula cuando se usan para un ejercicio y se escriben en minúscula cuando se usan demostraciones.   
## Símbolos:   
$$
\begin{aligned}
&\lnot p &\text{No p}\\
&p\lor q  &\text{p o q }\\
&p\land q  &\text{p y q}\\
&p \implies q &\text{Si p, entonces q}\\
&p \iff q & \text{Doble implicancia}\\
&p \otimes q &\text{Or exclusivo}\\
&& \text{Solo si no son iguales}
\end{aligned}
$$

## Propiedades:
Se mantiene la asociatividad, conmutabilidad, distributividad y Leyes de Morgan en la semántica lógica, pero se añaden algunas nuevas:
###### Contraposición:
$$
(P\implies Q)\iff (\lnot Q \implies \lnot P)
$$
###### Eliminación de la implicación:
$$
(P\implies Q) \iff (\lnot P \lor Q) 
$$
## Conceptos clave:
Se le llamará **contradicción** cuando exista un predicado que siempre sea falso, al contrario, cuando sea siempre verdadero se le llamará **tautología**. 
### Ejemplo con tablas de verdad:
Revisa si la proposición $(r→w)∧(w→r)$ es lógicamente equivalente a $¬r∨w$. Justifica con tabla de verdad.
> Una proposición es lógicamente equivalente a otra si y solo si tienen los mismos resultados booleanos en todos los casos.
$$
\begin{aligned}
&\begin{array}{|c|c|c|c|c|c|}
\hline
r & w & r \implies w & w \implies r & \lnot r \lor w & w \implies r \land r \implies w  \\
\hline
T & T & T & T & T & T \\
T & F & F & T & F & F \\
F & T & T & F & T & F \\
F & F & T & T & T & T \\
\hline
\end{array}\\
&\text{Como sus valores no son iguales, las proposiciones no son equivalentes.}
\end{aligned}
$$

