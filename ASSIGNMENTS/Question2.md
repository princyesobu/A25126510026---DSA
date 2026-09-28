#include <stdio.h>

int main()
{
    int a[100], n, i, j, key;
    int shifts = 0;

    printf("Enter number of marks: ");
    scanf("%d", &n);

    printf("Enter marks:\n");
    for(i = 0; i < n; i++)
        scanf("%d", &a[i]);

    for(i = 1; i < n; i++)
    {
        key = a[i];
        j = i - 1;

        while(j >= 0 && a[j] > key)
        {
            a[j + 1] = a[j];
            j--;
            shifts++;
        }

        a[j + 1] = key;

        printf("Pass %d: ", i);
        for(int k = 0; k < n; k++)
            printf("%d ", a[k]);
        printf("\n");
    }

    printf("Sorted list: ");
    for(i = 0; i < n; i++)
        printf("%d ", a[i]);

    printf("\nTotal shifts = %d\n", shifts);

    return 0;
}


<img width="351" height="365" alt="Image" src="https://github.com/user-attachments/assets/2848ac1b-3ef5-4147-acf0-bcb2190c8c8c" />
