# proyecto_final_DE

# Árbol Binario de Búsqueda Autobalanceado (ABB)

Este repositorio contiene la implementación de un Árbol Binario de Búsqueda (ABB) en C++, con la capacidad de autobalancearse para convertirse en un Árbol AVL. El programa permite la inserción de nodos, muestra el árbol en orden de nivel y verifica si el árbol es un AVL. Además, se puede convertir el árbol inicial en un AVL y generar una visualización del árbol utilizando el formato DOT.

## Contenido

- Compilación y Ejecución
- Descripción de Funcionalidades
- Estructura del Código
- Ejemplos de Uso

## Requisitos

- Compilador C++ compatible con C++11 o superior.
- Herramienta dot de Replit (opcional, para generar visualizaciones del árbol).

## Descripción de Funcionalidades

- Menú Principal

## El programa presenta un menú principal con las siguientes opciones:

- Presentar ABB Autobalanceados
- Presentar Grafos (No implementado)
- Salir
- Menú de ABB Autobalanceados

## Dentro del menú de ABB Autobalanceados, se tienen las siguientes opciones:

- Ingresar la lista de nodos y el recorrido para construir el árbol
- Mostrar de forma visual el árbol inicial (indica si el árbol es AVL o no)
- Convertir en AVL el árbol inicial y mostrar la visualización del árbol
- Convertir en árbol Rojo y Negro el árbol inicial y mostrar la visualización del árbol (No implementado)
- Volver al menú principal
  
## Funcionalidades Principales

- Insertar Nodos: Permite ingresar nodos al árbol.
- Mostrar Nivel de Orden: Muestra el árbol en orden de nivel.
- Verificar AVL: Verifica si el árbol es un AVL.
- Convertir en AVL: Convierte el árbol en un AVL balanceado.
  
## Generar Archivo DOT: 

## Genera un archivo *arbol.dot* para visualización gráfica del árbol.

- Estructura del Código
- Estructura del Nodo
  
`struct Nodo {
    int dato;
    int altura;
    Nodo* izquierdo;
    Nodo* derecho;
    Nodo(int valor) : dato(valor), altura(1), izquierdo(nullptr), derecho(nullptr) {} 
    };`

*Clase ArbolBinario*

`class ArbolBinario {
public:
    Nodo* raiz;
    ArbolBinario() : raiz(nullptr) {}
    void insertar(int valor);
    void mostrarNivelOrden();
    int altura(Nodo* nodo);
    bool esAVL(Nodo* nodo);
    void mostrarArbolConAVL();
    void recalcularAlturas(Nodo* nodo);
    void convertirEnAVL();`

`private:
    void insertarRecursivo(Nodo* nodo, int valor);
    void convertirEnAVLRecursivo(Nodo*& nodo);
    void rotacionIzquierda(Nodo*& nodo);
    void rotacionDerecha(Nodo*& nodo);
    void rotacionDobleIzquierda(Nodo*& nodo);
    void rotacionDobleDerecha(Nodo*& nodo);
};` 

## Funciones Auxiliares

## Ingresar Nodos y Recorrido:

Permite ingresar una lista de nodos y muestra el árbol.

## Generar Archivo DOT: 

Genera un archivo DOT para visualizar el árbol utilizando replit.

## Ejemplos de Uso

- Ingresar Nodos y Mostrar Árbol

## Convertir en AVL y Mostrar Árbol

- Copiar código
- Se ha generado el archivo 'arbol.dot'.
- Para visualizar el árbol, utilice el archivo arbol.dot con Replit:

![image](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/4f19ea2f-6ed3-49ce-a9ac-1acfcb1a1a80)

## Árbol NO AVL

![image](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/3c4e0eec-e29c-4d4a-8fbf-619c95e77124)

## Árbol AVL

# Grafos

# Proyecto de Grafos

Este proyecto contiene la implementación de varios algoritmos de grafos en C++, incluyendo la lectura de una matriz de adyacencias desde un archivo, visualización del grafo en formato DOT, y algoritmos para encontrar caminos más cortos y árboles de peso mínimo.

## Contenido

