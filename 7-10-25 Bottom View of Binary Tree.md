# 7-10-2025
---
## Bottom View of Binary Tree
Difficulty: MediumAccuracy: 54.18%Submissions: 330K+Points: 4Average Time: 45m

<pre>


You are given the root of a binary tree, and your task is to return its bottom view. The bottom view of a binary tree is the set of nodes visible when the tree is viewed from the bottom.

Note: If there are multiple bottom-most nodes for a horizontal distance from the root, then the latter one in the level order traversal is considered.

Examples :

Input: root = [1, 2, 3, 4, 5, N, 6]
    
Output: [4, 2, 5, 3, 6]
Explanation: The Green nodes represent the bottom view of below binary tree.
    
Input: root = [20, 8, 22, 5, 3, 4, 25, N, N, 10, 14, N, N, 28, N]
    
Output: [5, 10, 4, 28, 25]
Explanation: The Green nodes represent the bottom view of below binary tree.
    
Constraints:
1 ≤ number of nodes ≤ 105
1 ≤ node->data ≤ 105



</pre>

---
```
class Solution:
    def __init__(self):
        self.map = {}

    def traverse(self, root, val = 0, depth = 0):
        if val not in self.map or self.map[val][0] <= depth:
            self.map[val] = (depth, root.data)
        
        if root.left:
            self.traverse(root.left, val - 1, depth + 1)
            
        if root.right:
            self.traverse(root.right, val + 1, depth + 1)
        
    def bottomView(self, root):
        # code here
        res = []
        self.traverse(root)
        for k in sorted(self.map):
            res.append(self.map[k][1])
        return res
        
        
```
---
