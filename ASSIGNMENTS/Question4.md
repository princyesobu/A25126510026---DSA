#include <stdio.h>
#define SIZE 5

int q[SIZE];
int front = -1, rear = -1;

void insert()
{
    int x;

    if((rear + 1) % SIZE == front)
    {
        printf("Queue Overflow\n");
        return;
    }

    printf("Enter value: ");
    scanf("%d", &x);

    if(front == -1)
        front = 0;

    rear = (rear + 1) % SIZE;
    q[rear] = x;
}

void delete()
{
    if(front == -1)
    {
        printf("Queue Underflow\n");
        return;
    }

    printf("Deleted: %d\n", q[front]);

    if(front == rear)
        front = rear = -1;
    else
        front = (front + 1) % SIZE;
}

void display()
{
    int i;

    if(front == -1)
    {
        printf("Queue is empty\n");
        return;
    }

    i = front;

    printf("Queue: ");
    while(1)
    {
        printf("%d ", q[i]);

        if(i == rear)
            break;

        i = (i + 1) % SIZE;
    }

    printf("\n");
}

int main()
{
    int ch;

    do
    {
        printf("\n1.Insert 2.Delete 3.Display 4.Exit\n");
        scanf("%d", &ch);

        switch(ch)
        {
            case 1: insert(); break;
            case 2: delete(); break;
            case 3: display(); break;
            case 4: break;
            default: printf("Invalid choice\n");
        }
    } while(ch != 4);

    return 0;
}

<img width="420" height="562" alt="Image" src="https://github.com/user-attachments/assets/37f09d32-9b6e-415e-8f09-7b71f1b0ede2" />
