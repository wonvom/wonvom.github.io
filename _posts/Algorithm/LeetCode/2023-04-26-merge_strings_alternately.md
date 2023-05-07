---
title: LeetCode75 || 1768. Merge Strings Alternately | +
author: wonvom
date: 2023-04-26 11:10:00 -0800
categories: [Algorithm, LeetCode]
tags: [string, merge strings, alternately, algorithm, python, leetcode, leetcode1768]
math: true
pin: false
---

# Merge Strings Alternately

### **Problem**
You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

**Example 1**
```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1: a b c
word2: p q r
merged: a p b q c r
```


**Example 2**
```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1: a b
word2: p q r s
merged: a p b q r s
```


**Example 3**
```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1: a b c d
word2: p q
merged: a p b q c d
```


### **Solution**
```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        i = 0
        j = 0
        result = []
        
        while i < len(word1) and j < len(word2) :
            result.append(word1[i])
            result.append(word2[j])
            i += 1
            j += 1
        result.append(word1[i:])
        result.append(word2[j:])
        
        return "".join(result)
```

### **Explain**
1. Initialize two pointers i and j to 0, and an empty list result.
2. Iterate through both strings word1 and word2 using the pointers i and j.
3. Append the character at index i in word1 and the character at index j in word2 to the result list.
4. Increment both pointers i and j.
5. After the iteration, append the remaining characters of word1 and word2 to the result list.
6. Convert the result list to a string and return it.


### **Complexity**
Time Complexity:
$$ \mathcal{O}(n+m) $$ <br>
The algorithm iterates through both input strings once, so the time complexity is linear with the sum of the lengths of the input strings.

Space Complexity:
$$ \mathcal{O}(n+m) $$ <br>
The algorithm uses a result list to store the merged characters, which has the combined length of the input strings. Therefore, the space complexity is linear with the sum of the lengths of the input strings.

<br><br><br>
Citation
- https://leetcode.com/problems/merge-strings-alternately/

<br><br>
![Desktop View](/assets/img/whale/whale9.png){: w="300" h="300" }