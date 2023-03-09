# Funciones en C++

Las funciones en C++ son bloques de código que realizan una tarea específica y pueden ser llamados desde cualquier parte del programa. Las funciones permiten dividir el código en partes más pequeñas y fáciles de mantener, mejorar la reutilización de código y facilitar la lectura y comprensión del mismo.

## Ejemplo de función en C++

Supongamos que queremos calcular el área de un rectángulo. Podríamos definir una función para realizar este cálculo de la siguiente manera:

```cpp
#include <iostream>
using namespace std;

// Definimos la función areaRectangulo
float areaRectangulo(float base, float altura) {
  float area = base * altura;
  return area;
}

int main() {
  // Pedimos al usuario la base y la altura del rectángulo
  float base, altura;
  cout << "Ingrese la base del rectángulo: ";
  cin >> base;
  cout << "Ingrese la altura del rectángulo: ";
  cin >> altura;

  // Calculamos y mostramos el área del rectángulo
  float area = areaRectangulo(base, altura);
  cout << "El área del rectángulo es: " << area << endl;

  return 0;
}
```

# Estructuras en C++

Las estructuras en C++ son una forma de definir un tipo de datos personalizado que agrupa distintos tipos de datos en una sola entidad. Las estructuras son similares a las clases en C++, pero no tienen métodos ni miembros privados.

## Ejemplo de estructura en C++

Supongamos que queremos almacenar la información de un alumno, como su nombre, edad y promedio. Podríamos definir una estructura de la siguiente manera:

```cpp
#include <iostream>
using namespace std;

struct Alumno {
  string nombre;
  int edad;
  float promedio;
};

int main() {
  // Creamos una instancia de la estructura Alumno
  Alumno alumno1;

  // Asignamos valores a sus miembros
  alumno1.nombre = "Juan";
  alumno1.edad = 18;
  alumno1.promedio = 8.5;

  // Mostramos los valores asignados
  cout << "Nombre: " << alumno1.nombre << endl;
  cout << "Edad: " << alumno1.edad << endl;
  cout << "Promedio: " << alumno1.promedio << endl;

  return 0;
}
```

# Punteros en C++

Los punteros en C++ son variables que contienen direcciones de memoria. Los punteros se utilizan para trabajar con datos en la memoria y para compartir datos entre funciones.

## Ejemplo de puntero en C++

Supongamos que queremos intercambiar los valores de dos variables `a` y `b`. Podríamos definir una función que intercambie los valores usando punteros de la siguiente manera:

```cpp
#include <iostream>
using namespace std;

// Definimos la función intercambiar
void intercambiar(int* ptrA, int* ptrB) {
  int temp = *ptrA;
  *ptrA = *ptrB;
  *ptrB = temp;
}

int main() {
  int a = 5, b = 10;

  // Mostramos los valores originales de a y b
  cout << "a = " << a << endl;
  cout << "b = " << b << endl;

  // Llamamos a la función intercambiar y pasamos los punteros a y b como argumentos
  intercambiar(&a, &b);

  // Mostramos los nuevos valores de a y b
  cout << "a = " << a << endl;
  cout << "b = " << b << endl;

  return 0;
}
```

# Pilas en C++

Una pila en C++ es una estructura de datos que sigue el principio LIFO (Last In, First Out), es decir, el último elemento que se inserta es el primero que se saca. Las pilas se pueden implementar en C++ utilizando arreglos o listas enlazadas.

## Ejemplo de pila en C++ con arreglos

Supongamos que queremos implementar una pila de enteros utilizando un arreglo en C++. Podríamos definir una clase `Pila` con los siguientes métodos:

```cpp
#include <iostream>
using namespace std;

const int MAX_SIZE = 100;

class Pila {
public:
  Pila(); // Constructor
  bool estaVacia();
  bool estaLlena();
  void push(int x);
  int pop();
private:
  int elementos[MAX_SIZE];
  int tope;
};

// Constructor
Pila::Pila() {
  tope = -1;
}

// Verifica si la pila está vacía
bool Pila::estaVacia() {
  return tope == -1;
}

// Verifica si la pila está llena
bool Pila::estaLlena() {
  return tope == MAX_SIZE - 1;
}

// Agrega un elemento a la pila
void Pila::push(int x) {
  if (estaLlena()) {
    cout << "Error: la pila está llena" << endl;
    return;
  }
  tope++;
  elementos[tope] = x;
}

// Elimina y devuelve el elemento del tope de la pila
int Pila::pop() {
  if (estaVacia()) {
    cout << "Error: la pila está vacía" << endl;
    return -1;
  }
  int elemento = elementos[tope];
  tope--;
  return elemento;
}

int main() {
  Pila p;

  // Agregamos elementos a la pila
  p.push(5);
  p.push(10);
  p.push(15);

  // Sacamos elementos de la pila y los mostramos por pantalla
  while (!p.estaVacia()) {
    int elemento = p.pop();
    cout << "Elemento sacado de la pila: " << elemento << endl;
  }

  return 0;
}
```

