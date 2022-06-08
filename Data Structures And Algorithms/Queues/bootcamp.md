# Basic.
Queue is an abstract data type that support mainly two operations : `dequeue()` and `enqueue(o)`. Another operation could also be `isEmpty()` to check whether the queue is empty of not. The queue is managed by the FIFO (First In First Out) policy, this means the first to comes to the collection is the first to be served out of the collection.
- `enqueue(o)` : insert object o at the rear of the collection. input : object, output : None
- `dequeue() ` : remove the object from the front of the collection and return it. An error occurs if the queue is empty. Input : none, output : object

These support methods should also be defined :
- `size()    ` : returns the number of objects in the collection
- `isEmpty() ` : returns a boolean value that indicates whether the queue is empty
- `front()   ` : returns but not remove the front object in the collection; an error occurs if the collection is empty. 

# Knowledge
Queues can be implemented using arrays or linked lists. Depending of whichever data structures we use, the time complexity can vary from better to armortized to worst cases. In all our cases, we will be using the Linked Lists because that is the data structure that give us the best time complexity possible.
- Inserting an object at the front of a linked list takes O(1).
- Deleting an element from the end of the linked list takes O(1) time complexity.
- Getting the size of the linked list requires to traverse the list and counting the element, thus this takes O(n) time.
- Checking if the linked list is empty requires checking is the list is null, thus this take O(1) time
- Getting the front element of the collection takes O(1) time.

# Java libraries for Queues
In Java, we can represent a queue using two interfaces : `Queue<E>` and `Deque<E>`. Each of these interface can be implemented using the class `LinkedList<E>` in java. So we have the following code:
```
Queue<Integer> queue1 = new LinkedList<Integer>();
Deque<Integer> queue2 = new LinkedList<Integer>();
```
