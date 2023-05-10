---
title: LeetCode75 || 605. Can Place Flowers | +
author: wonvom
date: 2023-04-29 13:30:00 -0800
categories: [Algorithm, LeetCode]
tags: [array, algorithm, python, leetcode, leetcode605]
math: false
pin: false
---

# Can Place Flowers

### **Problem**
You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return true if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and false otherwise.

**Example 1**
```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
```

**Example 2**
```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: false
```


### **Solution**
```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        if n == 0:
            return True

        flowerbed = [0] + flowerbed + [0]
        available_slots = 0

        for i in range(1, len(flowerbed) - 1):
            if flowerbed[i - 1] == 0 and flowerbed[i] == 0 and flowerbed[i + 1] == 0:
                flowerbed[i] = 1
                available_slots += 1

                if available_slots >= n:
                    return True

        return False
```

### **Explain**
1. If n is 0, return True since no new flowers need to be planted.
2. Add 0 to the beginning and end of the flowerbed list to simplify checking edge cases.
3. Initialize available_slots to 0, which will count the available spots to plant flowers.
4. Iterate through the flowerbed list, starting from index 1 and ending at the second-to-last element.
5. Check if the current slot and its adjacent slots are empty (0), and if so, plant a flower (set the current element to 1) and increment available_slots.
6. If available_slots is greater than or equal to n, return True.
7. If the loop completes without finding enough available slots, return False.

### **Complexity**
Time Complexity:
$$ \mathcal{O}(n) $$ <br>
The algorithm iterates through the flowerbed list once, so the time complexity is linear with the number of elements in the flowerbed.

Space Complexity:
$$ \mathcal{O}(1) $$ <br>
The algorithm creates a modified flowerbed list, but the additional space needed for this operation is constant, making the space complexity constant.

<br><br><br>
Citation

- https://leetcode.com/problems/can-place-flowers/

<br><br>
![Desktop View](/assets/img/whale/whale12.png){: w="300" h="300" }