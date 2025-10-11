# 11-10-2025
---
## Maximum path sum
Difficulty: MediumAccuracy: 42.92%Submissions: 111K+Points: 4Average Time: 45m

<pre>


Given the root of a binary tree, your task is to find the maximum path sum. The path may start and end at any node in the tree.

Examples:

Input: root[] = [10, 2, 10, 20, 1, N, -25, N, N, N, N, 3, 4]
Output: 42
Explanation: Max path sum is represented using green colour nodes in the above binary tree.

Input: root[] = [-17, 11, 4, 20, -2, 10]
Output: 31
Explanation: Max path sum is represented using green colour nodes in the above binary tree.

Constraints:
1 ≤ number of nodes ≤ 103
-104 ≤ node->data ≤ 104



</pre>

---
```
'''
class Node:
    def __init__(self,val):
        self.data = val
        self.left = None
        self.right = None
'''

class Solution:
    def dfs(self,root,ans):
        if root:
            l=max(self.dfs(root.left,ans),0)
            r=max(self.dfs(root.right,ans),0)
            ans[0]=max(ans[0],root.data+l+r)
            return root.data+max(l,r)
        return 0
    
    def findMaxSum(self, root): 
        ans=[-float("inf")]
        self.dfs(root,ans)
        return ans[0]
        
```
---
