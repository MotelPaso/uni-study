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

```cpp
class Node{
	int data;
	Node* next;
public:
    Node(int data){
    this.data = data;
    this.next = nullptr;
    }
}
```

#### Lista Enlazada
##### LinkedList.h
Aqui vamos a definir todos los metodos necesarios 

```cpp
#pragma once
#include "Node.h"
#include <string>
class LinkedList {
	Node *head;
public:
	LinkedList();
	LinkedList(int data);
	~LinkedList();
	void append(int data);
	void remove(int data);
	int getAtIndex(int index);
	std::string printList();
};
```

##### LinkedList.cpp

```cpp
void LinkedList::LinkedList{
  head = new Node(0);
}

void LinkedList::LinkedList(int data){
  head = new Node(data);
}

void LinkedList::~LinkedList{
  while (head) {
  
  }
}
```






