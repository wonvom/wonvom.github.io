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

### **Solution** <br>
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
            for j in range(1, i-1):
                temp[j] = answer[-1][j] + answer[-1][j-1]
            answer.append(temp)
        return answer
```

### **Explain**

1. The code first checks if "numRows" is 1, if so it returns [[1]]
2. If "numRows" is not 1, it checks if "numRows" is 2, if so it returns [[1], [1, 1]]
3. If "numRows" is not 2, it initializes the variable "answer" with the first two rows of the pascal's triangle, [[1], [1, 1]]
4. It starts a for loop that runs from 3 to numRows+1.
5. In each iteration of the loop, it creates a temporary list "temp" of size i filled with 1s.
6. It starts another for loop that runs from 1 to i-1.
7. In each iteration of the inner loop, it updates the ith element of "temp" with the sum of the (i-1)th element of the last row of "answer" and the (i-2)th element of the last row of "answer".
8. It appends "temp" to "answer"
9. At the end of the for loop, the function returns "answer" which is a 2D list that represents the Pascal's triangle with "numRows" number of rows.

```
Example 1 : numRows = 5
answer = [[1], [1, 1]]
i = 3 -> temp = [1, 1, 1]
    j = 1 -> temp[1] = 1 + 1 
    -> temp = [1, 2, 1] 
    -> answer = [[1], [1, 1], [1, 2, 1]]
i = 4 -> temp = [1, 1, 1, 1]
    j = 1 -> temp[1] = 2 + 1
    j = 2 -> temp[2] = 1 + 2
    -> temp = [1, 3, 3, 1]
    -> answer = [[1], [1, 1], [1, 2, 1], [1, 3, 3, 1]]
```
### **Complexity**
Time Complexity : $$ \mathcal{O}(n^2) $$ <br>
Although updating each value of triangle happens in constant time, it is performed $$ \mathcal{O}(n^2) $$ times. To see why, consider how many overall loop iterations there are. The outer loop obviously runs $$ \mathcal{O}(n) $$ times, but for each iteration of the outer loop, the inner loop runs $$ \mathcal{O}(n) $$ times. Therefore, it runs $$ \mathcal{O}(n^2) $$ times <br><br>
Space Complexity : $$ \mathcal{O}(n) $$ <br>
While space $$ \mathcal{O}(n^2) $$ is used to store the output, the input and output generally do not count towards the space complexity.
<br>
<br>
<br>
Citation
- <https://leetcode.com/problems/pascals-triangle/solution/>

<br><br>
![Desktop View](/assets/img/whale/whale3.png){: w="300" h="300" }