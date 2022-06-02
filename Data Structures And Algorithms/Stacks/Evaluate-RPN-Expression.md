# Evaluate an RPN (Reverse Polished Notation) expression.
## Problem: 
A string is said to be an arithmetical expression in Reverse Polish notation (RPN), if: 
- It is a single digit or a sequence of digits, prefixed with an option -, e.g., "6", "123", "-42".
- It is of the form“A,B,o" where A and B are RPN expressions and o is one of +,-,*,/
For example, the following strings satisfy these rules: "1729", "3,4,+,2,X,1,+", "1,1,+,-2,x","-641,6,/,28,/".

Write a program that takes an arithmetical expression in RPN and returns the number that the expression evaluates to.

## Thinking process
The first thing that comes to my mind when we are talking about evaluating an expression, is the use of the stack to do so. Given the fact that the expression is an RPN (Reverse Polish Notation), we can straightly evaluate.

Let's suppose we have an expression such as the following s = "3,4,+,2,*,1,+". The first thing to do is to split the string based on the comma delimiter. We will have a set of tokens to traverse.

- We create a stack to store all the operands.
- We traverse the list of the tokens. 
- If the current token is a number, then we push that token onto the stack.
If the current token is an operator, we pop the two operands on top of the stack and apply the operator and push the result back onto the stack 
and continue to traverse the list of tokens.
- When we are done traversing the list of tokens, the last element in the stack is the result the expression evaluates to.

We assume that the expression will be given in the form of "3,4,+,2,*,1,+" with comma separated.

The time complexity is O(n) which is the number of characters in the given expression, and the space complexity is O(2), which is constant.


## Code
```
public int evaluateRPNExpresion(String expr) {
  Stack<Integer> stack = new Stack<Integer>();
  String[] tokens = expr.split(",");
  for (String token : tokens) {
    if (isOperator(token)) {
      char c = token.trim().charAt(0);
      int val = 0;
      int val1 = stack.pop();
      int val2 = stack.pop();
      switch(c) {
        case '+':
          val = val1 + val2;
        break;
        case '-':
          val = val1 - val2;
        break;
        case '*':
          val = val1 * val2;
        break;
        case '/':
          if (val == 0) {
            throw new IllegaStateException("Division By zero");
          }
          val = val1 / val2;
        break;
      }
      stack.push(val);
    } else {
      stack.push(Integer.parseInt(token.trim()));
    } 
  }
  return stack.peek();
}

public boolean isOperator(String s) {
  Set<Character> opSet = new HashSet<>(Arrays.asList('+', '-', '*', '/'));
  if (s == null || s.length() = 0) {
    return false;
  }
  return s.length() == 1 && opSet.contains(s.charAt(0));
}
```
