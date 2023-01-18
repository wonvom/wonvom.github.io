---
title: Top100 || 118. Pascal's Triangle | +
author: wonvom
date: 2023-01-13 10:00:00 -0800
categories: [Algorithm, LeetCode]
tags: [leetcode, easy, problem118, pascal's triangle, algorithm]
math: true
pin: false
---

# Pascal's Triangle

### **Problem**
Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example 1**
```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```
**Example 2**
```
Input: numRows = 1
Output: [[1]]
```

### **Solution**
```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows == 1:
            return [[1]]
        if numRows == 2:
            return [[1], [1, 1]]
        
        answer = [[1], [1, 1]]
        for i in range(3, numRows+1):
            temp = [1]*i
            print(temp)
            for j in range(1, i-1):
                print(answer[-1][0])
                print(answer[-1][-1])
                temp[j] = answer[-1][j] + answer[-1][j-1]
                print(temp)
            answer.append(temp)
        return answer
```

### **Explain**

### **Complexity**


Citation
- https://leetcode.com/problems/pascals-triangle/solution/