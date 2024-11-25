#include<stdio.h>
#include<math.h>
#include<stdlib.h>

int main()
{
    char postfix[30], t[30];
    int stack[10], top = -1, len, i, j, op2, op1, n;
    
    printf("\n\n\nEnter the postfix expression: ");
    gets(postfix); 

    for(i = 0; postfix[i] != '\0'; i++)
    {
        j = 0;
        if(postfix[i] == ' ')
            continue;

        if(postfix[i] == '+' || postfix[i] == '-' || postfix[i] == '*' || postfix[i] == '/' || postfix[i] == '^' || postfix[i] == '%')
        {
            op2 = stack[top--];
            op1 = stack[top--];
            switch(postfix[i])
            {
                case '+': stack[++top] = op1 + op2;
                          break;
                case '-': stack[++top] = op1 - op2;
                          break;
                case '*': stack[++top] = op1 * op2;
                          break;
                case '/': stack[++top] = op1 / op2;
                          break;
                case '^': stack[++top] = pow(op1, op2);
                          break;
                case '%': stack[++top] = op1 % op2;
                          break;
            }
        }
        else
        {
            while(postfix[i] != ' ' && postfix[i] != '\0')
            {
                t[j++] = postfix[i++];
            }
            t[j] = '\0';

            n = atoi(t);
            stack[++top] = n;
        }
    }

    printf("\n\n\nResult = %d\n", stack[top]);
    return 0;
}
