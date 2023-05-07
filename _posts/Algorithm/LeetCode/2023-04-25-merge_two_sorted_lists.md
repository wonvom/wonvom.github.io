---
title: LeetCode75 || 21. Merge Two Sorted Lists (Iterative) | +
author: wonvom
date: 2023-04-25 10:00:00 -0800
categories: [Algorithm, LeetCode]
tags: [linked list, merge sorted lists, algorithm, python, iterative, leetcode, leetcode21]
math: true
pin: false
---

# Merge Two Sorted Lists (Iterative)

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
        head = ListNode()
        current = head
        while list1 and list2:
            if list1.val < list2.val:
                current.next = list1
                list1 = list1.next
            else:
                current.next = list2
                list2 = list2.next
            current = current.next

        current.next = list1 or list2
        return head.next
```

### **Explain***
1. Create a new ListNode head, and set current to point to head.
Iterate through both linked lists until either list1 or list2 is empty.
2. If the value of the current node in list1 is less than the value of the current node in list2, point current.next to list1, and move list1 to the next node.
3. If the value of the current node in list1 is not less than the value of the current node in list2, point current.next to list2, and move list2 to the next node.
4. Move current to the next node.
5. After the iteration, set current.next to either list1 or list2, whichever is not empty.
6. Return the next node of the head ListNode.

### **Complexity**
Time Complexity:
$$ \mathcal{O}(n+m) $$ <br>
The algorithm iterates through both input linked lists once, so the time complexity is linear with the sum of the lengths of the input linked lists.

Space Complexity:
$$ \mathcal{O}(1) $$ <br>
The algorithm uses a constant amount of extra space for the sentinel node head. Therefore, the space complexity is constant.

<br><br><br>
Citation
- https://leetcode.com/problems/merge-two-sorted-lists/


<br><br>
![Desktop View](/assets/img/whale/whale8.png){: w="300" h="300" }