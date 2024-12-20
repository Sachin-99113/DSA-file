# DSA-file
Experiment No.: 1

Program Description:

Implementation of Linked List using array.

Solution:

#include <stdio.h>

#include <stdlib.h>

// Define the structure for a Node

struct Node {

    int data;

    struct Node* next;

};

// Function to create a new node

struct Node* newNode(int data) {

    struct Node* node = (struct Node*)malloc(sizeof(struct Node));

    node->data = data;

    node->next = NULL;

    return node;

}

// Function to insert a new node at the end of the list

void insertNewNode(struct Node** root, int data) {

    struct Node* node = newNode(data);

    struct Node* ptr;

    if (*root == NULL) {

        *root = node;

    } else {

        ptr = *root;

        while (ptr->next != NULL) {

            ptr = ptr->next;

        }

        ptr->next = node;

    }

}

// Function to print the linked list

void printLinkedList(struct Node* root) {

    while (root != NULL) {

        printf("%d -> ", root->data);

        root = root->next;

    }

    printf("NULL\n");

}

 

// Function to create a linked list from an array

struct Node* createLinkedList(int arr[], int n) {

    struct Node* root = NULL;

    for (int i = 0; i < n; i++) {

        insertNewNode (&root, arr[i]);

    }

    return root;

}

 

// Main function

int main() {

    int arr[] = {10, 20, 30, 40, 50};

    int n = 5;

    struct Node* root = createLinkedList(arr, n);

    printLinkedList(root);

    return 0;

}

 

Output:

1.Insert at head

2.Insert at end.

3.Insert at position.

4.Delete at head.

5.Delete at end.

6.Display

7.Exit

Enter your choice:

 

 

 

 
Experiment No.: 2

Program Description:

Implementation of Linked List using Pointers.
Solution:

#include <stdio.h>

#include <stdlib.h>

 

// Define the Node structure

struct Node {

  int data;

  struct Node *next;

};

 

// Global head pointer for the linked list

struct Node* head = NULL;

 

// Function to insert a new node at the beginning of the list

void insert(int new_data) {

  struct Node* new_node = (struct Node*) malloc(sizeof(struct Node));

  new_node->data = new_data;

  new_node->next = head;

  head = new_node;

}

 

// Function to display the linked list

void display() {

  struct Node* ptr = head;

  while (ptr != NULL) {

     printf("%d ", ptr->data);

     ptr = ptr->next;

  }

}

 

int main() {

  // Insert some data into the linked list

  insert(3);

  insert(1);

  insert(7);

  insert(2);

  insert(9);

 

  // Display the linked list

  printf("The linked list is: ");

  display();

 

  return 0;

}

 

Output:

The linked list is: 9 2 7 1 3

 

 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 

Experiment No.: 3

Program Description:

Implementation of Doubly Linked List using Pointers.
Solution:

#include <stdio.h>

#include <stdlib.h>

// Define the Node structure for a doubly linked list

struct Node {

   int data;

   struct Node* prev;

   struct Node* next;

};

// Define the DoublyLinkedList structure

struct DoublyLinkedList {

   struct Node* head;

   struct Node* tail;

};

// Function to initialize a new doubly linked list

void initList(struct DoublyLinkedList* list) {

   list->head = NULL;

   list->tail = NULL;

}

// Function to insert a node at the head of the list

void insertAtHead(struct DoublyLinkedList* list, int value) {

   struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

   newNode->data = value;

   newNode->prev = NULL;

   newNode->next = list->head;

 

  if (list->head != NULL) {

       list->head->prev = newNode;

   }

list->head = newNode;

  if (list->tail == NULL) {

       list->tail = newNode;

   }

}

// Function to insert a node at the tail of the list

void insertAtTail(struct DoublyLinkedList* list, int value) {

   struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

   newNode->data = value;

   newNode->next = NULL;

   newNode->prev = list->tail;

 

   if (list->tail != NULL) {

       list->tail->next = newNode;

   }

   list->tail = newNode;

   if (list->head == NULL) {

       list->head = newNode;

   }

}

// Function to delete a node from the head of the list

void deleteFromHead(struct DoublyLinkedList* list) {

   if (list->head == NULL) {

       printf("The list is already empty.\n");

       return;

   }

  struct Node* temp = list->head;

   list->head = list->head->next;

  if (list->head != NULL) {

       list->head->prev = NULL;

   }

  free(temp);

  // If the list becomes empty after deletion, update the tail

   if (list->head == NULL) {

       list->tail = NULL;

   }

}

// Function to delete a node from the tail of the list

