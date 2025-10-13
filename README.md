# 13-10-2025
---
## Maximum Non-Adjacent Nodes Sum
Difficulty: MediumAccuracy: 55.35%Submissions: 97K+Points: 4Average Time: 45m
<pre>


Given the root of a binary tree with integer values. Your task is to select a subset of nodes such that the sum of their values is maximized, with the condition that no two selected nodes are directly connected that is, if a node is included in the subset, neither its parent nor its children can be included.

Examples:

Input: root = [11, 1, 2]

Output: 11
Explanation: The maximum sum is obtained by selecting the node 11.

Input: root = [1, 2, 3, 4, N, 5, 6]

Output: 16
Explanation: The maximum sum is obtained by selecting the nodes 1, 4, 5 and 6, which are not directly connected to each other. Their total sum is 16.  

Constraints:
1 ≤ number of nodes ≤ 104
1 ≤ node.data ≤ 105



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
    def getMaxSum(self, root):
        #code here
        def dfs(cur=root):
            if not cur:
                return 0,0
            li,le=dfs(cur.left)
            ri,re=dfs(cur.right)
            return cur.data+le+re,max(li+ri,li+re,le+ri,le+re)
        return max(dfs())
        
```
---
