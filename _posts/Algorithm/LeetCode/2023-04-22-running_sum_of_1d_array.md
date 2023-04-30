---
title: LeetCode75 || 1480. Running Sum of 1D Array | +
author: wonvom
date: 2023-04-22 8:52:00 -0800
categories: [Algorithm, LeetCode]
tags: [array, running sum, algorithm, python, linear time, linear space, 1d array, leetcode, leetcode1480]
math: true
pin: false
---

# Running Sum of 1D Array

### **Problem**
Given an array `nums`, we define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`. Return the running sum of `nums`.

**Example 1**
```
Input: nums = [1, 2, 3, 4]
Output: [1, 3, 6, 10]
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```

**Example 2**
```
Input: nums = [1, 1, 1, 1, 1]
Output: [1, 2, 3, 4, 5]
Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].
```

**Example 3**
```
Input: nums = [3, 1, 2, 10, 1]
Output: [3, 4, 6, 16, 17]
```


### **Solution**
```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        result = []
        sum = 0
        for i in nums:
            sum += i
            result.append(sum)
        return result
```

### **Explain**

1. Initialize an empty list result and a variable sum with a value of 0.
2. Iterate through each element i in the input list nums.
3. Add the value of i to the sum variable.
4. Append the updated sum value to the result list.
5. Return the result list after iterating through all elements in nums.



### **Complexity**
Time Complexity:
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the input list nums once, so the time complexity is linear with the size of the input list.

Space Complexity: 
$$ \mathcal{O}(n) $$ <br>
The algorithm uses a result list to store the running sum values, which has the same size as the input list nums. Therefore, the space complexity is linear with the size of the input list.

<br><br><br>
Citation
- https://leetcode.com/problems/running-sum-of-1d-array/


<br><br>
![Desktop View](/assets/img/whale/whale5.png){: w="300" h="300" }