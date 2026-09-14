# Clase 4: Limpieza de datos   
## Transformacion de Datos:   
Se busca una escala común para normalizar los parámetros que le pasamos un modelo de aprendizaje.   
### Normalizacion:   
Se lleva la columna a valores entre 0 y 1, guardando la escala de la variable:   

$$
X_{normalized} = \frac{X-X_{min}}{X_{max} - X_{min}}


$$
### Estandarizacion:   
Utilizando la media y la desviacion estandar, aplica la siguiente formula, es usualmente usada para datos normalmente distribuidos.   

$$
Z = \frac{X-\mu}{\sigma}
$$
### Escalado Robusto:   
Funciona igual a la estandarizacion, pero en su lugar utiliza la mediana y el rango intercuartilico.   

$$
X_{robust} = \frac{X-X_{median}}{IQR}

$$
### Tranformacion Logaritmica:   
Sirve para que los datos normalmente sesgados, se tranformen en una variable mas simetrica.   
Se utiliza para variables como ingresos o poblacion, o de tipo exponencial.   
### Escalado de Caracteristicas:   
## Eleccion de Metodo:   
 --- 
# Encoding:   
Podemos tranformar datos categoricos o no-numericos en valores numericos para ser usados en machine learning.   
### Label Encoding:   
Asignarle un numero unico a cada categoria,   
```
variables = ["small", "medio", "grande"]
numero = [1, 2, 3]
```
Esto asume que las etiquetas tienen un orden intrinsico, pero podria pasar que:   
```
variables = ["perro", "gato", "zorro"]
numero = [1, 2, 3]
```
Que realmente no tienen orden, además podria ser que el numero de muestras per clase sea disparejo, llevando a modelos sesgados.   
### One Hot Encoding (Dummy Encoding):   
Reemplaza las categorias en vectores binarios, haciendo una columna por valor, pero permite informacion redundante.   
### GroupBy:   
Se pueden agrupar las variables categoricas con variables numericas por su probabilidad, frecuencia o promedio.   
aa   
## Outliers   
Un outlier es un valor atipico en nuestra base de datos, que sale del promedio, de lo "normal" basado en los tipos de datos que tenemos, como un billonario.   
Hay muchos origenes de outliers, sean intencionales o errores.   
### Formas de detectar outliers:   
1. Aplicar estandarizacion, si el valor absoluto obtenido es mayor a 3, cuenta como outlier.   
2. Aplicando el rango intercuartilico, con los limites de Q1 - 1.5IQR o Q3 + 1.5 IQR.
En un grafico de caja y bigotes, son los datos fuera de los limites.   
   
### Tratamiento:   
