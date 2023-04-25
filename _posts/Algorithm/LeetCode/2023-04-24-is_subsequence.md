---
title: LeetCode75 || 392. Is Subsequence || +
author: wonvom
date: 2023-04-24 12:09:00 -0800
categories: [Algorithm, LeetCode]
tags: [string, subsequence, algorithm, python, linear time, leetcode, leetcode392]
math: true
pin: false
---

# Is Subsequence

### **Problem**
Given two strings `s` and `t`, return true if `s` is a subsequence of `t`, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

**Example 1**
```
Input: s = "abc", t = "ahbgdc"
Output: true
```

**Example 2**
```
Input: s = "axc", t = "ahbgdc"
Output: false
```

### **Solution**
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i = 0
        j = 0
        
        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i += 1
            j += 1
        
        if i == len(s):
            return True
        else:
            return False
```

### **Explain**

1. Initialize two pointers i and j with a value of 0.
2. Use a while loop to iterate through both strings s and t as long as neither i nor j reaches the end of their respective strings.
3. If the characters at index i of s and index j of t are equal, increment i by 1.
4. Increment j by 1 for each iteration.
5. After the while loop, if i is equal to the length of s, then all characters in s are found in t in the correct order, and the function returns True. Otherwise, it returns False.


### **Complexity**

Time Complexity:
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the input strings once, so the time complexity is linear with the size of the input strings.

Space Complexity:
$$ \mathcal{O}(1) $$ <br>
The algorithm uses constant extra space for the pointers i and j. Therefore, the space complexity is constant.

<br><br><br>
Citation

https://leetcode.com/problems/is-subsequence/
<br><br>
![Desktop View](/assets/img/whale/whale7.png){: w="300" h="300" }