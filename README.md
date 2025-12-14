# 14-12-25
---
## 2D Submatrix Sum Queries
Difficulty: MediumAccuracy: 69.18%Submissions: 7K+Points: 4Average Time: 20m
<pre>


Given a 2D integer matrix mat[][] and a list of queries queries[][], your task is to answer a series of submatrix sum queries.

Each query is represented as a list [r1, c1, r2, c2], where:

(r1, c1) is the top-left coordinate of the submatrix
(r2, c2) is the bottom-right coordinate of the submatrix (both inclusive)
Your task is to return a list of integers, the sum of elements within the specified submatrix for each query.

Examples: 

Input: mat[][] = [[1, 2, 3], queries[][] = [[0, 0, 1, 1], [1, 0, 2, 2]]
                [1, 1, 0],
                [4, 2, 2]]
Output: [5, 10]
Explanation: 
Query 1 selects submatrix [[1, 2], [1, 1]] → sum = 5.
Query 2 selects submatrix [[1, 1, 0], [4, 2, 2]] → sum = 10.
Input: mat[][] = [[1, 1, 1], queries[][] = [[1, 1, 2, 2], [0, 0, 2, 2], [0, 2, 2, 2]]
                [1, 1, 1],
                [1, 1, 1]]
Output: [4, 9, 3]
Explanation: 
Query 1 selects submatrix [[1, 1], [1, 1]] → sum = 4.
Query 2 selects submatrix [[1, 1, 1], [1, 1, 1], [1, 1, 1]] → sum = 9.
Query 3 selects submatrix [[1], [1], [1]] → sum = 3.
Constraints:
1 ≤ n × m, q ≤ 105
0 ≤ mat[i][j] ≤ 104
0 ≤ r1 ≤ r2 ≤ n - 1
0 ≤ c1 ≤ c2 ≤ m - 1

    
</pre>

---
```

class Solution:
    def prefixSum2D(self, mat, queries):
        # code here 
        m, n = len(mat), len(mat[0])
        dp = [[0]*(n+1) for _ in range(m+1)]
        
        for r in range(m):
            for c in range(n):
                dp[r+1][c+1] = dp[r+1][c] + dp[r][c+1] - dp[r][c] + mat[r][c]
        
        ans = []
        for r1, c1, r2, c2 in queries:
            v = dp[r2+1][c2+1] - dp[r2+1][c1] - dp[r1][c2+1] + dp[r1][c1]
            ans.append(v)
        return ans

        
```
---
