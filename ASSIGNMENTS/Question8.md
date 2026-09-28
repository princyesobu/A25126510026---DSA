#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *left, *right;
};

struct node* insert(struct node *root, int x)
{
    if(root == NULL)
    {
        root = (struct node*)malloc(sizeof(struct node));
        root->data = x;
        root->left = root->right = NULL;
        return root;
    }

    if(x < root->data)
        root->left = insert(root->left, x);
    else if(x > root->data)
        root->right = insert(root->right, x);

    return root;
}

struct node* minNode(struct node *root)
{
    while(root->left != NULL)
        root = root->left;

    return root;
}

struct node* deleteNode(struct node *root, int key)
{
    struct node *temp;

    if(root == NULL)
        return root;

    if(key < root->data)
        root->left = deleteNode(root->left, key);

    else if(key > root->data)
        root->right = deleteNode(root->right, key);

    else
    {
        if(root->left == NULL)
        {
            temp = root->right;
            free(root);
            return temp;
        }
        else if(root->right == NULL)
        {
            temp = root->left;
            free(root);
            return temp;
        }

        temp = minNode(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }

    return root;
}

void inorder(struct node *root)
{
    if(root != NULL)
    {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main()
{
    struct node *root = NULL;
    int n, x, key, i;

    printf("Enter number of nodes: ");
    scanf("%d", &n);

    printf("Enter values:\n");
    for(i = 0; i < n; i++)
    {
        scanf("%d", &x);
        root = insert(root, x);
    }

    printf("Before deletion: ");
    inorder(root);

    printf("\nEnter value to delete: ");
    scanf("%d", &key);

    root = deleteNode(root, key);

    printf("After deletion: ");
    inorder(root);

    return 0;
}
<img width="392" height="343" alt="Screenshot 2026-09-28 180451" src="https://github.com/user-attachments/assets/5d114b51-84cd-4cf7-b405-c5edc5a2e6a6" />
