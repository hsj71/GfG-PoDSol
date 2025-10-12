# 12-10-2025
---
## Distribute Candies
Difficulty: HardAccuracy: 63.24%Submissions: 35K+Points: 8
<pre>



You are given the root of a binary tree with n nodes, where each node contains a certain number of candies, and the total number of candies across all nodes is n. In one move, you can select any two adjacent nodes and transfer one candy from one node to the other. The transfer can occur between a parent and child in either direction.

The task is to determine the minimum number of moves required to ensure that every node in the tree has exactly one candy.

Note: The testcases are framed such that it is always possible to achieve a configuration in which every node has exactly one candy, after some moves.

Examples:

Input: root = [5, 0, 0, N, N, 0, 0]
  
Output: 6
Explanation:
Move 1 candy from root to left child
Move 1 candy from root to right child
Move 1 candy from right child to root->right->left node
Move 1 candy from root to right child
Move 1 candy from right child to root->right->right node
Move 1 candy from root to right child
so, total 6 moves required.
Input: root = [2, 0, 0, N, N, 3, 0]
  
Output: 4
Explanation:
Move 1 candy from root to left child
Move 1 candy from root->right->left node to root->right node
Move 1 candy from root->right node to root->right->right node
Move 1 candy from root->right->left node to root->right node
so, total 4 moves required.
Constraints:
1 ≤ n ≤ 3*103
0 ≤ Node->data ≤ n
The sum of all Node->data = n



</pre>

---
```
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None


class Solution:
    def __init__(self):
        self.moves = 0  

    def distCandy(self, root):
        def dfs(node):
            if not node:
                return 0
            left_balance = dfs(node.left)
            right_balance = dfs(node.right)
            self.moves += abs(left_balance) + abs(right_balance)
            return node.data + left_balance + right_balance - 1

        dfs(root)
        return self.moves
        
```
---
