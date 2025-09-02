# 02-09-2025
---
## Swap Kth nodes from ends
Difficulty: MediumAccuracy: 35.5%Submissions: 75K+Points: 4Average Time: 45m
<pre>
Given the head of a singly linked list and an integer k. Swap the kth node (1-based index) from the beginning and the kth node from the end of the linked list. Return the head of the final formed list and if it's not possible to swap the nodes return the original list.

Examples:

Input: k = 1,
  
Output: 5 -> 2 -> 3 -> 4 -> 1
Explanation: Here k = 1, hence after swapping the 1st node from the beginning and end the new list will be 5 -> 2 -> 3 -> 4 -> 1.
  
Input: k = 2,
  
Output: 5 -> 9 -> 8 -> 5 -> 10 -> 3
Explanation: Here k = 2, hence after swapping the 2nd node from the beginning and end the new list will be 5 -> 9 -> 8 -> 5 -> 10 -> 3.
  
Constraints:
1 ≤ list size ≤ 104
1 ≤ node->data ≤ 106
1 ≤ k ≤ 104


</pre>

---
```
'''
class Node:
    def __init__(self, x):
        self.data = x
        self.next = None
'''
class Solution:
    def swapKth(self, head, k):
        # code here
        f=head
        s1=None
        s2=head
        for i in range(k):
            if i==k-1:
                s1=f
            if not f:
                return head
            f=f.next
        while f:
            s2=s2.next
            f=f.next
        s1.data, s2.data=s2.data, s1.data
        return head


```
---
