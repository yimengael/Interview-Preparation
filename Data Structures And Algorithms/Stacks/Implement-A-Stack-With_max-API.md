# Implement a stack with Max API
## Problem: 
Design a stack that includes a max operation, in addition to push and pop. The max method should return the maximum value stored in the stack. 
## Thinking process
The stack is a data structure that allows you to push an element on top of the stack and pop the element on top of the stack. So if we want to maintain the stack operation and maintain the max element of the stack, we will need to find a mechanism to do so.

1) The first approach that comes to my mind is that : Let's suppose that we have a variable MaxValue that will maintain the maximum element in the stack so far. When we push an element onto the stack, we will update MaxValue variable easily by doing MaxValue = Math.max(MaxValue, element), element being the data that we want to push on top of the stack. But when we are doing pop() operation, we do not have an easier way to update Max except to traverse the whole stack and look for the maximum element.

2) Let's consider that we have two stacks, the first stack is for the actual values and the second stack is to maintain the maximum at every push or pop operation.

- When we push the first value onto the value stack, we push the same value onto the maximum stack.
- If we push a value x onto the value stack, we check if maxStack.peek() > x, if yes, we do maxStack.push(Math.max(maxStack.peek(), x)), otherwise we do maxStack.push(x).
- If we pop from the value stack, we also pop from the maximum stack and we return the value.
- If we want to get the maximum value of the stack, we just return the peek() of the maximum stack.

The time complexity of each operation is O(1), but for the space, we will have to maintain O(n) space for the maximum stack.


## Code 
```
public class MaxStack {

  Stack<Integer> valueStack;
  Stack<Integer> maxStack;
  
  public MaxStack() {
    valueStack = new Stack<Integer>();
    maxStack = new Stack<Integer>();
  }
  
  public int isEmpty() {
    return valueStack.isEmpty();
  }
  
  public int pop() {
    if (valueStack.isEmpty()) {
      throw new IllegalStateException("pop(): the stack is empty");
    }
    int val = valueStack.pop();
    return val;
  }
  
  public void push(int x) {
    int max = maxStack.isEmpty() ? x : maxStack.peek();
    maxStack.push(max > x ? max : x);
    valueStack.push(x);
  }
  
  public int peek() {
    if (valueStack.isEmpty()) {
      throw new IllegalStateException("pop(): the stack is empty");
    }
    int val = valueStack.peek();
    return val;
  }
  
  public int max() {
    if (valueStack.isEmpty()) {
      throw new IllegalStateException("pop(): the stack is empty");
    }
    int max = maxStack.peek();
    return max;
  }
}
```