# Colas en C++

Una cola en C++ es una estructura de datos que sigue el principio FIFO (First In, First Out), es decir, el primer elemento que se inserta es el primero que se saca. Las colas se pueden implementar en C++ utilizando arreglos o listas enlazadas.

## Ejemplo de cola en C++ con listas enlazadas

Supongamos que queremos implementar una cola de enteros utilizando listas enlazadas en C++. Podríamos definir una clase `Cola` con los siguientes métodos:

```cpp
#include <iostream>
using namespace std;

class Nodo {
public:
  Nodo(int x);
  int valor;
  Nodo* siguiente;
};

Nodo::Nodo(int x) {
  valor = x;
  siguiente = nullptr;
}

class Cola {
public:
  Cola(); // Constructor
  bool estaVacia();
  void encolar(int x);
  int desencolar();
private:
  Nodo* primero;
  Nodo* ultimo;
};

// Constructor
Cola::Cola() {
  primero = nullptr;
  ultimo = nullptr;
}

// Verifica si la cola está vacía
bool Cola::estaVacia() {
  return primero == nullptr;
}

// Agrega un elemento a la cola
void Cola::encolar(int x) {
  Nodo* nuevoNodo = new Nodo(x);
  if (estaVacia()) {
    primero = nuevoNodo;
    ultimo = nuevoNodo;
  } else {
    ultimo->siguiente = nuevoNodo;
    ultimo = nuevoNodo;
  }
}

// Elimina y devuelve el primer elemento de la cola
int Cola::desencolar() {
  if (estaVacia()) {
    cout << "Error: la cola está vacía" << endl;
    return -1;
  }
  int elemento = primero->valor;
  Nodo* temp = primero;
  primero = primero->siguiente;
  if (primero == nullptr) {
    ultimo = nullptr;
  }
  delete temp;
  return elemento;
}

int main() {
  Cola c;

  // Agregamos elementos a la cola
  c.encolar(5);
  c.encolar(10);
  c.encolar(15);

  // Sacamos elementos de la cola y los mostramos por pantalla
  while (!c.estaVacia()) {
    int elemento = c.desencolar();
    cout << "Elemento sacado de la cola: " << elemento << endl;
  }

  return 0;
}
```

# Listas enlazadas en C++

Una lista enlazada es una estructura de datos en la que cada elemento está conectado a través de punteros a su siguiente elemento en la lista. Las listas enlazadas pueden ser simples o dobles, y se utilizan comúnmente en C++ para implementar estructuras de datos como pilas, colas y árboles.

## Ejemplo de lista enlazada simple en C++

Supongamos que queremos implementar una lista enlazada simple de enteros en C++. Podríamos definir una clase `Nodo` que representa cada nodo de la lista, y una clase `ListaEnlazada` que tiene punteros al primer y último nodo de la lista.

