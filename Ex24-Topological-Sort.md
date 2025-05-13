# Ex24: Topological Sort  
## DATE: 15.04.2025

## AIM:  
To compose the code to determine whether the topological ordering for the following graph is possible or not.

## Algorithm:

1. Represent the directed graph using an adjacency matrix or adjacency list.
2. Calculate the in-degree of each vertex.
3. Use a queue to process all vertices with in-degree 0.
4. For each dequeued vertex:
   - Add it to the topological order.
   - Decrease the in-degree of all its adjacent vertices.
   - If any vertex's in-degree becomes 0, enqueue it.
5. If all vertices are processed, topological ordering is possible.
   Else, the graph contains a cycle (not a DAG), so ordering is not possible.

## Program:

```c
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>
#include <stdlib.h>

#define MAX 10

int adj[MAX][MAX], indegree[MAX];
int queue[MAX], front = 0, rear = -1;
int n;

void findIndegree() {
    int i, j;
    for (i = 0; i < n; i++) {
        indegree[i] = 0;
        for (j = 0; j < n; j++) {
            if (adj[j][i] == 1) {
                indegree[i]++;
            }
        }
    }
}

void enqueue(int v) {
    queue[++rear] = v;
}

int dequeue() {
    return queue[front++];
}

int isQueueEmpty() {
    return front > rear;
}

void topologicalSort() {
    int i, j, count = 0;
    findIndegree();

    for (i = 0; i < n; i++) {
        if (indegree[i] == 0)
            enqueue(i);
    }

    printf("Topological Order: ");
    while (!isQueueEmpty()) {
        int current = dequeue();
        printf("%d ", current);
        count++;

        for (j = 0; j < n; j++) {
            if (adj[current][j] == 1) {
                indegree[j]--;
                if (indegree[j] == 0)
                    enqueue(j);
            }
        }
    }

    if (count != n) {
        printf("\nTopological ordering is not possible (Graph contains a cycle).\n");
    } else {
        printf("\nTopological ordering is possible.\n");
    }
}

int main() {
    int i, j, edges, start, end;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter number of edges: ");
    scanf("%d", &edges);

    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            adj[i][j] = 0;

    printf("Enter the edges (start end):\n");
    for (i = 0; i < edges; i++) {
        scanf("%d %d", &start, &end);
        adj[start][end] = 1;
    }

    topologicalSort();
    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/0fe5574c-21be-4d8f-b6f9-1df1fd170598)



## Result:
Thus, the C program for determining whether the topological ordering for the following graph is possible or not, is implemented successfully.
