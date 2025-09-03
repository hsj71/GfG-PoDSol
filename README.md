# 03-09-2025
---
## Reverse a Doubly Linked List
Difficulty: EasyAccuracy: 70.38%Submissions: 198K+Points: 2Average Time: 15m
<pre>
You are given the head of a doubly linked list. You have to reverse the doubly linked list and return its head.

Examples:

Input:
   
Output: 5 <-> 4 <-> 3
Explanation: After reversing the given doubly linked list the new list will be 5 <-> 4 <-> 3.
   
Input: 
   
Output: 196 <-> 59 <-> 122 <-> 75
Explanation: After reversing the given doubly linked list the new list will be 196 <-> 59 <-> 122 <-> 75.
   
Constraints:
1 ≤ number of nodes ≤ 106
0 ≤ node->data ≤ 104

</pre>

---
```
"""
class Node:
    def __init__(self, val):
        self.data = val
        self.next = None
        self.prev = None
"""

class Solution:
    def reverse(self, head):
        # code here
        while head:
            head.next, head.prev = head.prev, head.next
            if not head.prev:return head
            head=head.prev
        


```
---
