# Ex22: Breadth First Graph  
## DATE: 12.04.2025

## AIM:
To write a `printQueue` C function for the given graph that is to be traversed in the **breadth-first manner (BFS)**.

## Algorithm:

1. Start the program and define the graph using an adjacency matrix.
2. Create a queue to help in BFS traversal and an array to track visited nodes.
3. Enqueue the starting vertex and mark it as visited.
4. Repeat the following until the queue is empty:
   - Dequeue a vertex from the front of the queue.
   - Print the vertex.
   - Enqueue all adjacent unvisited vertices and mark them as visited.
5. End the program.

## Program:

```c
/*
Program to traverse graph using BFS
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>
#define SIZE 10

int queue[SIZE], front = -1, rear = -1;
int visited[SIZE];

// Function to add elements to the queue
void enqueue(int vertex) {
    if (rear == SIZE - 1)
        return;
    if (front == -1)
        front = 0;
    queue[++rear] = vertex;
}

// Function to remove elements from the queue
int dequeue() {
    if (front == -1 || front > rear)
        return -1;
    return queue[front++];
}

// Function to perform BFS
void bfs(int adjMatrix[SIZE][SIZE], int vertices, int start) {
    int i;
    enqueue(start);
    visited[start] = 1;

    printf("BFS Traversal starting from vertex %d:\n", start);
    while (front <= rear) {
        int current = dequeue();
        printf("%d ", current);

        for (i = 0; i < vertices; i++) {
            if (adjMatrix[current][i] == 1 && !visited[i]) {
                enqueue(i);
                visited[i] = 1;
            }
        }
    }
}

int main() {
    int vertices, edges, i, j, start, end;

    printf("Enter the number of vertices: ");
    scanf("%d", &vertices);

    int adjMatrix[SIZE][SIZE] = {0};

    printf("Enter the number of edges: ");
    scanf("%d", &edges);

    printf("Enter the edges (start end):\n");
    for (i = 0; i < edges; i++) {
        scanf("%d %d", &start, &end);
        adjMatrix[start][end] = 1;
        adjMatrix[end][start] = 1; // Remove this line for directed graph
    }

    for (i = 0; i < vertices; i++) {
        visited[i] = 0;
    }

    printf("Enter the starting vertex for BFS: ");
    scanf("%d", &start);

    bfs(adjMatrix, vertices, start);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/b48c6322-9a4e-4b45-8b0e-cb972b1b0621)


## Result:
Thus, the code for the printQueue function of the following graph that is to be traversed in the breadth first manner is implemented successfully.
