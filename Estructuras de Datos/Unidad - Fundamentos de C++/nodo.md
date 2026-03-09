# Nodo
Un `Nodo` es la base de las listas enlazadas, pilas y colas. 
Tiene dos atributos, sus datos y la dirección del siguiente `Nodo` en la lista. 

### Implementación:
```cpp

class Node{
private:
	int data;
	Node* next;
public:
	Node() : next(nullptr);
	void setData(int data) { this->data = data;}
	const int getData { return data; };
	void setNextNode(Node* next) { this->next = next };
	const Node* getNextNode { return next };
}

```
