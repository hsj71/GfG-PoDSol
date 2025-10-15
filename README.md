# 15-10-2025
---
## k-th Smallest in BST
Difficulty: MediumAccuracy: 43.53%Submissions: 152K+Points: 4Average Time: 40m
<pre>


Given the root of a BST and an integer k, the task is to find the kth smallest element in the BST. If there is no kth smallest element present then return -1.

Examples:

Input: root = [20, 8, 22, 4, 12, N, N, N, N, 10, 14], k = 3
    
Output: 10
Explanation: 10 is the 3rd smallest element in the BST.
Input: root = [2, 1, 3], k = 5
    
Output: -1
Explanation: There is no 5th smallest element in the BST as the size of BST is 3.
Constraints:
1 ≤ number of nodes, k ≤ 104
1 ≤ node->data ≤ 104



</pre>

---
'''
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
'''

class Solution:
    def __init__(self):
        self.ans = -1
        self.k = None
        
    def InOrderTraversal(self, root):
        if root == None:
            return
        
        self.InOrderTraversal(root.left)
        self.k -= 1
        if self.k == 0:
            self.ans = root.data
            raise Exception()
            
        self.InOrderTraversal(root.right)
        
    def kthSmallest(self, root, k):
        self.k = k
        try:
            self.InOrderTraversal(root)
        except Exception:
            pass
        return self.ans
        

        
```
---
