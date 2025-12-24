# DS-Assignment-1
DATA STRUCTURE ASSIGNMENT-5TH SEM
NAME: YASIR AMIN DAR
ROLL NO : BS DYOD 18



#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* ===============================
   DOUBLE LINKED LIST STRUCTURE
================================ */
struct Node {
    int data;
    struct Node *prev;
    struct Node *next;
};

struct Node *head = NULL;

/* ===============================
   INSERT NODE AT END
================================ */
void insert(int value) {
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;
    newNode->prev = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    struct Node *temp = head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    newNode->prev = temp;
}

/* ===============================
   DISPLAY LIST
================================ */
void display() {
    struct Node *temp = head;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

/* =====================================================
   Q1: DISPLAY ONLY EVEN NUMBERS IN LINKED LIST
===================================================== */
void displayEven() {
    struct Node *temp = head;
    while (temp != NULL) {
        if (temp->data % 2 == 0)
            printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

/* =====================================================
   Q2: DISPLAY ONLY PRIME NUMBERS
===================================================== */
int isPrime(int n) {
    if (n <= 1) return 0;
    for (int i = 2; i <= n / 2; i++)
        if (n % i == 0)
            return 0;
    return 1;
}

void displayPrime() {
    struct Node *temp = head;
    while (temp != NULL) {
        if (isPrime(temp->data))
            printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

/* =====================================================
   Q3: FIND SUM OF ALL ELEMENTS
===================================================== */
int sumList() {
    int sum = 0;
    struct Node *temp = head;
    while (temp != NULL) {
        sum += temp->data;
        temp = temp->next;
    }
    return sum;
}

/* =====================================================
   Q4: FIND SUM AND AVERAGE
===================================================== */
void sumAndAverage() {
    int sum = 0, count = 0;
    struct Node *temp = head;
    while (temp != NULL) {
        sum += temp->data;
        count++;
        temp = temp->next;
    }
    printf("Sum = %d\n", sum);
    printf("Average = %.2f\n", (float)sum / count);
}

/* =====================================================
   Q5: FIND MIN AND MAX
===================================================== */
void minMax() {
    int min, max;
    struct Node *temp = head;

    min = max = temp->data;

    while (temp != NULL) {
        if (temp->data < min) min = temp->data;
        if (temp->data > max) max = temp->data;
        temp = temp->next;
    }

    printf("Min = %d\n", min);
    printf("Max = %d\n", max);
}

/* =====================================================
   Q6: STUDENT DATABASE USING DOUBLE LINKED LIST
===================================================== */
struct Student {
    char name[50];
    int roll;
    float marks;
    struct Student *prev;
    struct Student *next;
};

struct Student *shead = NULL;

void insertStudent(char name[], int roll, float marks) {
    struct Student *newNode = (struct Student *)malloc(sizeof(struct Student));
    strcpy(newNode->name, name);
    newNode->roll = roll;
    newNode->marks = marks;
    newNode->next = NULL;
    newNode->prev = NULL;

    if (shead == NULL) {
        shead = newNode;
        return;
    }

    struct Student *temp = shead;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    newNode->prev = temp;
}

void displayPassingStudents() {
    struct Student *temp = shead;
    while (temp != NULL) {
        if (temp->marks > 40) {
            printf("Name: %s | Roll: %d | Marks: %.2f\n",
                   temp->name, temp->roll, temp->marks);
        }
        temp = temp->next;
    }
}