void deleteFromTail(struct DoublyLinkedList* list) {

   if (list->tail == NULL) {

       printf("The list is already empty.\n");

       return;

   }

  struct Node* temp = list->tail;

   list->tail = list->tail->prev;

 

   if (list->tail != NULL) {

       list->tail->next = NULL;

   }

  free(temp);

  // If the list becomes empty after deletion, update the head

   if (list->tail == NULL) {

       list->head = NULL;

   }

}

// Function to print the entire doubly linked list

void printList(struct DoublyLinkedList* list) {

   struct Node* temp = list->head;

   while (temp != NULL) {

       printf("%d ", temp->data);

       temp = temp->next;

   }

   printf("\n");

}

int main() {

   struct DoublyLinkedList list;

   initList(&list);

   // Insert elements at the head and tail of the list

   insertAtHead(&list, 5);

   insertAtHead(&list, 10);

   insertAtTail(&list, 15);

   insertAtTail(&list, 20);

  printf("List: ");

   printList(&list);

// Delete elements from the head and tail of the list

   deleteFromHead(&list);

   deleteFromTail(&list);

   printf("List after deletions: ");

   printList(&list);

   return 0;

}

 

Output:

List: 10 5 15 20

List after deletions: 5 15

 

 

 
 
 
 

Experiment No.: 4

Program Description:

Implementation of Circular Single Linked List using Pointers.
Solution:

#include <stdio.h>

#include <stdlib.h>

typedef struct Node {

   int data;

   struct Node* next;

} Node;

Node* head = NULL;

void insertNode(int data) {

   Node* newNode = (Node*)malloc(sizeof(Node));

   newNode->data = data;

   newNode->next = NULL;

 

   if (head == NULL) {

       head = newNode;

       newNode->next = head;

   } else {

       Node* temp = head;

       while (temp->next != head) {

           temp = temp->next;

       }

       temp->next = newNode;

       newNode->next = head;

   }

}

void deleteNode(int data) {

   if (head == NULL) {

       return;

   }

 

   Node* temp = head;

   Node* prev = NULL;

  // If head node holds the data to be deleted

   if (temp->data == data) {

       if (temp->next == head) { // Only one node in the list

           free(temp);

           head = NULL;

       } else {

           while (temp->next != head) {

               temp = temp->next;

           }

           temp->next = head->next;

           free(head);

           head = temp->next;

       }

       return;

   }

   // Search for the node to be deleted

   prev = head;

   temp = head->next;

   while (temp != head) {

       if (temp->data == data) {

           prev->next = temp->next;

           free(temp);

           return;

       }

       prev = temp;

       temp = temp->next;

   }

}

void printList() {

   if (head == NULL) {

       return;

   }

   Node* temp = head;

   do {

       printf("%d ", temp->data);

       temp = temp->next;

   } while (temp != head);

   printf("\n");

}

void freeList() {

   if (head != NULL) {

       Node* temp = head;

       do {

           Node* nextNode = temp->next;

           free(temp);

           temp = nextNode;

       } while (temp != head);

       head = NULL;

   }

}

int main() {

   insertNode(1);

   insertNode(2);

   insertNode(3);

   insertNode(4);

   printList(); // Output: 1 2 3 4

   deleteNode(3);

   printList(); // Output: 1 2 4

   freeList(); // Free all allocated memory

   return 0;

}

 

Output:

1 2 3 4

1 2 4

 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 

Experiment No.: 5

Program Description:

Implementation of Circular Doubly Linked List using Pointers.

Solution:

#include <stdio.h>

#include <stdlib.h>

// Define the Node structure for a circular doubly linked list

struct Node {

   int data;

   struct Node* next;

   struct Node* prev;

};

// Define the CircularDoublyLinkedList structure

struct CircularDoublyLinkedList {

   struct Node* head;

};

// Function to initialize a new circular doubly linked list

void initList(struct CircularDoublyLinkedList* list) {

   list->head = NULL;

}

// Function to insert a new node into the circular doubly linked list

void insertNode(struct CircularDoublyLinkedList* list, int data) {

   struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

   newNode->data = data;

   newNode->next = NULL;

   newNode->prev = NULL;

 

   if (list->head == NULL) {

       list->head = newNode;

       newNode->next = newNode;

       newNode->prev = newNode;

       return;

   }

  struct Node* temp = list->head;

   while (temp->next != list->head) {

       temp = temp->next;

   }

   temp->next = newNode;

   newNode->prev = temp;

   newNode->next = list->head;

   list->head->prev = newNode;

}

// Function to delete a node with a specific value from the circular doubly linked list

