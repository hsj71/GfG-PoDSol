# 14-10-2025
---
## Sum of Nodes in BST Range
Difficulty: MediumAccuracy: 85.12%Submissions: 7K+Points: 4
<pre>


Given the root of a Binary Search Tree and two integers l and r, the task is to find the sum of all nodes that lie between l and r, including both l and r.

Examples

Input: root = [22, 12, 30, 8, 20], l = 10, r = 22
     
Output: 54
Explanation: The nodes in the given Tree that lies in the range [10, 22] are {12, 20, 22}. Therefore, the sum of nodes is 12 + 20 + 22 = 54.
Input: root = [8, 5, 11, 3, 6, N, 20], l = 11, r = 15  
     
Output: 11
Explanation: The nodes in the given Tree that lies in the range [11, 15] is {11}. Therefore, the sum of node is 11.
Constraints:
0 ≤ number of nodes ≤ 104
0 ≤ node->data ≤ 104
0 ≤ l ≤ r ≤ 104

</pre>

---
"""
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
"""

class Solution:
    def inorder(self,root,l,r):
        if root:
            self.inorder(root.left,l,r)
            if l<=root.data<=r:
                self.ans+=root.data
            self.inorder(root.right,l,r)
    
    def nodeSum(self, root, l, r):
        self.ans=0
        self.inorder(root,l,r)
        return self.ans
        

        
```
---
