#include <stdio.h>

int main()
{
    int a[20][20], visited[20] = {0};
    int q[20], front = 0, rear = -1;
    int n, start, i, j, v;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter adjacency matrix:\n");
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            scanf("%d", &a[i][j]);

    printf("Enter starting vertex (0 to %d): ", n - 1);
    scanf("%d", &start);

    visited[start] = 1;
    q[++rear] = start;

    printf("BFS Traversal: ");

    while(front <= rear)
    {
        v = q[front++];
        printf("%d ", v);

        for(i = 0; i < n; i++)
        {
            if(a[v][i] == 1 && visited[i] == 0)
            {
                visited[i] = 1;
                q[++rear] = i;
            }
        }
    }

    printf("\nUnvisited vertices: ");
    for(i = 0; i < n; i++)
    {
        if(visited[i] == 0)
            printf("%d ", i);
    }

    return 0;
}

<img width="371" height="260" alt="Image" src="https://github.com/user-attachments/assets/f739e906-287e-4a3c-a090-6992ad4fd10e" />
