# Basic.
A stack is an abstract data type that supports four basic operations, push, pop, peek and empty. Elements are added and removed from the stack following the LIFO (Last In First Out) policy.
Elements are added (pushed) on top of the stack and they are removed (popped) from the top of the stack. If the stack is empty, pop operation typically returns null or throws an exception.
 
- push(element) : add an element on top of the stack
- pop() : remove the element on top of the stack and return null or throw an exefption if the stack is empty
- peek() : return the element on top of the stack and return null or throws an exception if the stack is empty
- isEmpty() : return true if the stack is empty and false otherwise.

# Knowledge
Stacks can be implemented using arrays or linked lists. Depending of whiever data structures we use, the time complexity can vary from better to armortized to worst cases.

## Using arrays

## Using linked lists
When you use linked list to implement the stack, all the operations run in O(i). We are adding a node at the head of the linked list when pushing, we are removing a node at the head when popping, we are just reading the value of the head node when getting the peek and we are checking is the head noe is null when checking if the stack is empty.

# Java libraries for Stacks
