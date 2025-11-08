# 08-11-25
---
## Number of paths in a matrix with k coins
Difficulty: MediumAccuracy: 16.96%Submissions: 63K+Points: 4

<pre>
  

You are given a matrix mat[][] of size n x m, where each of its cells contains some coins. Count the number of ways to collect exactly k coins while moving from the top left cell of the matrix to the bottom right cell.
From a cell (i, j), you can only move to cell (i+1, j) or (i, j+1).

Note: It is guaranteed that the answer will not exceed 32-bit integer limits.

Examples:

Input: k = 12, mat[] = [[1, 2, 3],
                      [4, 6, 5],
                      [3, 2, 1]]
Output: 2
Explanation: There are 2 possible paths with exactly 12 coins, (1 + 2 + 6 + 2 + 1) and (1 + 2 + 3 + 5 + 1).
Input: k = 16, mat[] = [[1, 2, 3], 
                      [4, 6, 5], 
                      [9, 8, 7]]
Output: 0 
Explanation: There are no possible paths that lead to sum = 16.
Constraints:
1 ≤ k ≤ 100
1 ≤ n, m ≤ 100
0 ≤ mat[i][j] ≤ 200
    
</pre>

---
```
class Solution:
    def numberOfPath(self, mat, k):
        # code here
        def f(i, j, s):
            if s > k:
                return 0
            if i == m-1 and j == n-1:
                s += mat[i][j]
                if s == k:
                    return 1
                return 0
            if i>=m or j>=n:
                return 0
            if (i, j, s) in dp:
                return dp[(i, j, s)]
            p1 = f(i+1, j, s+mat[i][j])
            p2 = f(i, j+1, s + mat[i][j])
            dp[(i, j, s)] = p1+p2
            return p1 + p2
        m, n = len(mat), len(mat[0])
        dp = {}
        return f(0,0,0)


        
```
---
