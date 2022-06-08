# Leetcode 1332. Remove Palindromic Subsequences

## Problem: 
The description of the problem is given [here](https://leetcode.com/problems/remove-palindromic-subsequences/).

In fact we are given a string. In a single step one can remove one `palindromic subsequence` from s. We want to compute the `minimum number of steps` needed to make the string empty.
One constraint is that we can only use two characters in the string `a` and `b`.
Example 1:
```
Input: s = "ababa"
Output: 1
Explanation: s is already a palindrome, so its entirety can be removed in a single step.
```

Example 2:
```
Input: s = "abb"
Output: 2
Explanation: "abb" -> "bb" -> "". 
Remove palindromic subsequence "a" then "bb".
```

Example 3:
```
Input: s = "baabb"
Output: 2
Explanation: "baabb" -> "b" -> "". 
Remove palindromic subsequence "baab" then "b".
```

## Thinking process
This problem is categorized as an easy problem and i think so too. we only need to see that if the string is empty, that means the number of steps to make it empty is zero, if the string is a palindrome, we just have to remove the whole string and that can be done in one step. It becomes tricky when the string is not a palindrome.
When the string is not a palindrome, we have two steps to make the string empty, either we can regroup the `a` together and the `b` together or we can remove a part of the string and the rest is also a palindrome. we ar just leveraging the fact that we only have two type of characters `a` and `b`.

The time complexity of this approch is `O(n)`.

## Code
```
public int removePalindromeSub(String s) {
  if (s == null || s.length() == 0) {
    return 0;
  }
  
  StringBuilder sb = new StringBuilder(s);
  sb.reverse();
  if (s.equals(sb.toString())) {
    return 1;
  }
  
  return 2;
}
```


