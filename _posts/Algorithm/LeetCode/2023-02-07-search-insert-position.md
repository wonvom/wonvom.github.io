---
title: Top100 || 35. Search Insert Position | +
author: wonvom
date: 2023-02-07 15:30:00 -0800
categories: [Algorithm, LeetCode]
tags: [leetcode, easy, problem35, search insert position, algorithm, array]
math: true
pin: false
---

# Search Insert Position

### **Problem**
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with $$ \mathcal{O}(logn) $$ runtime complexity.

**Example 1**
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

**Example 2**
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```

**Example 3**
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

### **Solution**
```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        
        left = 0
        right = len(nums) - 1

        while left <= right:
            mid = (left + right) // 2

            if target == nums[mid]:
                return mid
            
            if target > nums[mid]:
                left = mid + 1
            else:
                right = mid -1
        return left
```
### **Explain**
1. The searchInsert function takes in two parameters, nums which is a list of integers representing a sorted array and target which is the target value we are trying to find or insert into the array.

2. We start by initializing two pointers, left and right, to the beginning and end of the array, respectively. We then use a while loop to perform a binary search. The loop continues until left is greater than right.

3. In each iteration of the loop, we calculate the middle index mid as the average of left and right. We then compare target with the value at the mid index in the nums array. If target is equal to nums[mid], we have found the target and return mid as the result.

4. If target is greater than nums[mid], we update left to be mid + 1. This is because the target must be in the right half of the array.

5. If target is less than nums[mid], we update right to be mid - 1. This is because the target must be in the left half of the array.

6. Finally, after the loop, left will be the index where the target should be inserted.

```
Example 2 : nums = [1,3,5,6], target = 2
left = 0 , right = 3
i) left < right
    mid = ( 0 + 3 ) // 2 = 1
    target > mid
        left = mid + 1 = 2
ii) left < right
    mid = ( 2 + 3 ) // 2 = 2
    target = mid = 2
        return 2
```


### **Complexity**
Time Complexity : $$ \mathcal{O}(logn) $$ <br>
The n is the length of the nums array. This is because in each iteration, the size of the search space is halved.
<br><br>

Space Complexity : $$ \mathcal{O}(1) $$ <br>
As we only use a few variables.
