# 12-12-25
---
## Transpose of Matrix
Difficulty: EasyAccuracy: 66.5%Submissions: 122K+Points: 2Average Time: 20m
<pre>

You are given a square matrix of size n x n. Your task is to find the transpose of the given matrix.
The transpose of a matrix is obtained by converting all the rows to columns and all the columns to rows.

Examples :

Input: mat[][] = [[1, 1, 1, 1],
                [2, 2, 2, 2],
                [3, 3, 3, 3],
                [4, 4, 4, 4]]
Output: [[1, 2, 3, 4],
       [1, 2, 3, 4],
       [1, 2, 3, 4],
       [1, 2, 3, 4]]
Explanation: Converting rows into columns and columns into rows.
Input: mat[][] =  [[1, 2],
                 [9, -2]]
Output: [[1, 9],
        [2, -2]]
Explanation: Converting rows into columns and columns into rows.
Constraints:
1 ≤ n ≤ 103
-109 ≤ mat[i][j] ≤109



    
</pre>

---
```

class Solution:
    def transpose(self, mat):
        # code here
        r=[[mat[j][i] for j in range(len(mat))]for i in range(len(mat[0]))]
        return r
        
```
---
