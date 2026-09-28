# Clase 3: Limpieza de datos   

## CRISP-DM
### 3 - Data Preparation
Preparamos el conjunto final de datos, haciendo tareas como seleccion de tablas, registros y atributos.

## Faltan datos...

1. Reemplazo con media, mediana o moda
2. FFILL o BFILL (llenar con el anterior o con el siguiente)
3. Interpolacion (llenar basado en tendencias)
4. Borrar filas completas con datos faltantes
5. Dominio del tema (juicio propio basado en la experiencia)
6. Otros metodos como **machine learning** para predecir los valores faltantes.



## Transformación de Datos:   
Se busca una escala común para normalizar los parámetros que le pasamos un modelo de aprendizaje.   
### Normalización:   
Se lleva la columna a valores entre 0 y 1, guardando la escala de la variable:   

$$
X_{normalized} = \frac{X-X_{min}}{X_{max} - X_{min}}


$$
Esto se conoce como Min-Max Scaling, dato menor quedará con 0 y el mayor con 1.
### Estandarización:   
Utilizando la media y la desviación estándar, aplica la siguiente formula, es usualmente usada para datos normalmente distribuidos.   

$$
Z = \frac{X-\mu}{\sigma}
$$
### Escalado Robusto:   
Funciona igual a la estandarización, pero en su lugar utiliza la mediana y el rango intercuartilico.   

$$
X_{robust} = \frac{X-X_{median}}{IQR}

$$
### Tranformacion Logaritmica:   
Sirve para que los datos normalmente sesgados, se transformen en una variable mas simétrica.   
Se utiliza para variables como ingresos o población, o de tipo exponencial.   
#### Elección de Método:
Depende mucho de los datos que se quieran

 --- 
# Encoding:   
Podemos transformar datos categóricos o no-numericos en valores numéricos para ser usados en machine learning.   
### Label Encoding:   
Asignarle un numero único a cada categoría,   
```
variables = ["small", "medio", "grande"]
numero = [1, 2, 3]
```
Esto asume que las etiquetas tienen un orden intrínseco, pero podría pasar que:   
```
variables = ["perro", "gato", "zorro"]
numero = [1, 2, 3]
```
Que realmente no tienen orden, además podría ser que el numero de muestras per clase sea disparejo, llevando a modelos sesgados.   
### One Hot Encoding (Dummy Encoding):   
Reemplaza las categorías en vectores binarios, haciendo una columna por valor, pero permite información redundante.   

> Convierte los datos a expresiones booleanas, si es correcto, 1, si no, 0
### Mean, Frequency, Probability Encoding:   
Se pueden agrupar las variables categóricas con variables numéricas por su probabilidad, frecuencia o promedio.   

## Outliers   
Un outlier es un valor atipico en nuestra base de datos, que sale del promedio, de lo "normal" basado en los tipos de datos que tenemos, como un billonario.   
Hay muchos origenes de outliers, sean intencionales o errores.   
### Formas de detectar outliers:   
1. Aplicar estandarizacion, si el valor absoluto obtenido es mayor a 3, cuenta como outlier.   
2. Aplicando el rango intercuartilico, con los limites de $Q_1 - 1.5\cdot IQR$ o $Q_3 + 1.5\cdot  IQR$.
En un grafico de caja y bigotes, son los datos fuera de los limites.   
### Tratamiento:   
Para tratar con estos, se pueden:
- Eliminar
- Transformar
- Reemplazar
- Dejar como estan (no recomendado).