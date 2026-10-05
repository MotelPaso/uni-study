# Regresión Lineal

Su formula general es la de una recta, definida:

$$
\hat y = w_0 + w_1\cdot x_1 + \cdots + w_n\cdot x_n
$$

> $w_n$ también se denota como $\theta_n$, son lo mismo: los **parámetros** del modelo (los valores que aprende la regresión).
#### Mínimos Cuadrados

Para calcular el modelo, se utiliza como función de costo el error cuadrático medio, definido por la siguiente formula:
$$
ECM = J(\theta) = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2
$$
Donde $N$ es el número de ejemplos, $y_i$ es el valor real y $\hat{y}_i$ es la predicción para el ejemplo $i$.

Esto se puede redefinir usando la formula general de la regresión lineal mediante:
$$
ECM = \frac{1}{N} \sum_{i=1}^{N} (y_i - (w_0 + w_1\cdot x_{1,i} + \cdots + w_n\cdot x_{n,i}))^2
$$
#### Descenso del gradiente

Se trabaja mediante iteraciones, cada iteracion se acerca más al valor correcto.

La formula del descenso del gradiente es la siguiente:

$$
\theta := \theta - \alpha\nabla J(\theta)
$$
Donde $\alpha$ es el learning rate (**hiperparámetro**) y $\nabla J(\theta)$ es el gradiente de la función de costo.

La misma formula expandida para cada parámetro $\theta_j$ quedaría así:

$$
\theta_j := \theta_j - \alpha \cdot \frac{\partial J}{\partial \, \theta_j} = \theta_j - \alpha \cdot \frac{2}{N} \sum_{i=1}^{N} (\hat{y}_i - y_i)\cdot x_{j,i}
$$
Con $x_{0,i} = 1$ para el término independiente $\theta_0$.

### Resolución:

1. Definir la función de regresión principal, es decir, tu $\hat y = \cdots$
2. Definir tus **hiperparámetros**: el learning rate $\alpha$ y el criterio de parada (número máximo de iteraciones o tolerancia mínima del ECM).
3. Definir los valores iniciales de tus **parámetros**, es decir, tus $\theta$ (normalmente en $0$ o valores aleatorios pequeños).
#### Iteración
1. Calcular la predicción $\hat{y}_i$ con los parámetros actuales.
2. Calcular el error cuadrático medio con la predicción anterior (sirve para monitorear si el error baja).
3. Sacar la derivada parcial de la función de costo respecto a cada parámetro $\theta_j$.
4. Calcular los nuevos parámetros usando la formula del descenso de gradiente y tu learning rate $\alpha$.
5. Repetir hasta que el ECM deje de bajar o se alcance el número máximo de iteraciones.

### Regularización: Ridge y Lasso

Sirven para evitar el **sobreajuste** cuando el modelo tiene muchos pesos grandes. Se agrega un castigo a la función de costo para mantener los pesos pequeños. $\lambda$ es el **hiperparámetro** que controla cuánto castigas: si $\lambda = 0$ no hay regularización, si es muy grande el modelo se vuelve muy simple.

#### Ridge (L2)

$$
J_{Ridge} = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{n} w_j^2
$$

* Castiga el cuadrado de los pesos.
* **Encoge** los pesos hacia $0$, pero casi nunca los hace exactamente $0$.
* Útil cuando crees que todas las variables aportan algo y solo quieres controlarlas.
* No se suele regularizar $w_0$ (el sesgo).

#### Lasso (L1)

$$
J_{Lasso} = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{n} |w_j|
$$

* Castiga el valor absoluto de los pesos.
* Puede llevar pesos exactamente a $0$, o sea que hace **selección de variables** automática.
* Útil cuando sospechas que muchas variables son irrelevantes.

#### Para el examen: Ridge vs Lasso

| | Ridge (L2) | Lasso (L1) |
|---|---|---|
| Castigo | $\lambda \sum w_j^2$ | $\lambda \sum \|w_j\|$ |
| ¿Lleva pesos a $0$? | No, solo los encoge | Sí, elimina variables |
| ¿Cuándo usarlo? | Muchas variables útiles, multicolinealidad | Muchas variables inútiles, quieres modelo simple |
