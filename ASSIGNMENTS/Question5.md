#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *next;
};

struct node *head = NULL;

void insertBegin(int x)
{
    struct node *newnode;
    newnode = (struct node*)malloc(sizeof(struct node));

    newnode->data = x;
    newnode->next = head;
    head = newnode;
}

void insertEnd(int x)
{
    struct node *newnode, *temp;

    newnode = (struct node*)malloc(sizeof(struct node));
    newnode->data = x;
    newnode->next = NULL;

    if(head == NULL)
        head = newnode;
    else
    {
        temp = head;
        while(temp->next != NULL)
            temp = temp->next;

        temp->next = newnode;
    }
}

void search(int x)
{
    struct node *temp = head;
    int pos = 1;

    while(temp != NULL)
    {
        if(temp->data == x)
        {
            printf("Found at position %d\n", pos);
            return;
        }

        temp = temp->next;
        pos++;
    }

    printf("Value not found\n");
}

void deleteValue(int x)
{
    struct node *temp = head, *prev = NULL;

    while(temp != NULL && temp->data != x)
    {
        prev = temp;
        temp = temp->next;
    }

    if(temp == NULL)
    {
        printf("Value not found\n");
        return;
    }

    if(prev == NULL)
        head = temp->next;
    else
        prev->next = temp->next;

    free(temp);
    printf("Deleted successfully\n");
}

void display()
{
    struct node *temp = head;

    printf("List: ");
    while(temp != NULL)
    {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main()
{
    int ch, x;

    do
    {
        printf("\n1.Insert Begin 2.Insert End");
        printf("\n3.Search 4.Delete 5.Display 6.Exit\n");
        scanf("%d", &ch);

        switch(ch)
        {
            case 1:
                scanf("%d", &x);
                insertBegin(x);
                break;

            case 2:
                scanf("%d", &x);
                insertEnd(x);
                break;

            case 3:
                scanf("%d", &x);
                search(x);
                break;

            case 4:
                scanf("%d", &x);
                deleteValue(x);
                break;

            case 5:
                display();
                break;
        }
    } while(ch != 6);

    return 0;
}
<img width="490" height="607" alt="Screenshot 2026-09-28 171931" src="https://github.com/user-attachments/assets/2a7fb727-a48c-4e87-8103-ebf693c8e26f" />
<img width="410" height="535" alt="Image" src="https://github.com/user-attachments/assets/25137552-5470-43ea-8103-ea134ef77a82" />
