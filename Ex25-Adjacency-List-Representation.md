# Ex25: Adjacency List Representation  
## DATE: 16.04.2025  

## AIM:  
To write a C program to represent the given graph using the adjacency list.

## Algorithm:

1. Define a `Node` structure to represent each vertex's adjacency list node.
2. Define a `Graph` structure that holds an array of adjacency lists.
3. Create a function `createNode` to allocate memory for a new node.
4. Create a function `createGraph` to initialize the graph with empty lists.
5. Create a function `addEdge` to insert edges into the graph.
6. Create a function `printGraph` to display the adjacency list.
7. In `main()`, read the number of vertices and edges, add edges, and print the graph.

## Program:

```c
/*
Program to represent the given graph using the adjacency list
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int vertex;
    struct Node* next;
};

struct Graph {
    int numVertices;
    struct Node** adjLists;
};

// Create a node
struct Node* createNode(int vertex) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->vertex = vertex;
    newNode->next = NULL;
    return newNode;
}

// Create a graph
struct Graph* createGraph(int vertices) {
    int i;
    struct Graph* graph = malloc(sizeof(struct Graph));
    graph->numVertices = vertices;
    graph->adjLists = malloc(vertices * sizeof(struct Node*));

    for (i = 0; i < vertices; i++) {
        graph->adjLists[i] = NULL;
    }

    return graph;
}

// Add edge (undirected)
void addEdge(struct Graph* graph, int src, int dest) {
    // Add edge from src to dest
    struct Node* newNode = createNode(dest);
    newNode->next = graph->adjLists[src];
    graph->adjLists[src] = newNode;

    // Add edge from dest to src (comment this line for directed graph)
    newNode = createNode(src);
    newNode->next = graph->adjLists[dest];
    graph->adjLists[dest] = newNode;
}

// Print the graph
void printGraph(struct Graph* graph) {
    int v;
    for (v = 0; v < graph->numVertices; v++) {
        struct Node* temp = graph->adjLists[v];
        printf("Vertex %d: ", v);
        while (temp) {
            printf("-> %d ", temp->vertex);
            temp = temp->next;
        }
        printf("\n");
    }
}

int main() {
    int vertices, edges, i, src, dest;

    printf("Enter number of vertices: ");
    scanf("%d", &vertices);

    struct Graph* graph = createGraph(vertices);

    printf("Enter number of edges: ");
    scanf("%d", &edges);

    printf("Enter the edges (src dest):\n");
    for (i = 0; i < edges; i++) {
        scanf("%d %d", &src, &dest);
        addEdge(graph, src, dest);
    }

    printf("\nAdjacency List Representation:\n");
    printGraph(graph);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/68419094-9b55-4b58-b448-0fb34080e315)



## Result:
Thus, the C program to represent the given graph using the adjacency list is implemented successfully
