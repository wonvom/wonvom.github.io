---
title: LeetCode21 || Merge Two Sorted Lists | +
author: wonvom
date: 2023-04-25 9:30:00 -0800
categories: [Algorithm, LeetCode]
tags: [linked list, merge sorted lists, algorithm, python, recursion, leetcode, leetcode21]
math: true
pin: false
---

# Merge Two Sorted Lists

### **Problem**
You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

**Example 1**
```
Input: list1 = [1, 2, 4], list2 = [1, 3, 4]
Output: [1, 1, 2, 3, 4, 4]
```

**Example 2**
```
Input: list1 = [], list2 = []
Output: []
```

**Example 3**
```
Input: list1 = [], list2 = [0]
Output: [0]
```


### **Solution**
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if (not list1) or (list2 and list1.val > list2.val):
            list1, list2 = list2, list1

        if list1:
            list1.next = self.mergeTwoLists(list1.next, list2)

        return list1
```

Explain
Base case: if either list1 is None or if list2 is not None and the value of the head node in list1 is greater than the value of the head node in list2, swap the two lists.
If list1 is not None, set the next pointer of the head node in list1 to the result of the recursive call to mergeTwoLists() with the next node in list1 and the head node in list2 as arguments.
Return the head node of the merged linked list (which is now list1).
Complexity
Time Complexity:
$$ \mathcal{O}(n+m) $$ <br>
The algorithm iterates through both input linked lists once, so the time complexity is linear with the sum of the lengths of the input linked lists.

Space Complexity:
$$ \mathcal{O}(n+m) $$ <br>
The algorithm uses recursion which adds function calls to the call stack. In the worst case, the maximum depth of the recursion is equal to the sum of the lengths of the input linked lists. Therefore, the space complexity is linear with the sum of the lengths of the input linked lists.

<br><br><br>
Citation
- https://leetcode.com/problems/merge-two-sorted-lists/


<br><br>
![Desktop View](/assets/img/whale/whale8.png){: w="300" h="300" }