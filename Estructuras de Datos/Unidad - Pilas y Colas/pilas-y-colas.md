---
Object type:
  - Unidad
Backlinks:
  - Estructuras de Datos
Creation date: 2026-03-04T03:29:28Z
Links:
  - Estructuras de Datos
  - motelpaso
---
Hay algunos problemas para los que no nos servirán directamente una lista enlazada y necesitaremos algo más focalizado para resolverlos.
# Pila (Stack)
### Definición:


### Implementación:

#### Stack.h
```cpp
#pragma once
#include "Node.h"

class Stack
{
  Node *top; 
public:
  Stack() : top(nullptr) {};
  ~Stack();
  void push(int data);
  int pop();
  const int *checkTop();
  bool isEmpty();
};
```

#### Stack.cpp

```cpp
#include "Stack.h"
#include "Node.h"
Stack::~Stack()
{
  while (top != nullptr)
  {
    Node *current = top->getNextNode();
    delete top;
    top = current;
  }
}
bool Stack::isEmpty()
{
  return top == nullptr;
}
void Stack::push(int data)
{
  Node *newNode = new Node();
  newNode->setData(data);
  newNode->setNextNode(top);
  top = newNode;
}

int Stack::pop()
{
  if (isEmpty())
  {
    return -1;
  }
  int data = *(top->getData());
  Node *prev = top;
  top = top->getNextNode();
  delete prev;
  return data;
}
const int *Stack::checkTop()
{
	if (top == nullptr){
		return nullptr;
	}
  return top->getData();
}
```

# Cola (Queue)
### Implementación:
#### Queue.h
```cpp
#include "Node.h"
class Queue {
	Node* first;
	Node* last;
public:
	Queue(): first(nullptr), last(nullptr) {};
	~Queue();
	void push(int data);
	int pop();
	const int* checkTop();
	bool isEmpty();
};
```

#### Queue.cpp
```cpp
#include "Queue.h"
#include "Node.h"
Queue::~Queue()
{
	while (!isEmpty()){
		Node* temp = last->getNextNode();
		delete last;
		last = temp;
	}
}
void Queue::push(int data) {
	Node* newNode = new Node();
	newNode->setData(data);
	if (isEmpty()) {
		first = newNode;
		last = newNode;
		return;
	}
	// else
	last->setNextNode(newNode);
	last = newNode;
	return;
}

int Queue::pop(){

	if (isEmpty()) return -1; 
	int data = *(first->getData());
	Node* temp = first;
	first = first->getNextNode();
	delete temp;
	return data;
}
const int* Queue::checkTop(){
	if (first == nullptr){
		return nullptr;
	}
	return first->getData();
}
bool Queue::isEmpty() {
return first == nullptr && last == nullptr;
}
```