- [Requisitos](#requisitos)
- [Compilación y Ejecución](#compilacion-y-ejecucion)
- [Descripción de Funcionalidades](#descripcion-de-funcionalidades)
- [Estructura del Código](#estructura-del-codigo)
- [Ejemplos de Uso](#ejemplos-de-uso)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

## Requisitos

- Compilador C++ compatible con C++11 o superior.
- Herramienta `dot` de Replit para la visualización del grafo.

## Menú de Grafos

*Dentro del menú de Grafos, se tienen las siguientes opciones:*

- Grafo dirigido ponderado
- Grafo no dirigido ponderado
- Funcionalidades Principales
- Leer Matriz de Adyacencias: Lee la matriz de adyacencias desde un archivo llamado matriz.txt.
- Guardar Grafo en DOT: Guarda la representación del grafo en un archivo grafo.dot para visualización.
- Algoritmo de Dijkstra: Encuentra el camino más corto desde un vértice inicial utilizando el algoritmo de Dijkstra.
- Algoritmo de Floyd-Warshall: Encuentra los caminos más cortos entre todos los pares de vértices utilizando el algoritmo de Floyd- 
  Warshall.
- Algoritmo de Kruskal: Encuentra el árbol de peso mínimo utilizando el algoritmo de Kruskal.
- Algoritmo de Prim: Encuentra el árbol de peso mínimo utilizando el algoritmo de Prim.
- Estructura del Código
- Funciones Principales

## mostrarMenu()

`int mostrarMenu() {
    int opcion;
    cout << "Seleccione el tipo de grafo:" << endl;
    cout << "1. Grafo dirigido ponderado" << endl;
    cout << "2. Grafo no dirigido ponderado" << endl;
    cout << "Ingrese su opción: ";
    cin >> opcion;
    return opcion;
}`

## leerMatrizAdyacencias()

`void leerMatrizAdyacencias(vector<vector<int>>& matriz, bool dirigido) {
    ifstream file("matriz.txt");
    string line;
    vector<vector<int>> tempMatriz;
    while (getline(file, line)) {
        vector<int> row;
        istringstream iss(line);
        int value;
        while (iss >> value) {
            row.push_back(value);
        }
        tempMatriz.push_back(row);
    }
    file.close();
    int n = tempMatriz.size();
    matriz = vector<vector<int>>(n, vector<int>(n, 0));
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < n; ++j) {
            matriz[i][j] = tempMatriz[i][j];
            if (!dirigido && j > i) {
                matriz[j][i] = matriz[i][j];
            }
        }
    }
}`

## guardarGrafoEnDot()

`void guardarGrafoEnDot(const vector<vector<int>>& matriz, int n, bool dirigido) {
    ofstream file("grafo.dot");
    if (file.is_open()) {
        if (dirigido) {
            file << "digraph G {" << endl;
        } else {
            file << "graph G {" << endl;
        }
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matriz[i][j] != 0) {
                    if (dirigido) {
                        file << "  " << i << " -> " << j << " [label=\"" << matriz[i][j] << "\"];" << endl;
                    } else if (i <= j) {
                        file << "  " << i << " -- " << j << " [label=\"" << matriz[i][j] << "\"];" << endl;
                    }
                }
            }
        }
        file << "}" << endl;
        file.close();
        cout << "Grafo guardado en 'grafo.dot' para visualización." << endl;
    } else {
        cout << "No se pudo abrir el archivo para escritura." << endl;
    }
}`

## dijkstra()

`void dijkstra(const vector<vector<int>>& matriz, int n) {
    int inicio = 0; // Vértice inicial
    vector<int> dist(n, INT_MAX);
    vector<bool> visitado(n, false);
    dist[inicio] = 0;
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    pq.push({0, inicio});
    while (!pq.empty()) {
        int u = pq.top().second;
        pq.pop();
        if (visitado[u]) continue;
        visitado[u] = true;
        for (int v = 0; v < n; ++v) {
            if (matriz[u][v] != 0 && !visitado[v] && dist[u] + matriz[u][v] < dist[v]) {
                dist[v] = dist[u] + matriz[u][v];
                pq.push({dist[v], v});
            }
        }
    }
    cout << "Distancias desde el vértice " << inicio << ":" << endl;
    for (int i = 0; i < n; ++i) {
        cout << "Al vértice " << i << " : " << dist[i] << endl;
    }
}`

![image](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/0061ca68-65c6-4ed7-9a8a-3806fcae3af2)

## floydWarshall()

`void floydWarshall(const vector<vector<int>>& matriz, int n) {
    vector<vector<int>> dist = matriz;
    for (int k = 0; k < n; ++k) {
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (dist[i][k] != INT_MAX && dist[k][j] != INT_MAX && dist[i][k] + dist[k][j] < dist[i][j]) {
                    dist[i][j] = dist[i][k] + dist[k][j];
                }
            }
        }
    }
    cout << "Matriz de distancias más cortas:" << endl;
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < n; ++j) {
            if (dist[i][j] == INT_MAX) {
                cout << "INF ";
            } else {
                cout << dist[i][j] << " ";
            }
        }
        cout << endl;
    }
}`

![WhatsApp Image 2024-06-07 at 7 26 15 PM](https://github.com/Franky0010/proyecto_final_DE/assets/159094484/8484d0bc-ed7f-45a5-a413-9ddd15521e7d)

## kruskal()

`void kruskal(const vector<vector<int>>& matriz, int n) {
    vector<Arista> aristas;
    for (int i = 0; i < n; ++i) {
        for (int j = i + 1; j < n; ++j) {
            if (matriz[i][j] != 0) {
                aristas.push_back({i, j, matriz[i][j]});
            }
        }
    }
    sort(aristas.begin(), aristas.end());
    vector<int> padres(n);
    vector<int> rank(n, 0);
    for (int i = 0; i < n; ++i) {
        padres[i] = i;
    }
    vector<Arista> mst;
    for (const auto& arista : aristas) {
        int x = encontrar(padres, arista.origen);
        int y = encontrar(padres, arista.destino);
        if (x != y) {
            mst.push_back(arista);
            unir(padres, rank, x, y);
        }
    }
    cout << "Árbol de peso mínimo (Kruskal):" << endl;
    for (const auto& arista : mst) {
        cout << arista.origen << " -- " << arista.destino << " [peso=" << arista.peso << "]" << endl;
    }
}`

## prim()

`void prim(const vector<vector<int>>& matriz, int n) {
    vector<int> key(n, INT_MAX);
    vector<int> parent(n, -1);
    vector<bool> inMST(n, false);
    key[0] = 0;
    for (int count = 0; count < n - 1; ++count) {
        int u = -1;
        for (int i = 0; i < n; ++i) {
            if (!inMST[i] && (u == -1 || key[i] < key[u])) {
                u = i;
            }
        }
        inMST[u] = true;
        for (int v = 0; v < n; ++v) {
            if (matriz[u][v] && !inMST[v] && matriz[u][v] < key[v]) {
                parent[v] = u;
                key[v] = matriz[u][v];
            }
        }
    }
    cout << "Árbol de peso mínimo (Prim):" << endl;
    for (int i = 1; i < n; ++i) {
        if (parent[i] != -1) {
            cout << parent[i] << " -- " << i << " [peso=" << matriz[i][parent[i]] << "]" << endl;
        }
    }
}`

## Función Principal

`int main() {
    int opcion;
    do {
        std::cout << "Menu Principal:\n";
        std::cout << "1. Presentar ABB Autobalanceados\n";
        std::cout << "2. Presentar Grafos\n";
        std::cout << "3. Salir\n";
        std::cout << "Seleccione una opcion: ";
        std::cin >> opcion;
        switch (opcion) {
            case 1:
                presentarABB();
                break;
            case 2:
                presentarGrafos();
                break;
            case 3:
                std::cout << "Saliendo...\n";
                break;
            default:
                std::cout << "Opcion invalida. Intente de nuevo.\n";
        }
    } while (opcion != 3);
  return 0;
}`

## Ejemplos de Uso

- Seleccionar Grafo No Dirigido Ponderado
- Seleccione el tipo de grafo:

1. Grafo dirigido ponderado
2. Grafo no dirigido ponderado
 
## Visualización del Grafo

Después de leer la matriz de adyacencias, se guarda el grafo en un archivo grafo.dot que puede ser visualizado con Graphviz:

`dot -Tpng grafo.dot -o grafo.png`

## Ejecutar Algoritmo de Dijkstra

- Seleccione un algoritmo para encontrar el camino más corto:
1. Dijkstra
2. Floyd-Warshall

## Ejecutar Algoritmo de Kruskal

- Seleccione un algoritmo para encontrar el árbol de peso mínimo:
1. Kruskal
2. Prim
