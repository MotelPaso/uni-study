---
Object type:
  - Unidad
Backlinks:
  - Estructuras de Datos
Creation date: 2026-01-24T01:02:24Z
Links:
  - Estructuras de Datos
  - motelpaso
---
# Listas Enlazadas

### Definición:

Una **lista enlazada** es una estructura de datos lineal compuesta por **nodos**, donde cada nodo almacena un dato y un puntero al siguiente nodo de la lista.
A diferencia de un arreglo, los nodos **no** están juntos en memoria, cada uno puede estar en cualquier dirección, enlazándose mediante [[punteros-y-memoria|punteros]].
### Utilidad:

Son útiles cuando se necesitan inserciones y eliminaciones frecuentes, ya que no requieren reorganizar la memoria. Su desventaja es que el acceso a un elemento específico requiere recorrer la lista desde el inicio.
### Complejidad:

| Operación      | Tiempo | Notas                           |
| -------------- | ------ | ------------------------------- |
| `append()`     | O(n)   | Hay que recorrer hasta el final |
| `remove()`     | O(n)   | Hay que buscar el elemento      |
| `getAtIndex()` | O(n)   | Acceso secuencial, no directo   |
| `printList()`  | O(n)   | Recorre toda la lista           |
| Constructor    | O(1)   | Solo crea el nodo cabeza        |
| Destructor     | O(n)   | Borra todos los nodos           |
### Implementación:
#### Nodo:
Primero, se inicia creando una clase `{cpp} Node`, que tenga dos atributos, sus datos y la dirección (puntero) del proximo `{cpp} Node` en la lista.

```cpp
class Node{
	int data;
	Node* next;
public:
	Node() : next(nullptr){};
	void setData(int& data){
		this->data = data;
	}
	const int* getData(){
		return &data;
	}
	Node* getNextNode(){
	return next;
	}
	void setNextNode(Node* next){
		this->next = next;
	}
};
```

#### Lista Enlazada:
##### LinkedList.h
Definimos en el header los métodos de la clase a trabajar.

```cpp
#pragma once
#include "Node.h"
#include <string>
class LinkedList {
	Node *head;
public:
	LinkedList() : head(nullptr) {};
	LinkedList(int data);
	~LinkedList();
	void append(int data);
	void remove(int data);
	int getAtIndex(int index);
	std::string printList();
};
```

##### LinkedList.cpp
Esta es la implementación de todos los métodos de la lista. 
```cpp
#include "LinkedList.h"
#include "Node.h"
#include <string>

LinkedList::LinkedList(int data){
	head = new Node(); 
	head->setData(data);
	// creamos un nodo y lo añadimos como el primero de la lista
}
LinkedList::~LinkedList(){
	while (head != nullptr) // mientras que hayan nodos en la lista
	{
		Node *nextNode = head->getNextNode(); // mientras avanzamos
		delete head; // borramos
		head = nextNode;
	}
}
void LinkedList::append(int data){
	Node* newNode = new Node(); // creamos el nodo a agregar
	newNode->setData(data);
	if (head == nullptr) // si la lista esta vacia
	{ 
		head = newNode; // lo añadimos como el primero
		return;
	}
	Node* current = head; // si no, recorremos la lista
	while (current->getNextNode() != nullptr)
	{
		current = current -> getNextNode(); // hasta encontrar el ultimo
	}
	current->setNextNode(newNode); // y agregamos el nuevoNodo al final.
}
void LinkedList::remove(int data){
	Node* current = head; // creamos dos nodos auxiliares
	Node* prev = nullptr; // uno actual y uno anterior
	while (current != nullptr) // mientras queden nodos
	{
		if (*(current->getData()) == data) // si coincide el actual
		{
			if (prev != nullptr) // si no es el primero
			{
			// hacemos que el anterior apunte al siguiente
			// 0 -> 1 -> 2 pasa a  0 -> 2
				prev->setNextNode(current -> getNextNode());
			}	
			else // si el primero es el borrado
			{
				head = current->getNextNode(); 
				// ponemos el siguiente a la cabeza
			}
			delete current; // borramos el encontrado
			return;
		}
		prev = current; // pasamos el 0 al 1
		current = current->getNextNode(); // y el 1 al 2
	}	
}
int LinkedList::getAtIndex(const int index){
	Node* current = head; // creamos un nodo auxiliar
	int currentIndex = 0; // y un contador
	if (index < 0) return -1;
	
	while (current != nullptr){ // mientras hayan nodos en la lista
		if (currentIndex == index) // si lo encontramos
		{
			return *( current->getData() ); // devolvemos los datos
		}
		current = current->getNextNode();
		currentIndex++;
	}
	// devolvemos -1 si se han pasado de la lista
	return -1;
}
std::string LinkedList::printList(){
	Node* current = head;
	std::string text = "";
	while (current != nullptr)
	{ 
		text += std::to_string(*(current->getData()));
		if (current->getNextNode() != nullptr) {
			text += " -> ";
		}
		current = current->getNextNode();
	}
	if (text == "") return "Lista vacia...";
	text += " -> null";
	return text; // devuelve como 1 -> 2 -> 3 -> null
}
```
