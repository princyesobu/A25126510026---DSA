#include <stdio.h>
#include <ctype.h>

char stack[100];
int top = -1;

void push(char x)
{
    stack[++top] = x;
}

char pop()
{
    return stack[top--];
}

int priority(char x)
{
    if(x == '^')
        return 3;
    if(x == '*' || x == '/')
        return 2;
    if(x == '+' || x == '-')
        return 1;
    return 0;
}

int main()
{
    char infix[100], postfix[100];
    int i, j = 0;
    char x;

    printf("Enter infix expression: ");
    scanf("%s", infix);

    for(i = 0; infix[i] != '\0'; i++)
    {
        x = infix[i];

        if(isalnum(x))
            postfix[j++] = x;

        else if(x == '(')
            push(x);

        else if(x == ')')
        {
            while(top != -1 && stack[top] != '(')
                postfix[j++] = pop();

            if(top != -1)
                pop();
        }

        else
        {
            while(top != -1 && stack[top] != '(' &&
                  (priority(stack[top]) > priority(x) ||
                  (priority(stack[top]) == priority(x) && x != '^')))
                postfix[j++] = pop();

            push(x);
        }
    }

    while(top != -1)
        postfix[j++] = pop();

    postfix[j] = '\0';

    printf("Postfix expression: %s\n", postfix);

    return 0;
}

<img width="326" height="70" alt="Image" src="https://github.com/user-attachments/assets/8fa9b36f-c684-476b-949e-3a63a7505b54" />
<img width="432" height="72" alt="Image" src="https://github.com/user-attachments/assets/e4e534ad-cbc9-499e-a22a-5ba966d2b6dc" />
