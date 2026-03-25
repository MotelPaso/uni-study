### Funciones
Existen dos formas de pasarle argumentos a una función, por copia o por referencia.

```cpp
int sumar_copia(int num1, int num2) 
{
	num1 = 8;
	return num1 + num2;
}
// Esta función hace nuevas variables con los valores de num1 y num2,
// usando más memoria pero sin tocar las variables originales

int sumar_refer(int* num1, int* num2)
{
	*num1 = 8;
	return *num1 + *num2;
}
// Esta función agarra directamente las variables de sus espacios en la memoria.
// Funcionalmente, interpreta las variables como si fueran "globales"
```

> La función por referencia usa [[punteros-y-memoria|punteros]] para enviar los espacios de memoria de las variables.
#### Ejemplo de uso:
```cpp
#include <iostream>
using namespace std; // para hacer el print mas corto
// las funciones van aqui!

int main()
{
	int num1 = 1;
	int num2 = 4;
	
	cout << sumar_copia(num1, num2) << endl; // 12
	cout << num1 << " | " << num2 << endl; // 1 | 4
	
	cout << sumar_refer(&num1, &num2) << endl; // 12
	cout << num1 << " | " << num2 << endl; // 8 | 4	
	return 0;
}
```
