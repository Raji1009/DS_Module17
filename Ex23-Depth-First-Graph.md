# Ex23: Depth First Graph  
## DATE: 13.04.2025  

## AIM:  
To compose the code for the function `createNode` to traverse the graph below in the **depth first fashion** (DFS).

## Algorithm:

1. Start the program and define the structure for a graph node using a linked list.
2. Create a function `createNode` to allocate memory for a new node and initialize it.
3. Create an adjacency list to represent the graph.
4. Write a DFS function that:
   - Marks the current node as visited.
   - Recursively visits all its unvisited adjacent nodes.
5. Call the DFS function from `main()` with the starting node and print the traversal.

## Program:

```c
/*
Program to traverse the graph below in the depth first fashion
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

struct Node {
    int vertex;
    struct Node* next;
};

struct Graph {
    int numVertices;
    struct Node** adjLists;
    int* visited;
};

// Function to create a new node
struct Node* createNode(int vertex) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->vertex = vertex;
    newNode->next = NULL;
    return newNode;
}

// DFS algorithm
void DFS(struct Graph* graph, int vertex) {
    struct Node* temp = graph->adjLists[vertex];
    graph->visited[vertex] = 1;

    printf("%d ", vertex);

    while (temp != NULL) {
        int adjVertex = temp->vertex;

        if (graph->visited[adjVertex] == 0) {
            DFS(graph, adjVertex);
        }
        temp = temp->next;
    }
}

// Create a graph
struct Graph* createGraph(int vertices) {
    int i;
    struct Graph* graph = (struct Graph*)malloc(sizeof(struct Graph));
    graph->numVertices = vertices;

    graph->adjLists = (struct Node**)malloc(vertices * sizeof(struct Node*));
    graph->visited = (int*)malloc(vertices * sizeof(int));

    for (i = 0; i < vertices; i++) {
        graph->adjLists[i] = NULL;
        graph->visited[i] = 0;
    }

    return graph;
}

// Add edge
void addEdge(struct Graph* graph, int src, int dest) {
    // Add edge from src to dest
    struct Node* newNode = createNode(dest);
    newNode->next = graph->adjLists[src];
    graph->adjLists[src] = newNode;

    // Add edge from dest to src (remove this for directed graph)
    newNode = createNode(src);
    newNode->next = graph->adjLists[dest];
    graph->adjLists[dest] = newNode;
}

int main() {
    int vertices = 5;

    struct Graph* graph = createGraph(vertices);

    addEdge(graph, 0, 1);
    addEdge(graph, 0, 2);
    addEdge(graph, 1, 3);
    addEdge(graph, 1, 4);

    printf("Depth First Traversal starting from vertex 0:\n");
    DFS(graph, 0);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/ad99ff1c-abbc-4297-b25c-a741b1a232f5)


## Result:
Thus, the C code for the function createNode to traverse the graph below in the depth first fashion is implemented successfully
