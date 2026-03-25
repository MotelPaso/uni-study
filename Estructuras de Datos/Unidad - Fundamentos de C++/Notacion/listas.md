### Listas (Vectores)
Los datos de una lista nativa de C++, es decir `datatype lista[size]`, se guardan de forma continua en la memoria.
Al crear la lista, se reserva una cantidad de memoria para la lista, determinada por el tamaño de la lista y el tamaño de los datos.
> Una lista de int de tamaño 5 reservaría $4 \times 5 = 20$ bytes. 

```cpp
int main() 
{
	int lista[5];
	// o int lista[2] = {0,1};
	for (int i = 0; i < 5; i++)
	{
		std::cout << lista[i] << " | "; 
		// 0 | 0 | 0 | 0 | 0 |
	}
	std::cout << "\n"; 
}
```

##### Aritmética de Punteros
El código `lista[0]` se comporta implícitamente como un [puntero](punteros-y-memoria), apuntando al inicio de la lista.
Al hacer `lista[n]`, lo que esta haciendo el compilador es ir a `lista[0]` y sumarle n veces el tamaño del dato que estamos guardando.
```cpp title=Ejemplo

int lista[5] = {0,1,2,3,4}
// lista[0] -> 0x0001
// lista[4] -> 0x0001 + 4 * tamañoInt = 0x0001 + 16 = 0x0011
```
