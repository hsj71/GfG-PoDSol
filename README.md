# 17-10-2025
---
## BST to greater sum tree
Difficulty: MediumAccuracy: 66.73%Submissions: 23K+Points: 4

<pre>


Given the root of a  BST with unique node values, transform it into greater sum tree where each node contains sum of all nodes greater than that node.

Examples:

Input: root = [11, 2, 29, 1, 7, 15, 40, N, N, N, N, N, N, 35, N]
      
Output: [119, 137, 75, 139, 130, 104, 0, N, N, N, N, N, N, 40, N]
Explanation: Every node is replaced with the sum of nodes greater than itself. 
      
Input: root = [2, 1, 6, N, N, 3, 7]
     
Output: [16, 18, 7, N, N, 13, 0]
Explanation: Every node is replaced with the sum of nodes greater than itself. 
     
Constraints :
1 ≤ node->data ≤ 3*104
1 ≤ number of nodes ≤ 3*104



</pre>

---
```
class Solution:
    def transformTree(self, root):
        sm=0
        def dfs(cur=root):
            nonlocal sm
            if not cur:
                return 0
            dfs(cur.right)
            cur.data,sm=sm,sm+cur.data
            dfs(cur.left)
        dfs()
        return root
        
```
---
