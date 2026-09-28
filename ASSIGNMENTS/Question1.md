#include <stdio.h>

int main()
{
    int a[100], n, key, i;
    int low, high, mid, count = 0, found = 0;

    printf("Enter number of employees: ");
    scanf("%d", &n);

    printf("Enter IDs in ascending order:\n");
    for(i = 0; i < n; i++)
        scanf("%d", &a[i]);

    printf("Enter ID to search: ");
    scanf("%d", &key);

    low = 0;
    high = n - 1;

    while(low <= high)
    {
        mid = (low + high) / 2;
        count++;

        if(a[mid] == key)
        {
            found = 1;
            break;
        }
        else if(key < a[mid])
            high = mid - 1;
        else
            low = mid + 1;
    }

    if(found)
        printf("ID found at position %d\n", mid + 1);
    else
        printf("ID not found\n");

    printf("Comparisons = %d\n", count);

    return 0;
}




<img width="346" height="287" alt="Image" src="https://github.com/user-attachments/assets/673dc355-a1b5-4731-a6fc-6b49d49afad6" />
