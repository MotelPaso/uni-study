---
Object type:
    - Unidad
Backlinks:
    - Estructuras de Datos
Creation date: "2026-01-23T21:42:55Z"
Links:
    - motelpaso
    - Estructuras de Datos
---
# Punteros y Memoria   
Un **puntero** es un nuevo datatype exclusivo\* a C y C++ que guardan la dirección de memoria de otra variable.   
> La dirección de memoria usualmente es un número hexadecimal que se ve así : 0xb73eb000   
> Siempre empiezan con `0x` y contienen `0-9` y `a-f`.

Sirven para trabajar con datos que puede que no estén al alcance de la función actual o para crear estructuras de datos complejas.   
Se crean de la siguiente manera:   
```cpp
int main()
{
	int num = 5;
	int* puntero = &num;
	return 0;
}
```
El símbolo `*` tiene dos significados dependiendo de si declara o no una variable.   
1. Indica que la variable a crear va a ser un puntero.   
    ```cpp
    int* puntero = &num; // 0x.......
    ```
2. Va a la dirección del puntero y toma el valor que este ahí.   
    ```cpp
    int copia_de_num = *puntero; // 5
    *puntero = 6;
    ```

El símbolo `&` nos devuelve la dirección de una variable.   
```cpp
	std::cout << &num << std::endl; // 0x.......
```

### Ejemplo grande:   
```cpp
#include <iostream>
int main() {
	int numero = 20;
	// std::cout << numero << std::endl;
	int* puntero_numero = &numero;
	std::cout << *puntero_numero << std::endl; // valor de numero
	std::cout << puntero_numero << std::endl; // direccion de numero
	std::cout << &puntero_numero << std::endl; // direccion del puntero
	/* Salida en consola
	 * 20
	 * 0x7ffcc452308c
	 * 0x7ffcc4523090
	 * Las direcciones estan en formato hexadecimal y no son siempre iguales, van variando.
	 */
	return 0;
}
```
   













