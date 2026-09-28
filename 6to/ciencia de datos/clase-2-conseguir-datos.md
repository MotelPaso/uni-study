# Clase 2: Conseguir Datos   
## CRISP-DM   
Es un estándar que atraviesa industrias para la minería de datos.   
### 1. Business Understanding:   
Antes de empezar, se debe comprender los objetivos del proyecto, después podremos definir un problema y un plan para alcanzar estos objetivos.   
### 2. Data Understanding:   
Aquí empezamos a buscar, definir y formar hipótesis acerca de los datos encontrados.

### Encontrar datos:

## API
Una API (*application programming interface*) es una forma de comunicación entre el Cliente y un Servidor, es usada comúnmente mediante **HTTP queries**, existen varios métodos con distintos significados:   
- GET, consigue datos de forma *read-only*, no debería cambiar ningún estado dentro de la aplicación principal.   
- POST, envía datos al servidor, donde se cambia el estado, también puede recibirlos.  
- PUT, modifica datos del servidor.
- DELETE, borra algo dentro del servidor, aunque se podría también usar un POST.   
#### RESTful API
Lo importante de las API REST es que no tienen "memoria", cada llamada, cada query no afecta a las demas querys de forma directa. No guarda datos dentro de la API. 
La mayoria requiere autentificacion, como una API KEY.


Se comunican mediante JSON (diccionario) XML o CSV (comma separated values).   

> Los JSON funcionan principalmente para comunicaciones web que requieren JavaScript, XML para sistemas antiguos, y CSV es usualmente para aplicaciones tableadas, como Excel.   

## Expresiones regulares:   

| exp      | Significado                 |
| -------- | --------------------------- |
| \d       | Digitos                     |
| \w       | \[a-z A-z 0-9_\]            |
| \s       | eSpacios                    |
| .        | cualquier cosa              |
| [abc]    | cualquiera dentro de los [] |
| \[^asb\] | cualquier excepto []        |
| a?       | 0 o 1                       |
| a*       | 0 o n                       |
| a+       | 1 o n                       |
| a{n}     | n veces                     |

   
