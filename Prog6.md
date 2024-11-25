#include <stdio.h>

#include<stdlib.h>

#define MAX 5

int cq[MAX],ch,item,i,f=-1,r=-1;

void enqueue();

void dequeue();

void display();



int main()

{

    while(1)

    {

        printf("\nMenu is 1. enqueue 2. dequeue 3.display 4.exit");

        printf("\nenter the choice");

        scanf("%d",&ch);

        switch(ch)

        {

            case 1:enqueue();

            break;

            case 2: dequeue();

            break;

            case 3:display();

            break;

            case 4:exit(0);

        }



    }

    return 0;

}

void enqueue()

{

    if((f==0&&r==MAX-1)||(f==r+1))

    printf("\ncq is full");

    else

    {

        if(f==-1)

        f=0;

        if(r==MAX-1)

        r=0;

        else

        r=r+1;

        printf("\nenter the value for an item");

        scanf("%d",&item);

        cq[r]=item;

    }

}

void dequeue()

{

    if(f==-1)

    printf("\ncq is empty");

    else

    {

        printf("\nthe deleted ele is:%d",cq[f]);

        if(f==r)

        f=r=-1;

        if(f==MAX-1)

        f=0;

        else

        f=f+1;

    }

}

void display()

{

    int fpos=f,rpos=r;

    if(f==-1)

    printf("\nthe cq is empty");

    else

    {

        printf("\nnow the array eles are:");

        if(fpos<=rpos)

        {

            while(fpos<=rpos)

            {

                printf("%d ",cq[fpos]);

                fpos++;

            }

        }

        else

        {

            while(fpos<=MAX-1)

            {

                printf("%d ",cq[fpos]);

                fpos++;

            }

            fpos=0;

            while(fpos<=rpos)

            {

                printf("%d ",cq[fpos]);

                fpos++;

            }

        }

    }
