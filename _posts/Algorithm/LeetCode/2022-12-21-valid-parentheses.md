---
title: Top100 || 20. Valid Parentheses | +
author: wonvom
date: 2022-12-21 04:04:00 -0800
categories: [Algorithm, LeetCode]
tags: [leetcode, easy, problem20, valid parentheses, algorithm]
math: true
pin: false
---


# Valid Parentheses

### **Problem**

Given a string s containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
<br>
<br>
An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

<br>

**Example 1**
```
Input: s = "()"
Output: true
```

**Example 2**
```
Input: s = "()[]{}"
Output: true
```

**Example 3**
```
Input: s = "(]"
Output: false
```

<br>
<br>

### **Solution** <br>

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {
            ')': '(',
            ']': '[',
            '}': '{',
        }

        for char in s:
            if char not in mapping:
                stack.append(char)
            else:
                if not stack:
                    return False
                opening = stack.pop()
                if mapping[char] != opening:
                    return False
        return not stack
```

### **Explain**

1. The method creates an empty stack called stack.
2. It creates a dictionary called mapping that maps closing parentheses to their corresponding opening parentheses.
3. The method then iterates through each character in the string s.
4. If the current character is not a closing parenthesis, it is pushed onto the stack.
5. If the current character is a closing parenthesis, the method checks if the stack is empty. If it is, the method returns False as there is no corresponding opening parenthesis.
6. If the stack is not empty, the method pops the top element of the stack, which should be the corresponding opening parenthesis.
7. If the popped element is not the same as the mapped opening parenthesis for the current closing parenthesis, the method returns False as the parentheses are not properly matched.
8. If the method completes the loop and the stack is not empty, it means there are unmatched opening parentheses so the method returns False. Else returns True if stack is empty and all the brackets are closed.

```
Example 3 : s = "(]"
char = `(` -> stack = `(` 
    because `(` is not in the dictionary called mapping
char = `]` -> stack = empty, opening = `(`
    opening : `(` != mapping[`]`] : `[`
    -> False
```

### **Complexity**

Time Complexity : $$ \mathcal{O}(n) $$
<br>
 We simply traverse the given string one character at a time and push and pop operations on a stack take $$ \mathcal{O}(1) $$time.
<br><br>
Space Complexity : $$ \mathcal{O}(n) $$
<br>
 We push all opening brackets onto the stack and in the worst case, we will end up pushing all the brackets onto the stack. 
  <br>e.g. ((((((((((.
<br>
<br>
<br>

Citation
- <https://leetcode.com/problems/valid-parentheses/solution/>

<br><br>
![Desktop View](/assets/img/whale/whale2.png){: w="300" h="300" }