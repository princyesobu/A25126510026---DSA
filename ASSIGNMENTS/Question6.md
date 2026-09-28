#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct node
{
    char page[50];
    struct node *prev, *next;
};

struct node *head = NULL, *current = NULL;

void insertPage(char name[])
{
    struct node *newnode, *temp;

    newnode = (struct node*)malloc(sizeof(struct node));
    strcpy(newnode->page, name);
    newnode->next = NULL;
    newnode->prev = NULL;

    if(head == NULL)
        head = newnode;
    else
    {
        temp = head;
        while(temp->next != NULL)
            temp = temp->next;

        temp->next = newnode;
        newnode->prev = temp;
    }

    current = newnode;
}

void forward()
{
    if(current != NULL && current->next != NULL)
    {
        current = current->next;
        printf("Current page: %s\n", current->page);
    }
    else
        printf("No next page\n");
}

void backward()
{
    if(current != NULL && current->prev != NULL)
    {
        current = current->prev;
        printf("Current page: %s\n", current->page);
    }
    else
        printf("No previous page\n");
}

void deletePage(char name[])
{
    struct node *temp = head;

    while(temp != NULL && strcmp(temp->page, name) != 0)
        temp = temp->next;

    if(temp == NULL)
    {
        printf("Page not found\n");
        return;
    }

    if(temp->prev != NULL)
        temp->prev->next = temp->next;
    else
        head = temp->next;

    if(temp->next != NULL)
        temp->next->prev = temp->prev;

    if(current == temp)
        current = temp->next ? temp->next : temp->prev;

    free(temp);
    printf("Page deleted\n");
}

void displayForward()
{
    struct node *temp = head;

    printf("Forward: ");
    while(temp != NULL)
    {
        printf("%s ", temp->page);
        temp = temp->next;
    }
    printf("\n");
}

void displayBackward()
{
    struct node *temp = head;

    if(temp == NULL)
    {
        printf("No pages\n");
        return;
    }

    while(temp->next != NULL)
        temp = temp->next;

    printf("Backward: ");
    while(temp != NULL)
    {
        printf("%s ", temp->page);
        temp = temp->prev;
    }
    printf("\n");
}

int main()
{
    int ch;
    char name[50];

    do
    {
        printf("\n1.Insert 2.Forward 3.Backward");
        printf("\n4.Delete 5.Display Forward");
        printf("\n6.Display Backward 7.Exit\n");
        scanf("%d", &ch);

        switch(ch)
        {
            case 1:
                printf("Enter page: ");
                scanf("%49s", name);
                insertPage(name);
                break;

            case 2: forward(); break;
            case 3: backward(); break;

            case 4:
                printf("Enter page to delete: ");
                scanf("%49s", name);
                deletePage(name);
                break;

            case 5: displayForward(); break;
            case 6: displayBackward(); break;
        }
    } while(ch != 7);

    return 0;
}


<img width="375" height="481" alt="Image" src="https://github.com/user-attachments/assets/4de52c53-3292-454c-9888-55997415058e" />

<img width="361" height="467" alt="Image" src="https://github.com/user-attachments/assets/0f44fa4d-c092-47b2-8f9d-cbfd0dc00811" />
