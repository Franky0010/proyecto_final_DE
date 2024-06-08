# proyecto_final_DE

*Árbol Binario de Búsqueda Autobalanceado (ABB)*
Este repositorio contiene la implementación de un Árbol Binario de Búsqueda (ABB) en C++, con la capacidad de autobalancearse para convertirse en un Árbol AVL. El programa permite la inserción de nodos, muestra el árbol en orden de nivel y verifica si el árbol es un AVL. Además, se puede convertir el árbol inicial en un AVL y generar una visualización del árbol utilizando el formato DOT.

*Contenido*
Compilación y Ejecución
Descripción de Funcionalidades
Estructura del Código
Ejemplos de Uso

*Requisitos*
Compilador C++ compatible con C++11 o superior.
Herramienta dot de Graphviz (opcional, para generar visualizaciones del árbol).

*Descripción de Funcionalidades*
Menú Principal
El programa presenta un menú principal con las siguientes opciones:

- Presentar ABB Autobalanceados
- Presentar Grafos (No implementado)
- Salir
- Menú de ABB Autobalanceados
Dentro del menú de ABB Autobalanceados, se tienen las siguientes opciones:

- Ingresar la lista de nodos y el recorrido para construir el árbol
- Mostrar de forma visual el árbol inicial (indica si el árbol es AVL o no)
- Convertir en AVL el árbol inicial y mostrar la visualización del árbol
- Convertir en árbol Rojo y Negro el árbol inicial y mostrar la visualización del árbol (No implementado)
- Volver al menú principal
  
*Funcionalidades Principales*
- Insertar Nodos: Permite ingresar nodos al árbol.
- Mostrar Nivel de Orden: Muestra el árbol en orden de nivel.
- Verificar AVL: Verifica si el árbol es un AVL.
- Convertir en AVL: Convierte el árbol en un AVL balanceado.
  
*Generar Archivo DOT*: Genera un archivo arbol.dot para visualización gráfica del árbol.
- Estructura del Código
- Estructura del Nodo
  
struct Nodo {
    int dato;
    int altura;
    Nodo* izquierdo;
    Nodo* derecho;

    Nodo(int valor) : dato(valor), altura(1), izquierdo(nullptr), derecho(nullptr) {}
};

*Clase ArbolBinario*

class ArbolBinario {
public:
    Nodo* raiz;
    ArbolBinario() : raiz(nullptr) {}

    void insertar(int valor);
    void mostrarNivelOrden();
    int altura(Nodo* nodo);
    bool esAVL(Nodo* nodo);
    void mostrarArbolConAVL();
    void recalcularAlturas(Nodo* nodo);
    void convertirEnAVL();

private:
    void insertarRecursivo(Nodo* nodo, int valor);
    void convertirEnAVLRecursivo(Nodo*& nodo);
    void rotacionIzquierda(Nodo*& nodo);
    void rotacionDerecha(Nodo*& nodo);
    void rotacionDobleIzquierda(Nodo*& nodo);
    void rotacionDobleDerecha(Nodo*& nodo);
};

*Funciones Auxiliares*

*Ingresar Nodos y Recorrido*: Permite ingresar una lista de nodos y muestra el árbol.

*Generar Archivo DOT*: Genera un archivo DOT para visualizar el árbol utilizando replit.
*Ejemplos de Uso*
Ingresar Nodos y Mostrar Árbol

![image](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/4f19ea2f-6ed3-49ce-a9ac-1acfcb1a1a80)
Árbol NO AVL

![image](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/3c4e0eec-e29c-4d4a-8fbf-619c95e77124)
Árbol AVL


