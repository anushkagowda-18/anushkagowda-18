stack is static arrays
==========================================================

#include <stdio.h>
#include <stdlib.h>

#define MAX 4

int stack[MAX];
int top = -1; // Make 'top' a global variable

void push();
void pop();
void display();

int main() {
    int ch;
    
    while (1) {
        printf("\nMenu: \n1. Push\n2. Pop\n3. Display\n4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        
        switch (ch) {
            case 1: 
                push();
                break;
            case 2: 
                pop();
                break;
            case 3: 
                display();
                break;
            case 4: 
                exit(0);
                break;
            
        }
    }

    return 0;
}

void push() {
    int item;

    if (top >= MAX - 1) {
        printf("Stack is full (Overflow)\n");
    } else {
        printf("Enter the item to push: ");
        scanf("%d", &item);
        top++;
        stack[top] = item;
    }
}

void pop() {
    if (top == -1) {
        printf("Stack is empty (Underflow)\n");
    } else {
        printf("Item popped: %d\n", stack[top]);
        top--;
    }
}

void display() {
    if (top == -1) {
        printf("Stack is empty\n");
    } else {
        printf("Stack elements are:\n");
        for (int i = top; i >= 0; i--) {
            printf("%d\n", stack[i]);
        }
    }
}






stack using dynamic arrays
====================================================

#include<stdio.h>
#include<stdlib.h>
#define MAX 4
int *stack;
int top=-1;
void push();
void pop();
void display();
int item;
int main()
{
    stack=(int *)malloc(MAX*sizeof(int));
    int ch;
    while(1)
    {
    printf("menu is 1.push 2.pop 3.display 4.exit\n");
    printf("enter the choice");
    scanf("%d",&ch);
    switch(ch)
    {
     case 1:push();
     break;
     case 2: pop();
     break;
     case 3:display();
     break;
     case 4:exit(0);
     }
    }
}
void push()
{
    if(top>=MAX-1)
    printf("stack is full and overflow\n");
    else
    {
        printf("enter the item");
        scanf("%d",&item);
        top++;
        stack[top]=item;
    }
}
void pop()
{
    if(top==-1)
    printf("stack is empty and underflow\n");
    else
    {
        printf("the deleted item is %d\n",stack[top]);
        top--;
    }
}
void display()
{
    if(top<=-1)
    printf("stack is empty and overflow\n");
    else
    {
        printf("now the array eles are:\n");
        for(int i=top;i>=0;i--)
        printf("%d\n",stack[i]);
    }
}



stack using dynami array for palindrome
=================================================
#include<stdio.h>
#include<stdlib.h>
#define MAX 5
int *stack;
int top = -1;
char str[MAX], item;

void push();
int pop();
void string();
void palindrome();

int main() {
    stack = (int *)malloc(MAX * sizeof(int));
    int ch;
    while (1) {
        printf("Menu is 1.push 2.pop 3.display 4.exit\n");
        printf("Enter the choice: ");
        scanf("%d",&ch);

        switch (ch) {
            case 1:
                push();
                break;
            case 2:
                pop();
                break;
            case 3:
                string();
                palindrome();
                break;
            case 4:
                exit(0);
        }
    }

    return 0;
}

void push() {
    if (top >= MAX - 1)
        printf("Stack is full (overflow)\n");
    else {
        printf("Enter the item: ");
        scanf(" %c", &item);  
        top++;
        stack[top] = item;
    }
}

void string() {
    if (top == -1)
        printf("Stack is empty (underflow)\n");
    else {
        printf("Pushing elements into str:\n");
        for (int i = 0; i <= top; i++)
            str[i] = stack[i];
    }
}

int pop() {
    if (top == -1) {
        printf("Stack is empty (underflow)\n");
        return 0; 
    } else {
        return stack[top--];
    }
}

void palindrome() {
    int found = 0;  
    for (int i = 0; i <= top; i++) {
        if (pop() == str[i]) 
            found = 1;  
            break;
    }

    if (found)
        printf("The string is a palindrome\n");
    else
        printf("The string is not a palindrome\n");
}
