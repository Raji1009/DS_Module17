# Ex21: Representation of Graph  
## DATE: 07.04.25

## AIM:
To write a C program to display the adjacency matrix of the given graph by supplying the edges and the number of vertices.

## Algorithm:

1. Start the program and declare variables for vertices, edges, and the adjacency matrix.
2. Input the number of vertices and edges from the user.
3. Initialize the adjacency matrix with zeros.
4. Use a loop to input the edges and update the adjacency matrix accordingly.
5. Display the adjacency matrix.

## Program:
```
```c
/*
Program to display the adjacency matrix of the given graph
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>

int main() {
    int vertices, edges, i, j, start, end;

    printf("Enter the number of vertices: ");
    scanf("%d", &vertices);

    int adjMatrix[vertices][vertices];

    // Initialize the adjacency matrix with 0s
    for (i = 0; i < vertices; i++) {
        for (j = 0; j < vertices; j++) {
            adjMatrix[i][j] = 0;
        }
    }

    printf("Enter the number of edges: ");
    scanf("%d", &edges);

    printf("Enter the edges (start and end vertex pairs):\n");
    for (i = 0; i < edges; i++) {
        scanf("%d %d", &start, &end);
        adjMatrix[start][end] = 1;
        adjMatrix[end][start] = 1; // Omit this line if the graph is directed
    }

    // Print the adjacency matrix
    printf("\nAdjacency Matrix:\n");
    for (i = 0; i < vertices; i++) {
        for (j = 0; j < vertices; j++) {
            printf("%d ", adjMatrix[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/25f512a1-10a3-469f-b814-6615bef314a5)


## Result:
Thus, the C program to print the adjacency matrix of the given graph is implemented successfully.
