---
title: LeetCode75 || 1431. Kids With the Greatest Number of Candies | +
author: wonvom
date: 2023-04-28 13:30:00 -0800
categories: [Algorithm, LeetCode]
tags: [array, boolean, algorithm, python, leetcode, leetcode1431]
math: false
pin: false
---

# Kids With the Greatest Number of Candies

### **Problem**
There are n kids with candies. You are given an integer array candies, where each candies[i] represents the number of candies the ith kid has, and an integer extraCandies, denoting the number of extra candies that you have.

Return a boolean array result of length n, where result[i] is true if, after giving the ith kid all the extraCandies, they will have the greatest number of candies among all the kids, or false otherwise.

Note that multiple kids can have the greatest number of candies.

**Example 1**
```
Input: candies = [2,3,5,1,3], extraCandies = 3
Output: [true,true,true,false,true]
```

**Example 2**
```
Input: candies = [4,2,1,1,2], extraCandies = 1
Output: [true,false,false,false,false]
```

**Example 3**
```
Input: candies = [12,1,12], extraCandies = 10
Output: [true,false,true]
```


### **Solution**
```python
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        max_candies = max(candies)
        result = []
        for candy in candies:
            if candy + extraCandies >= max_candies:
                result.append(True)
            else:
                result.append(False)
        return result
```

### **Explain**
1. Find the maximum number of candies among all the kids (max_candies).
2. Initialize an empty list result to store the boolean values.
3. Iterate through the candies list, and for each kid, check if their candies plus extraCandies is greater than or equal to max_candies.
4. If yes, append True to the result list.
5. If no, append False to the result list.
6. Return the result list.

### **Complexity**
Time Complexity:
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the candies list once, so the time complexity is linear with the number of kids.

Space Complexity:
$$ \mathcal{O}(n) $$ <br>
The algorithm creates a new list result with the same length as the input candies list. Therefore, the space complexity is linear with the number of kids.

<br><br><br>
Citation

- https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/

<br><br>
![Desktop View](/assets/img/whale/whale11.png){: w="300" h="300" }