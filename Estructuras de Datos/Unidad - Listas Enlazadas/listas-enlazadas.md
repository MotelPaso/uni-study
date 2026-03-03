---
Object type:
    - Unidad
Backlinks:
    - Estructuras de Datos
Creation date: "2026-01-24T01:02:24Z"
Links:
    - Estructuras de Datos
    - motelpaso
---
# Listas Enlazadas
### Implementación:
#### Nodo:
Primero, se inicia creando una clase `{cpp} Node`, que tenga dos atributos, sus datos y la dirección (puntero) del proximo `{cpp} Node` en la lista.

```cpp
class Node{
	int data;
	Node* next;
}
```


```cpp
#include "Node.h"
class LinkedList {
	Node *head;
public:
	LinkedList();
	~LinkedList();
	void append(int data);
	&int getAtIndex(int index);
	void remove(int data);
	string showList();
}
```








