# 10-10-2025
---
## ZigZag Tree Traversal
Difficulty: MediumAccuracy: 54.05%Submissions: 185K+Points: 4Average Time: 30m

<pre>

Given the root of a binary tree. You have to find the zig-zag level order traversal of the binary tree.
Note: In zig zag traversal we traverse the nodes from left to right for odd-numbered levels, and from right to left for even-numbered levels.

Examples:

Input: root = [1, 2, 3, 4, 5, 6, 7]
          
Output: [1, 3, 2, 4, 5, 6, 7]
Explanation:
Level 1 (left to right): [1]
Level 2 (right to left): [3, 2]
Level 3 (left to right): [4, 5, 6, 7]
Final result: [1, 3, 2, 4, 5, 6, 7]
Input: root = [7, 9, 7, 8, 8, 6, N, 10, 9]
 
Output: [7, 7, 9, 8, 8, 6, 9, 10] 
Explanation:
Level 1 (left to right): [7]
Level 2 (right to left): [7, 9]
Level 3 (left to right): [8, 8, 6]
Level 4 (right to left): [9, 10]
Final result: [7, 7, 9, 8, 8, 6, 9, 10]
Constraints:
1 ≤ number of nodes ≤ 105
1 ≤ node->data ≤ 105




</pre>

---
```
'''
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
'''

class Solution:
    def zigZagTraversal(self, root):
        # code here
        ret=[]
        lvl=0
        q=[root]
        while q:
            tmp=[]
            nq=[]
            for cur in q:
                if cur==None:
                    continue
                tmp.append(cur.data)
                nq.extend([cur.left,cur.right])
            lvl+=1
            if lvl%2==1:
                ret.extend(tmp)
            else:
                ret.extend(tmp[::-1])
            q=nq
        return ret
        
```
---
