# 07-09-2025
---
## Merge K sorted linked lists
Difficulty: MediumAccuracy: 57.01%Submissions: 117K+Points: 4Average Time: 60m
<pre>
Given an array arr[] of n sorted linked lists of different sizes. Your task is to merge all these lists into a single sorted linked list and return the head of the merged list.

Examples:

Input:
   
Output: 1 -> 2 -> 3 -> 4 -> 7 -> 8 -> 9
Explanation: The arr[] has 3 sorted linked list of size 3, 3, 1.
1st list: 1 -> 3 -> 7
2nd list: 2 -> 4 -> 8
3rd list: 9
The merged list will be: 
    
Input:
   
Output: 1 -> 3 -> 4 -> 5 -> 6 -> 8
Explanation: The arr[] has 3 sorted linked list of size 2, 1, 3.
1st list: 1 -> 3
2nd list: 8
3rd list: 4 -> 5 -> 6
The merged list will be: 
    
Constraints
1 ≤ total no. of nodes ≤ 105
1 ≤ node->data ≤ 103
</pre>

---
```
'''
class Node:
    def _init_(self, x):
        self.data = x
        self.next = None
'''

class Solution:
    def mergeKLists(self, arr):
        # code here
        import heapq
        
        h=[(d.data,i,) for i,d in enumerate(arr)]
        heapq.heapify(h)
        m=Node(-1)
        cur=m
        while h:
            o,x=heapq.heappop(h)
            cur.next=arr[x]
            cur=cur.next
            arr[x]=arr[x].next
            if arr[x]:
                heapq.heappush(h,(arr[x].data,x,))
        return m.next


```
---
