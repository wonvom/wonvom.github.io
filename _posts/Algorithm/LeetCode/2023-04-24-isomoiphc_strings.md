---
title: LeetCode75 || 205. Isomorphic Strings | +
author: wonvom
date: 2023-04-24 10:00:00 -0800
categories: [Algorithm, LeetCode]
tags: [isomorphic strings, algorithm, python, linear time, linear space, string manipulation, leetcode, leetcode205]
math: true
pin: false
---

# Isomorphic Strings

### **Problem**
Given two strings `s` and `t`, determine if they are isomorphic.

Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t`.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

**Example 1**
```
Input: s = "egg", t = "add"
Output: true
```


**Example 2**
```
Input: s = "foo", t = "bar"
Output: false
```

**Example 3**
```
Input: s = "paper", t = "title"
Output: true
```


### **Solution**
```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        mapA = {}
        mapB = {}
        
        for i in range(len(s)):
            c1 = s[i]
            c2 = t[i]
            
            if ((c1 in mapA and mapA[c1] != c2) 
                or (c2 in mapB and mapB[c2] != c1)):
                return False
            mapA[c1] = c2
            mapB[c2] = c1
        return True
```

### **Explain**
1. Create two dictionaries, mapA and mapB, to store the character mappings from s to t and from t to s, respectively.
2. Iterate through each character c1 in s and the corresponding character c2 in t.
3. Check if there is a mismatch in character mappings between mapA and mapB. If there is a mismatch, return False.
4. Update the character mappings in mapA and mapB.
If there is no mismatch found during the iteration, return True at the end.

### **Complexity**
Time Complexity: 
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the input strings s and t once, so the time complexity is linear with the length of the input strings.

Space Complexity: 
$$ \mathcal{O}(n) $$ <br>
The algorithm uses two dictionaries to store character mappings, which have linear space complexity with the length of the input strings.

<br><br><br>
Citation
- https://leetcode.com/problems/isomorphic-strings/


<br><br>
![Desktop View](/assets/img/whale/whale7.png){: w="300" h="300" }