void deleteNode(struct CircularDoublyLinkedList* list, int data) {

   if (list->head == NULL) {

       return;

   }

  struct Node* temp = list->head;

  // If the node to be deleted is the head node

   if (temp->data == data) {

       if (temp->next == list->head) {  // Only one node in the list

           list->head = NULL;

           free(temp);

           return;

       }

      temp->prev->next = list->head->next;

       list->head->next->prev = temp->prev;

       list->head = temp->next;

       free(temp);

       return;

   }

   // Traverse the list and find the node to delete

   temp = temp->next;

   while (temp != list->head) {

       if (temp->data == data) {

           temp->prev->next = temp->next;

           temp->next->prev = temp->prev;

           free(temp);

           return;

       }

       temp = temp->next;

   }

}

// Function to print the circular doubly linked list

void printList(struct CircularDoublyLinkedList* list) {

   if (list->head == NULL) {

       return;

   }

 

   struct Node* temp = list->head;

   printf("%d ", temp->data);

   temp = temp->next;

 

   while (temp != list->head) {

       printf("%d ", temp->data);

       temp = temp->next;

   }

   printf("\n");

}

int main() {

   struct CircularDoublyLinkedList list;

   initList(&list);

 

   // Insert nodes into the circular doubly linked list

   insertNode(&list, 1);

   insertNode(&list, 2);

   insertNode(&list, 3);

   insertNode(&list, 4);

 

   // Print the list

   printf("List: ");

   printList(&list);

 

   // Delete node with value 3

   deleteNode(&list, 3);

 

   // Print the list after deletion

   printf("List after deletion: ");

   printList(&list);

 

   return 0;

}

 

Output:

List: 1 2 3 4

List after deletion: 1 2 4

 

 
 
 
 

 


SECTION-B (Stack)

Experiment No.: 1

Program Description:

Implementation of Stack using Array.

Solution:

#include <stdio.h>

#include <stdlib.h>

#define MAX 100 // Define maximum stack size

 

// Stack structure

typedef struct {

   int arr[MAX];

   int top;

} Stack;

 

// Function prototypes

void initStack(Stack *s);

int isFull(Stack *s);

int isEmpty(Stack *s);

void push(Stack *s, int value);

int pop(Stack *s);

int peek(Stack *s);

 

int main() {

   Stack stack;

   int choice, value;

 

   // Initialize stack

   initStack(&stack);

 

   while (1) {

       printf("\nStack Operations:\n");

       printf("1. Push\n");

       printf("2. Pop\n");

       printf("3. Peek\n");

       printf("4. Check if Stack is Empty\n");

       printf("5. Check if Stack is Full\n");

       printf("6. Exit\n");

       printf("Enter your choice: ");

       scanf("%d", &choice);

 

       switch (choice) {

           case 1: // Push

               printf("Enter value to push: ");

               scanf("%d", &value);

               push(&stack, value);

               break;

           case 2: // Pop

               value = pop(&stack);

               if (value != -1) {

                   printf("Popped value: %d\n", value);

               }

               break;

           case 3: // Peek

               value = peek(&stack);

               if (value != -1) {

                   printf("Top value: %d\n", value);

               }

               break;

           case 4: // Check if stack is empty

               if (isEmpty(&stack)) {

                   printf("Stack is empty.\n");

               } else {

                   printf("Stack is not empty.\n");

               }

               break;

           case 5: // Check if stack is full

               if (isFull(&stack)) {

                   printf("Stack is full.\n");

               } else {

                   printf("Stack is not full.\n");

               }

               break;

           case 6: // Exit

               printf("Exiting program.\n");

               exit(0);

           default:

               printf("Invalid choice. Please try again.\n");

       }

   }

 

   return 0;

}

 

// Function to initialize stack

void initStack(Stack *s) {

   s->top = -1; // Stack starts empty

}

 

// Function to check if stack is full

int isFull(Stack *s) {

   return s->top == MAX - 1;

}

 

// Function to check if stack is empty

int isEmpty(Stack *s) {

   return s->top == -1;

}

 

// Function to push an element onto the stack

void push(Stack *s, int value) {

   if (isFull(s)) {

       printf("Stack Overflow! Cannot push %d.\n", value);

   } else {

       s->arr[++s->top] = value;

       printf("Pushed %d onto the stack.\n", value);

   }

}

 

// Function to pop an element from the stack

int pop(Stack *s) {

   if (isEmpty(s)) {

       printf("Stack Underflow! Cannot pop.\n");

       return -1;

   } else {

       return s->arr[s->top--];

   }

}

 

