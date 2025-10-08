# 8-10-2025
---
## Construct Tree from Preorder & Postorder
Difficulty: MediumAccuracy: 81.11%Submissions: 6K+Points: 4

<pre>



Given two arrays pre[] and post[] that represent the preorder and postorder traversals of a full binary tree. Your task is to construct the binary tree and return its root.

Note:  Full Binary Tree is a binary tree where every node has either 0 or 2 children. The preorder and postorder traversals contain unique values, and every value present in the preorder traversal is also found in the postorder traversal.

Examples:

Input: pre[] = [1, 2, 4, 8, 9, 5, 3, 6, 7], post[] = [8, 9, 4, 5, 2, 6, 7, 3, 1]
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
Explanation: The tree will look like
   
Input: pre[] = [1, 2, 4, 5, 3, 6, 7] , post[] = [4, 5, 2, 6, 7, 3, 1]
Output: [1, 2, 3, 4, 5, 6, 7]
Explanation: The tree will look like
   
Constraints:
1 ≤ number of nodes ≤ 103
1 ≤ pre[i], post[i] ≤ 104



</pre>

---
```
class Solution:
    def constructTree(self, pre, post):
        # code here
        n = len(pre)
        mpp = {val: i for i,val in enumerate(post)}
        pre_ind = 0
        
        def build(l,r):
            nonlocal pre_ind
            if l > r or pre_ind >= n:
                return None
            
            root = Node(pre[pre_ind])
            pre_ind += 1
            
            if l == r or pre_ind >= n :
                return root
            
            left_val = pre[pre_ind]
            
            mid = mpp[left_val]
            
            root.left = build(l,mid)
            root.right = build(mid+1,r-1)
            return root
        return build(0,n-1)
        
```
---
