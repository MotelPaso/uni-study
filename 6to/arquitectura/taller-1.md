---
Status: Done
Done: true
Curso: arquitectura-de-computadores
---
Problema 1:

En las direcciones #30 y #31 de memoria se encuentran los números iniciales de una sucesión de Fibonacci. Estos los debe definir como enteros sucesivos, no mayores a 30. Por ejemplo, pueden ser 20 y 21. También debe probar con la sucesión básica que parte con 0 y 1.

Se ingresa un número por teclado que corresponde a la cantidad de términos de la sucesión que deben generarse. Nunca se pedirá más de 10 términos calculados.

Como debiera saber, la sucesión de Fibonacci, dados los primeros términos $a_0$ y $a_1$ se genera según

Esto da origen a la conocida sucesión cuando $a_0=0$ y $a_1=1$ que es: 0,1,1,2,3,5,8,13,21,34, etc, etc.

Nótese que el primer término generado es $a_2$

Los términos de la sucesión deben presentarse en pantalla.

Problema 2:

A partir de la dirección 100 de memoria se encuentran los siguientes datos binarios:
```python
#100
101101010001
110000010100010101101111
1010
1111100001111
11111100
110
```


El objetivo es multiplicarlos por pares y dejar los tres resultados a partir de la dirección 200 de memoria. Note que, por las características de la multiplicación, cada resultado ocupará dos localidades de memoria.

Adicionalmente debe dividir el dato que está en la dirección 103 entre aquel que se encuentra en 104. El resultado debe ocupar las direcciones después del último resultado de multiplicación anterior.

Para cada caso, debe comparar los resultados, con la forma decimal.