# 18-10-2025
---
## Median of BST
Difficulty: MediumAccuracy: 27.43%Submissions: 106K+Points: 4

<pre>


You are given the root of a Binary Search Tree, find the median of it. 

Let the nodes of the BST, when written in ascending order (inorder traversal), be represented as V1, V2, V3, …, Vn, where n is the total number of nodes in the BST.

If number of nodes are even: return V(n/2)
If number of nodes are odd: return V((n+1)/2)
Examples:

Input: root = [20, 8, 22, 4, 12, N, N, N, N, 10, 14]
2
Output: 12
Explanation: The inorder of given BST is 4, 8, 10, 12, 14, 20, 22. Here, n = 7, so, here median will be ((7+1)/2)th value, i.e., 4th value, i.e, 12.
Input: root = [5, 4, 8, 1]
1 
Output: 4
Explanation: The inorder of given BST is 1, 4, 5, 8. Here, n = 4(even), so, here median will be (4/2)th value, i.e., 2nd value, i.e, 4.
Constraints:
1 ≤ number of nodes ≤ 105
1 ≤ node.data ≤  105




</pre>

---
```
class Solution:
    def findMedian(self, root):
        def inorder(node, arr):
            if not node:
                return
            inorder(node.left, arr)
            arr.append(node.data)
            inorder(node.right, arr)
        
        arr = []
        inorder(root, arr)
        n = len(arr)
        
        # For 1-based indexing in the problem statement
        if n % 2 == 1:
            return arr[n // 2]   # (n+1)/2 (1-based) → n//2 (0-based)
        else:
            return arr[(n // 2) - 1]  # V(n/2) (1-based) → (n//2 - 1) (0-based)


        
```
---