```cpp

#include <iostream>
using namespace std;

class Nodo {
public:
  Nodo(int x);
  int valor;
  Nodo* siguiente;
};

Nodo::Nodo(int x) {
  valor = x;
  siguiente = nullptr;
}

class ListaEnlazada {
public:
  ListaEnlazada(); // Constructor
  bool estaVacia();
  void insertarAlInicio(int x);
  void insertarAlFinal(int x);
  void eliminarAlInicio();
  void eliminarAlFinal();
  void imprimir();
private:
  Nodo* primero;
  Nodo* ultimo;
};

// Constructor
ListaEnlazada::ListaEnlazada() {
  primero = nullptr;
  ultimo = nullptr;
}

// Verifica si la lista está vacía
bool ListaEnlazada::estaVacia() {
  return primero == nullptr;
}

// Inserta un elemento al inicio de la lista
void ListaEnlazada::insertarAlInicio(int x) {
  Nodo* nuevoNodo = new Nodo(x);
  if (estaVacia()) {
    primero = nuevoNodo;
    ultimo = nuevoNodo;
  } else {
    nuevoNodo->siguiente = primero;
    primero = nuevoNodo;
  }
}

// Inserta un elemento al final de la lista
void ListaEnlazada::insertarAlFinal(int x) {
  Nodo* nuevoNodo = new Nodo(x);
  if (estaVacia()) {
    primero = nuevoNodo;
    ultimo = nuevoNodo;
  } else {
    ultimo->siguiente = nuevoNodo;
    ultimo = nuevoNodo;
  }
}

// Elimina el primer elemento de la lista
void ListaEnlazada::eliminarAlInicio() {
  if (estaVacia()) {
    cout << "Error: la lista está vacía" << endl;
  } else {
    Nodo* temp = primero;
    primero = primero->siguiente;
    delete temp;
  }
}

// Elimina el último elemento de la lista
void ListaEnlazada::eliminarAlFinal() {
  if (estaVacia()) {
    cout << "Error: la lista está vacía" << endl;
  } else if (primero == ultimo) {
    delete primero;
    primero = nullptr;
    ultimo = nullptr;
  } else {
    Nodo* temp = primero;
    while (temp->siguiente != ultimo) {
      temp = temp->siguiente;
    }
    delete ultimo;
    ultimo = temp;
    ultimo->siguiente = nullptr;
  }
}

// Imprime los elementos de la lista
void ListaEnlazada::imprimir() {
  Nodo* temp = primero;
  while (temp != nullptr) {
    cout << temp->valor << " ";
    temp = temp->siguiente;
  }
  cout << endl;
}

int main() {
  ListaEnlazada lista;
  lista.insertarAlFinal(5);
  lista.insertarAlInicio(3);
  lista.insertarAlFinal(7);
  lista.imprimir(); // Imprime: 3 5 7
  lista.eliminarAlInicio();
  lista.eliminarAlFinal();
  lista.imprimir(); // Imprime: 5
  return 0;
}

```
# Árboles en C++

Un árbol es una estructura de datos no lineal que se utiliza para almacenar y organizar datos jerárquicamente. En un árbol, cada elemento se llama nodo, y cada nodo puede tener uno o más nodos hijos que cuelgan de él. El nodo superior se llama la raíz del árbol, y los nodos sin hijos se llaman hojas.

```cpp
#include <iostream>
using namespace std;

class Nodo {
public:
  int valor;
  Nodo* izquierdo;
  Nodo* derecho;
  Nodo(int v);
};

Nodo::Nodo(int v) {
  valor = v;
  izquierdo = nullptr;
  derecho = nullptr;
}

class ArbolBinario {
public:
  ArbolBinario();
  void insertar(int v);
  bool buscar(int v);
  void imprimirInOrder();
private:
  Nodo* raiz;
  void insertar(int v, Nodo* nodo);
  bool buscar(int v, Nodo* nodo);
  void imprimirInOrder(Nodo* nodo);
};

ArbolBinario::ArbolBinario() {
  raiz = nullptr;
}

void ArbolBinario::insertar(int v) {
  if (raiz == nullptr) {
    raiz = new Nodo(v);
  } else {
    insertar(v, raiz);
  }
}

void ArbolBinario::insertar(int v, Nodo* nodo) {
  if (v < nodo->valor) {
    if (nodo->izquierdo == nullptr) {
      nodo->izquierdo = new Nodo(v);
    } else {
      insertar(v, nodo->izquierdo);
    }
  } else if (v > nodo->valor) {
    if (nodo->derecho == nullptr) {
      nodo->derecho = new Nodo(v);
    } else {
      insertar(v, nodo->derecho);
    }
  }
}

bool ArbolBinario::buscar(int v) {
  return buscar(v, raiz);
}

bool ArbolBinario::buscar(int v, Nodo* nodo) {
  if (nodo == nullptr) {
    return false;
  } else if (nodo->valor == v) {
    return true;
  } else if (v < nodo->valor) {
    return buscar(v, nodo->izquierdo);
  } else {
    return buscar(v, nodo->derecho);
  }
}

void ArbolBinario::imprimirInOrder() {
  imprimirInOrder(raiz);
  cout << endl;
}

void ArbolBinario::imprimirInOrder(Nodo* nodo) {
  if (nodo != nullptr) {
    imprimirInOrder(nodo->izquierdo);
    cout << nodo->valor << " ";
    imprimirInOrder(nodo->derecho);
  }
}

int main() {
  ArbolBinario arbol;
  arbol.insertar(5);
  arbol.insertar(3);
  arbol.insertar(7);
  arbol.insertar(2);
  arbol.insertar(4);
  arbol.insertar(6);
  arbol.insertar(8);
  arbol.imprimirInOrder(); // Imprime: 2 3 4 5 6 7 8
  cout << "7 está en el árbol


```
