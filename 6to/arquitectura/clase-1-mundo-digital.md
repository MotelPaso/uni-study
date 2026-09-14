# Clase 1: Mundo Digital   
Se puede convertir cualquier señal análoga a digital siguiendo una serie de pasos claves:   
### Paso 1: Revisar datos.   
Analógico significa electrico, es decir:   
Imagina la información que llega a tus ojos de la luz reflejada por un objeto, esta información es decodificada, convertida en una señal eléctrica.   
O un micrófono convirtiendo el sonido a una señal de voltaje.   
Estas señales se comportan como una onda en función al tiempo, que puede ser dividida en instantes para ser convertida a digital, en un proceso llamado:   
### Paso 2: Muestreo.   
El muestro es dividir una señal en distintos pulsos de tiempo, entre más pulsos se tomen, más precisa será la conversión.   
Existe una teorema de muestreo, donde una señal puede ser completamente recuperada solo si la frecuencia en la que se toman las muestras es mas del doble de la frecuencia de la señal original.   
### Paso 3: Cuantizacion:   
Restringe los valores de la señal a un rango finito de valores disponibles. Limita la señal a niveles definidos para reducir el ruido restante después del muestreo.   
### Paso 4: Conversion:   
El valor cuantificado de la señal se convierte a una secuencia de bits en grupos de n bits, donde $2^n$ es el numero de valores disponibles para la señal.   
Los eventos discretos siempre pueden ser traducidos en números enteros (int).   
 --- 
> Entonces, lo digital es la traducción del mundo análogo en términos de muestras cuantificadas.   

## Bits   
Son la forma de comunicación digital preferida, formada por el siguiente alfabeto:   

$$
\Sigma = \{0,1\}
$$
Se usan bits por su seguridad de transmisión, debido a que solo existen dos estados disponibles, activo (1) o no activo (0).   
Se pueden traducir rapidamente a señales electricas, como encendido y apagado.   
   
