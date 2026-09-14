<h1 align='center'>Ayudantía 8  - POO Invierno</h1>
<h5 align='center'>Profesor: Cristhian Rabi<br>  Ayudante: Paulo Araya</h5>
<h6 align='center'>10 de Agosto de 2026</h6>

Una empresa que vende cafe quiere expandir su negocio y necesita crear la logística principal de su sistema de envío, con los siguientes requerimientos:

La empresa puede ofrecer 3 tipos de envíos: terrestre, aéreo y marítimo, todos tienen una id, origen (km), destino (km), peso y precio.

El envío terrestre tiene la patente del vehículo de entrega, el envío aéreo tiene la marca de la aerolínea, además tiene un limite de peso de 50kg por envío, finalmente, el envío marítimo tiene el numero del contenedor y el puerto por donde sale. 

Se pueden calcular los costos de los envíos de 3 maneras: costo por peso, costo por distancia y costo express.
El costo por peso es la tarifa fija multiplicado por el peso total del envío.
El costo por distancia depende de la distancia a recorrer, con un precio mínimo fijo.
El costo express es igual al costo por peso, pero con una tarifa mucho mayor, en estos momentos, el costo express solo puede aplicarse al envío terrestre y aéreo.

El sistema debe mostrar un menu que permita crear un envío, cambiar el tipo de costo, ver un resumen de todos los envíos, y mostrar el envío con mayor peso.
Se le ha enviado un `envios.txt` para que pruebe su sistema.

### Restricciones
- Debe usar arquitectura app-sistema e implementar los patrones Factory, Singleton, Strategy y Visitor.
- No se puede usar `instanceof`.
- El tipo de envío se decide en base a la distancia que recorrerá (destino - origen) y en el peso vistos en la siguiente tabla:

| peso / distancia | d < 100km | d < 300km | d >= 300km |
| ---------------- | --------- | --------- | ---------- |
| p < 50kg         | terrestre | aéreo     | aéreo      |
| p >= 50kg        | terrestre | terrestre | marítimo   |
- Los datos específicos de cada envío se deben pedir al usuario.