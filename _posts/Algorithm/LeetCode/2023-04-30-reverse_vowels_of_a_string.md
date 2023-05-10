---
title: LeetCode75 || 345. Reverse Vowels of a String | +
author: wonvom
date: 2023-04-30 14:20:00 -0800
categories: [Algorithm, LeetCode]
tags: [string, algorithm, python, leetcode, leetcode345]
math: false
pin: false
---

# Reverse Vowels of a String

### **Problem**
Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

**Example 1**
```
Input: s = "hello"
Output: "holle"
```


**Example 2**
```
Input: s = "leetcode"
Output: "leotcede"
```


### **Solution**
```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        vowels = set('aeiouAEIOU')  # Define the vowels
        s = list(s)  # Convert the string to a list of characters for easier manipulation
        left, right = 0, len(s) - 1  # Initialize two pointers

        while left < right:
            if s[left] not in vowels:  # If the left pointer is not a vowel, move it to the right
                left += 1
            elif s[right] not in vowels:  # If the right pointer is not a vowel, move it to the left
                right -= 1
            else:  # If both pointers are vowels, swap the characters and move both pointers
                s[left], s[right] = s[right], s[left]
                left += 1
                right -= 1

        return ''.join(s)  # Convert the list of characters back to a string and return it
```

### **Explain**
1. Define the vowels as a set for quick look-up.
2. Convert the input string s to a list of characters for easier manipulation.
3. Initialize two pointers, left and right, at the beginning and end of the list, respectively.
4. While left is less than right, check if the characters at both pointers are vowels.
5. If the character at left is not a vowel, increment left. If the character at right is not a vowel, decrement right.
6. If both characters at the pointers are vowels, swap them and move both pointers.
7. Continue this process until the left pointer is greater than or equal to the right pointer.
8. Convert the list of characters back to a string and return the result.


### **Complexity**
Time Complexity: 
$$ \mathcal{O}(n) $$<br>
The algorithm iterates through the string once, so the time complexity is linear with the number of characters in the string.

Space Complexity: 
$$ \mathcal{O}(n) $$<br>
The algorithm creates a list of characters from the input string, which requires linear space.

<br><br><br>
Citation

https://leetcode.com/problems/reverse-vowels-of-a-string/

<br><br>
![Desktop View](/assets/img/whale/whale13.png){: w="300" h="300" }