# 08-09-2025
---
## Merge Sort for Linked List
Difficulty: MediumAccuracy: 74.76%Submissions: 85K+Points: 4Average Time: 30m
<pre>
You are given the head of a linked list. You have to sort the given linked list using Merge Sort.

Examples:

Input:
    
Output: 10 -> 20 -> 30 -> 40 -> 50 -> 60
Explanation: After sorting the given linked list, the resultant list will be:
    
Input:
    
Output: 2 -> 5 -> 8 -> 9
Explanation: After sorting the given linked list, the resultant list will be:
    
Constraints:
1 ≤ number of nodes ≤ 105
0 ≤ node->data ≤ 106
</pre>

---
```
'''
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
'''

class Solution:
    def mergeSort(self, head):
        # code here
        i=[]
        new=head
        while new:
            i.append(new.data)
            new=new.next
        i.sort()    
        current=head
        for J in i:
            current.data=J
            current=current.next
        return head
        
---
