# Normalize Paths
## Problem: 
Write a program which takes a pathname, and returns the shortest equivalent path¬ name. Assume individual directories and files have names that use only alphanu¬ meric characters. Subdirectory names may be combined using forward slashes (/), the current directory (.), and parent directory (..).

## Thinking process
In order to normalize a Unix style pathname, we will need to consider some cases. After we split the given pathane based on the forward slash ("/"), we need to traverse the list of tokens.
- traverse the list of token:
- if the current token is a '.' or is empty, then ignore the token.
- if the current token is '..', we check if the stack is not empty, if yes, we pop the last element, because '..' means we are going back to the parent folder
- otherwise we push the token to the stack
- Once we have traversed all the tokens, we need to traverse the stack and reconstruct the new pathname and return it.

The time complexity of each operation is O(# of tokens), but for the space, we will have to maintain O(# of tokens).

## Dry-run
Let's suppose we have path = "/home//foo/"
split = <home,/,foo>


## Code 
```
public String normalizePath(String path) {
  if (path == null || path.length() == 0) {
    return "";
  }
  
  Stack<String> stack = new Stack<>();
  String[] splitPaths = path.split("/");
  for (String token : splitPaths) {
    if (token.equals(".") || token.isEmpty()) {
      continue;
    } else if (token.equals("..")) {
      if (!stack.isEmpty()) {
        stack.pop();
      }
    } else {
      stack.push(token);
    }
  }
  
  StringBuilder sb = new StringBuilder();
  for (String s : stack) {
    sb.append("/").append(s);
  }
  
  return sb.length() > 0 ? sb.toString() : "/";
}
```
