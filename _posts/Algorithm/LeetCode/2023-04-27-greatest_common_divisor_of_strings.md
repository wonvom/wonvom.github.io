---
title: LeetCode75 || 1071. Greatest Common Divisor of Strings | +
author: wonvom
date: 2023-04-27 12:30:00 -0800
categories: [Algorithm, LeetCode]
tags: [string, greatest common divisor, algorithm, python, leetcode, leetcode1071]
math: true
pin: false
---

# Greatest Common Divisor of Strings

### **Problem**
For two strings s and t, we say "t divides s" if and only if s = t + ... + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

**Example 1**
```
Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
```

**Example 2**
```
Input: str1 = "ABABAB", str2 = "ABAB"
Output: "AB"
```

**Example 3**
```
Input: str1 = "LEET", str2 = "CODE"
Output: ""
```


### **Solution**
```python
class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        len1 = len(str1)
        len2 = len(str2)
        
        def isDivisor(l) :
            if len1 % l or len2 % l:
                return False
            f1, f2 = len1 // l , len2 // l
            return str1[:l] * f1 == str1 and str1[:l] *f2 == str2
        for l in range(min(len1, len2), 0, -1):
            if isDivisor(l):
                return str1[:l]
        return ""
```

### **Explain**
1. Calculate the lengths of both strings str1 and str2.
2. Define a helper function isDivisor(l) that checks if a given length l is a valid divisor of both strings str1 and str2.
- The function returns False if the lengths of the strings are not divisible by l.
- Otherwise, the function checks if the first l characters of str1 repeated a certain number of times form str1 and str2.
- If yes, the function returns True. Otherwise, it returns False.
3. Iterate through all possible lengths l (from the minimum length of the two strings to 1), and check if isDivisor(l) returns True.
4. If the function returns True, return the first l characters of str1 as the result.
5. If no such l is found, return an empty string.

### **Complexity**
Time Complexity:
$$ \mathcal{O}(n^2) $$ <br>
The algorithm iterates through all possible lengths and performs a string comparison operation in the helper function isDivisor(l). Thus, the time complexity is quadratic with the length of the input strings.

Space Complexity:
$$ \mathcal{O}(1) $$ <br>
The algorithm uses a constant amount of additional space to store variables and does not require any additional data structures. Therefore, the space complexity is constant.

<br><br><br>
Citation

https://leetcode.com/problems/greatest-common-divisor-of-strings/

<br><br>
![Desktop View](/assets/img/whale/whale10.png){: w="300" h="300" }