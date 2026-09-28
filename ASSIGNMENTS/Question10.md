#include <stdio.h>
#define INF 9999

int main()
{
    int a[10][10], dist[10], visited[10] = {0};
    int n, source, i, j, min, u;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter weighted adjacency matrix:\n");
    printf("Enter 0 if no edge exists.\n");

    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            scanf("%d", &a[i][j]);

            if(i != j && a[i][j] == 0)
                a[i][j] = INF;
        }
    }

    printf("Enter source vertex (0 to %d): ", n - 1);
    scanf("%d", &source);

    for(i = 0; i < n; i++)
        dist[i] = INF;

    dist[source] = 0;

    for(i = 0; i < n; i++)
    {
        min = INF;
        u = -1;

        for(j = 0; j < n; j++)
        {
            if(!visited[j] && dist[j] < min)
            {
                min = dist[j];
                u = j;
            }
        }

        if(u == -1)
            break;

        visited[u] = 1;

        for(j = 0; j < n; j++)
        {
            if(!visited[j] && a[u][j] != INF &&
               dist[u] + a[u][j] < dist[j])
            {
                dist[j] = dist[u] + a[u][j];
            }
        }
    }

    printf("\nShortest distances from vertex %d:\n", source);

    for(i = 0; i < n; i++)
    {
        if(dist[i] == INF)
            printf("To %d = Unreachable\n", i);
        else
            printf("To %d = %d\n", i, dist[i]);
    }

    return 0;
}

<img width="387" height="452" alt="Image" src="https://github.com/user-attachments/assets/2cef44aa-a5eb-4650-a816-4ecac7e6efd4" />
