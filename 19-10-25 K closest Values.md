# 19-10-2025
---
## K closest Values
Difficulty: MediumAccuracy: 76.47%Submissions: 7K+Points: 4

<pre>


Given the root of a Binary Search Tree, a target value, and an integer k. Your task is to find the k values in the BST that are closest to the target.

The closest value is taken by choosing the one that gives minimum absolute difference from target.

Note: In case two values have same absolute difference from target, choose the smaller one. The target may or may not be present in BST.
You can return the values in any order the driver code will print them in sorted order only.

Examples:

Input: root = [20, 8, 22, 4, 12, N, N, N, N, 10, 14], target = 17, k = 3
     
Output: [14, 20, 12]
Explanation: Absolute difference of 17 wrt 14 and 20 is 3 and 3, but we choose the smaller value in case of same absolute difference. So, 14 coes first and then 20. Then, 12 and 22 have same absolute difference, i.e., 5 from 17. But we choose the smaller value, i.e., 12.
     
Input: root = [5, 4, 8, 1], target = 5, k = 2
     
Output: [5, 4]
Explanation: The absolute difference of 5 wrt 5 is 0, and for 4, the absolute difference is 1.
    
Constraints:
1 ≤ number of nodes, k ≤ 104
1 ≤ node->data, target ≤ 104




</pre>

---
```
from collections import deque
class Solution:
    def inorder(self,root,dq):
        if root:
            self.inorder(root.left,dq)
            if len(dq)<self.k:
                dq.append(root.data)
            else:
                if self.target-dq[0]>root.data-self.target:
                    dq.popleft()
                    dq.append(root.data)
                else:
                    return
            self.inorder(root.right,dq)
    
    def getKClosest(self, root, target, k):
        self.k=k
        self.target=target
        dq=deque()
        self.inorder(root,dq)
        return list(dq)

        
```
---
