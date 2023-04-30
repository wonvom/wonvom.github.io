---
title: LeetCode75 || 724. Find Pivot Index | +
author: wonvom
date: 2023-04-21 10:00:00 -0800
categories: [Algorithm, LeetCode]
tags: [array, pivot index, algorithm, python, linear time, linear space, find pivot index, leetcode, leetcode724]
math: true
pin: false
---

# Find Pivot Index

### **Problem**
Given an array of integers `nums`, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.

Return the leftmost pivot index. If no such index exists, return -1.

**Example 1**

```
Input: nums = [1, 7, 3, 6, 5, 6]
Output: 3
Explanation:
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
```


**Example 2**
```
Input: nums = [1, 2, 3]
Output: -1
Explanation:
There is no index that satisfies the conditions in the problem statement.
```


**Example 3**
```
Input: nums = [2, 1, -1]
Output: 0
Explanation:
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
```


### **Solution**
```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        total = sum(nums)
        leftSum = 0
        for i in range(len(nums)):
            rightSum = total - nums[i] - leftSum
            if leftSum == rightSum:
                return i
            leftSum += nums[i]
        return -1
```

### **Expalin**
1. Calculate the total sum of the input list nums.
2. Initialize a variable leftSum with a value of 0.
3. Iterate through each element nums[i] in the input list nums.
4. Calculate the rightSum as the total sum minus the current element nums[i] and the leftSum.
5. If leftSum is equal to rightSum, return the current index i.
6. If no such index is found during the iteration, return -1 at the end.

### **Complexity**
Time Complexity: 
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the input list nums once, so the time complexity is linear with the size of the input list.

Space Complexity: 
$$ \mathcal{O}(1) $$ <br>
The algorithm uses a few variables (total, leftSum, and rightSum) to store intermediate values, which have constant space complexity.

<br><br><br>
Citation
- https://leetcode.com/problems/find-pivot-index/


<br><br>
![Desktop View](/assets/img/whale/whale6.png){: w="300" h="300" }