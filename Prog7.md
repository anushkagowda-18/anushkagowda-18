#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int ch, i;

void insertionfront();
void deletionfront();
void insertionend();
void deletionend();
void display();
void stack(); // Placeholder for stack-related operations

struct node {
    char name[10];
    char usn[10];
    char program[10];
    int sem;
    int phno;
    struct node *next;
} *ptr, *header, *ptr1, *ptr2, *new;

int main() {
    header = NULL;
    while (1) {
        printf("\nMenu driven program:\n1. Insertion at front\n2. Display\n3. Insertion at end\n4. Deletion from end\n5. Deletion from front\n6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                insertionfront();
                break;
            case 2:
                display();
                break;
            case 3:
                insertionend();
                break;
            case 4:
                deletionend();
                break;
            case 5:
                deletionfront();
                break;
            case 6:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}

void insertionfront() {
    new = malloc(sizeof(struct node));
    printf("Enter USN: ");
    scanf("%s", new->usn);
    printf("Enter Name: ");
    scanf("%s", new->name);
    printf("Enter Program: ");
    scanf("%s", new->program);
    printf("Enter Semester: ");
    scanf("%d", &new->sem);
    printf("Enter Phone Number: ");
    scanf("%d", &new->phno);
   
    new->next = header;
    header = new;
    printf("Node inserted at the front.\n");
}

void insertionend() {
    new = malloc(sizeof(struct node));
    printf("Enter USN: ");
    scanf("%s", new->usn);
    printf("Enter Name: ");
    scanf("%s", new->name);
    printf("Enter Program: ");
    scanf("%s", new->program);
    printf("Enter Semester: ");
    scanf("%d", &new->sem);
    printf("Enter Phone Number: ");
    scanf("%d", &new->phno);
   
    new->next = NULL;
    if (header == NULL) {
        header = new;
    } else {
        ptr = header;
        while (ptr->next != NULL) {
            ptr = ptr->next;
        }
        ptr->next = new;
    }
    printf("Node inserted at the end.\n");
}

void deletionfront() {
    if (header == NULL) {
        printf("List is empty, nothing to delete.\n");
    } else {
        ptr = header;
        header = header->next;
        free(ptr);
        printf("Node deleted from the front.\n");
    }
}

void deletionend() {
    if (header == NULL) {
        printf("List is empty, nothing to delete.\n");
    } else if (header->next == NULL) { // Only one node in the list
        free(header);
        header = NULL;
        printf("Node deleted from the end.\n");
    } else {
        ptr = header;
        while (ptr->next->next != NULL) {
            ptr = ptr->next;
        }
        free(ptr->next);
        ptr->next = NULL;
        printf("Node deleted from the end.\n");
    }
}

void display() {
    int count = 0;
    ptr = header;
    if (header == NULL) {
        printf("List is empty\n");
        printf("Count is %d\n", count);
    } else {
        printf("List is:\n");
        while (ptr != NULL) {
            printf("%s  %s  %s  %d  %d\n", ptr->usn, ptr->name, ptr->program, ptr->sem, ptr->phno);
            ptr = ptr->next;
            count++;
        }
        printf("Count is %d\n", count);
    }
}

void stack() {
    // Placeholder function for stack-related operations
    printf("Stack operations are not implemented.\n");
}