// Function to peek at the top element of the stack

int peek(Stack *s) {

   if (isEmpty(s)) {

       printf("Stack is empty! Cannot peek.\n");

       return -1;

   } else {

       return s->arr[s->top];

   }

}

Output:

Stack Operations:

1. Push

2. Pop

3. Peek

4. Check if Stack is Empty

5. Check if Stack is Full

6. Exit

Enter your choice:

 

 

 

 

 

 

 


Experiment No.: 2

Program Description:

Implementation of Stack using Pointers.
Solution:

#include <stdio.h>

#include <stdlib.h>

 

// Define a structure to represent a stack node

struct StackNode {

   int data;

   struct StackNode *next;

};

 

// Define a structure for the stack

struct Stack {

   struct StackNode *top;  // Pointer to the top node in the stack

};

// Function to initialize the stack

void initStack(struct Stack* stack) {

   stack->top = NULL;

}

// Function to check if the stack is empty

int isEmpty(struct Stack* stack) {

   return stack->top == NULL;

}

// Function to push an element onto the stack

void push(struct Stack* stack, int element) {

   struct StackNode* newNode = (struct StackNode*)malloc(sizeof(struct StackNode));

   newNode->data = element;

   newNode->next = stack->top;

   stack->top = newNode;

}

// Function to pop an element off the stack

int pop(struct Stack* stack) {

   if (isEmpty(stack)) {

       printf("Error: Stack is empty.\n");

       return -1;

   }

   int element = stack->top->data;

   struct StackNode* temp = stack->top;

   stack->top = stack->top->next;

   free(temp);

   return element;

}

// Function to peek at the top element of the stack

int peek(struct Stack* stack) {

   if (isEmpty(stack)) {

       printf("Error: Stack is empty.\n");

       return -1;

   }

   return stack->top->data;

}

int main() {

   struct Stack stack;  // Create a stack object

   initStack(&stack);   // Initialize the stack

 

   // Push some elements onto the stack

   push(&stack, 1);

   push(&stack, 2);

   push(&stack, 3);

 

   // Print the top element of the stack

   printf("Top element: %d\n", peek(&stack));

   // Pop an element off the stack

   printf("Popped element: %d\n", pop(&stack));

   // Print the top element of the stack again

   printf("Top element: %d\n", peek(&stack));

   return 0;

}

Output:

Top element: 3

Popped element: 3

Top element: 2

 

 

 


Experiment No.: 3

Program Description:

Program for Tower of Hanoi using recursion.
Solution:

#include <stdio.h>

 

// Recursive function to solve Tower of Hanoi

void towerOfHanoi(int n, char source, char destination, char auxiliary) {

   // Base case: If only one disk, move it directly

   if (n == 1) {

       printf("Move disk 1 from %c to %c\n", source, destination);

       return;

   }

 

   // Step 1: Move n-1 disks from source to auxiliary using destination

   towerOfHanoi(n - 1, source, auxiliary, destination);

 

   // Step 2: Move the nth disk from source to destination

   printf("Move disk %d from %c to %c\n", n, source, destination);

 

   // Step 3: Move n-1 disks from auxiliary to destination using source

   towerOfHanoi(n - 1, auxiliary, destination, source);

}

 

int main() {

   int n; // Number of disks

 

   // Input: Number of disks

   printf("Enter the number of disks: ");

   scanf("%d", &n);

 

   // Solve the Tower of Hanoi problem

   printf("The sequence of moves for %d disks is:\n", n);

   towerOfHanoi(n, 'A', 'C', 'B'); // 'A' is source, 'C' is destination, 'B' is auxiliary

 

   return 0;

}

 

 

 

 

 

Output:

Enter the number of disks: 2

The sequence of moves for 2 disks is:

Move disk 1 from A to B

Move disk 2 from A to C

Move disk 1 from B to C

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 


Experiment No.: 4

Program Description:

Program to find out factorial of given number using recursion. Also show the various states of stack using in this program.

Solution:

#include <stdio.h>

 

// Recursive function to calculate factorial

int factorial(int n) {

    printf("Entering state: n = %d\n", n); // Show stack state when entering a function call

 

    if (n == 0 || n == 1) { // Base case

        printf("Base case reached: n = %d\n", n);

        printf("Exiting state: n = %d, returning 1\n", n);

        return 1;

    }

 

    int result = n * factorial(n - 1);

    printf("Exiting state: n = %d, returning %d\n", n, result); // Show stack state when returning

    return result;

}

 

