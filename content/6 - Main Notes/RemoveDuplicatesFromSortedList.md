---
title: Remove Duplicates From a Sorted List
tags:
  - explorerexclude
publish: "true"
---
File Created: 2026-01-07 12:39  
Last Modified: 2026-01-07 12:39

Tags: [[LeetCode]]

---

**Problem Description:** The problem is conceptually simple. Given some sorted [[Linked Lists|linked list]] with root node `head`, remove all duplicate values and return the cut-down linked list.  

The constraints are:  

- The number of nodes in the list is in the range `[0, 300]`.
- `-100 <= Node.val <= 100`
- The list is guaranteed to be **sorted** in ascending order.

---

**Examples:**    

**Example 1:**  
![[file-20260107124140585.png]]  
**Input:** head = \[1,1,2\]
**Output:** \[1,2\]

**Example 2:**  

![[file-20260107124150353.png]]  
**Input:** head = \[1,1,2,3,3\]
**Output:** \[1,2,3\]

---

**Solution:**  Like I mentioned above, this problem is conceptually pretty simple. We can keep track of our current node, and with it all of its value and the node that it points, and carefully move through the list, comparing values to our current node value, and removing them if they are equal. If we come across a node with a different value, then we know there must not exist any more duplicates, given that this is a sorted list, and thus we can move onto the next node to purge of its duplicates. 

Below is the implementation in Python.  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        #if list not empty, lol
        if head:
            #initialize variables
            curr = head.val
            curr_node = head
            #while we are not at the end of the list
            while curr_node.next != None:
                #assign variable to next ListNode
                next = curr_node.next
                #if duplicate, assign .next value to following ListNode
                if (next.val == curr):
                    curr_node.next = next.next
                #if not, move down the list
                else:
                    curr = next.val
                    curr_node = next
        return head
```

Thanks for reading! Please email me any comments or suggestions at [brianoeaden@gmail.com](mailto:brianoeaden@gmail.com) :)