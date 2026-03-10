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
  return top->getData();
}
```

# Cola (Queue)
### Implementación:
#### Queue.h