int main() {

    int num;

 

    printf("Enter a number to find its factorial: ");

    scanf("%d", &num);

 

    if (num < 0) {

        printf("Factorial is not defined for negative numbers.\n");

    } else {

        printf("\nCalculating factorial of %d using recursion:\n\n", num);

        int result = factorial(num);

        printf("\nFactorial of %d is %d\n", num, result);

    }

 

    return 0;

}


Output:

Enter a number to find its factorial: 3

Calculating factorial of 3 using recursion:

Entering state: n = 3

Entering state: n = 2

Entering state: n = 1

Base case reached: n = 1

Exiting state: n = 1, returning 1

Exiting state: n = 2, returning 2

Exiting state: n = 3, returning 6

 

Factorial of 3 is 6

 

 

 

 

 

 

 

 

 

 

 

 


SECTION-C (Queue)

Experiment No.: 1

Program Description:

Implementation of Queue using Array.
Solution:

#include <stdio.h>

#include <stdlib.h>

#include <limits.h>

 

// Structure for Queue

struct Queue {

   int front, rear, size;

   unsigned actualSize;

   int* arr;

};

 

// Function to create a queue

struct Queue* createQueue(unsigned actualSize) {

   struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));

   queue->actualSize = actualSize;

   queue->front = queue->rear = -1;

   queue->size = 0;

   queue->arr = (int*)malloc(queue->actualSize * sizeof(int));

   return queue;

}

 

// Check if the queue is full

int isFull(struct Queue* queue) {

   return (queue->size == queue->actualSize);

}

 

// Enqueue operation

void enqueue(struct Queue* queue, int item) {

   if (isFull(queue)) {

       printf("Queue is full. Cannot enqueue %d.\n", item);

       return;

   }

   if (queue->rear == -1) {

       queue->front = 0;

       queue->rear = 0;

   } else {

       queue->rear = (queue->rear + 1) % queue->actualSize;

   }

   queue->arr[queue->rear] = item;

   queue->size++;

   printf("%d enqueued to queue.\n", item);

}

 

// Check if the queue is empty

int isEmpty(struct Queue* queue) {

   return (queue->size == 0);

}

 

// Dequeue operation

int dequeue(struct Queue* queue) {

   if (isEmpty(queue)) {

       printf("Queue is empty.\n");

       return INT_MIN;

   }

   int item = queue->arr[queue->front];

   if (queue->front == queue->rear) {

       queue->front = queue->rear = -1;

   } else {

       queue->front = (queue->front + 1) % queue->actualSize;

   }

   queue->size--;

   return item;

}

 

// Return the front element of the queue

int front(struct Queue* queue) {

   if (isEmpty(queue)) {

       return INT_MIN;

   }

   return queue->arr[queue->front];

}

 

// Return the rear element of the queue

int rear(struct Queue* queue) {

   if (isEmpty(queue)) {

       return INT_MIN;

   }

   return queue->arr[queue->rear];

}

 

int main() {

   int val, n;

   struct Queue* queue = createQueue(1000); // Create a queue with size 1000

 

   do {

       printf("\n**************************MENU*************\n");

       printf("1. ENQUEUE\n");

       printf("2. DEQUEUE\n");

       printf("3. IS EMPTY\n");

       printf("4. IS FULL\n");

       printf("5. FRONT ELEMENT\n");

       printf("6. LAST ELEMENT\n");

       printf("7. EXIT\n");

       printf("Enter your choice: ");

       scanf("%d", &n);

 

       switch(n) {

           case 1:

               printf("Enter the value to enqueue: ");

               scanf("%d", &val);

               enqueue(queue, val);

               break;

           case 2:

               val = dequeue(queue);

               if (val != INT_MIN) {

                   printf("Dequeued value: %d\n", val);

               }

               break;

           case 3:

               printf("IsEmpty: %d\n", isEmpty(queue));

               break;

           case 4:

               printf("IsFull: %d\n", isFull(queue));

               break;

           case 5:

               printf("Front element: %d\n", front(queue));

               break;

           case 6:

               printf("Last element: %d\n", rear(queue));

               break;

           case 7:

               break;

           default:

               printf("Wrong choice! Please enter a valid option.\n");

               break;

       }

 

       printf("\nDo you want to continue? (1 for yes, 0 for no): ");

       scanf("%d", &n);

   } while(n != 0);

 

   // Free the allocated memory

   free(queue->arr);

   free(queue);

 

   return 0;

}

 

Output:

1. ENQUEUE

2. DEQUEUE

3. IS EMPTY

4. IS FULL

5. FRONT ELEMENT

6. LAST ELEMENT

7. EXIT

Enter your choice: 2

Queue is empty.
