# 04-09-2025
---
## Linked List Group Reverse
Difficulty: HardAccuracy: 57.08%Submissions: 261K+Points: 8Average Time: 30m
<pre>
You are given the head of a Singly linked list. You have to reverse every k node in the linked list and return the head of the modified list.
Note: If the number of nodes is not a multiple of k then the left-out nodes at the end, should be considered as a group and must be reversed.

Examples:

Input: k = 2,
   
Output: 2 -> 1 -> 4 -> 3 -> 6 -> 5
Explanation: Linked List is reversed in a group of size k = 2.
   
Input: k = 4,
   
Output: 4 -> 3 -> 2 -> 1 -> 6 -> 5
Explanation: Linked List is reversed in a group of size k = 4.
   
Constraints:
1 ≤ size of linked list ≤ 105
0 ≤ node->data ≤ 106
1 ≤ k ≤ size of linked list 

</pre>

---
```
"""
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
"""

class Solution:
    def reverseKGroup(self, head, k):
        # Code here
        if k == 1:
            return head
    
        def rev(head):
            prev, node = None, head
            for i in range(k):
                node.next, node, prev = prev, node.next, node
                if node is None:
                    return prev
            head.next = rev(node)
            return prev
        
        return rev(head)


```
---
