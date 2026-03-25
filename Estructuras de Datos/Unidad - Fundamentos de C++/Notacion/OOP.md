### Programacion Orientada a Objetos

Una buena practica de C++ es separar la declaración de los métodos de una clase con su implementación. Para esto se utilizan archivos header .h y implementaciones .cpp.

```cpp title=profesiones.h
#include <string>
#include <queue>
class Persona // clase abstracta 
{ 
protected:
	std::string nombre;
public:
	virtual float calcularSueldo() = 0;
};

class Chef : public Persona // herencia
{
private:
	float sueldoBase;
	std::queue<std::string> ordenes;
public:
	Chef(std::string nombre);          // constructor
	~Chef() {};                        // destructor
	// metodos de chef
	void agregarOrden(std::string platillo);
	void cocinar();
	float calcularSueldo();
};
```

```cpp title=profesiones.cpp
#include "profesionales.h"
Chef::Chef(std::string nombre) 
{
	this->nombre = nombre;
	this->sueldoBase = 6000;
}
void Chef::agregarOrden(std::string platillo) 
{
	ordenes.push(platillo);
}
void Chef::cocinar() 
{
	if (!ordenes.empty())
	{
		std::string next = ordenes.front();
		// logica de cocinar 
		ordenes.pop();
	}
}

```
#### Ejemplo de uso:

```cpp
#include "profesionales.h"
#include <string>
#include <iostream>
int main() 
{
	// Persona p; ERROR, clase abstracta
	Persona* manolo = new Chef("Manolo");
	manolo->agregarOrden("Pizza");
	manolo->agregarOrden("Limonada");
	manolo->cocinar();
	delete manolo;
	return 0;
}
```