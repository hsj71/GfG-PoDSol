# 09-11-25
---
## Chocolate Pickup II
Difficulty: HardAccuracy: 67.74%Submissions: 7K+Points: 8
<pre>
  
You are given a square matrix mat[][] of size n × n, where each cell represents either a blocked cell or a cell containing some chocolates. If mat[i][j] equals -1, then the cell is blocked and cannot be visited. Otherwise, mat[i][j] represents the number of chocolates present in that cell.
The task is to determine the maximum number of chocolates a robot can collected by starting from the top-left cell (0, 0), moving to the bottom-right cell (n-1, n-1), and then returning back to (0, 0).
While moving from (0, 0) to (n-1, n-1), the robot can move only in the right (i, j+1) or downward (i+1, j) directions. On the return journey from (n-1, n-1) to (0, 0), it can move only in the left (i, j-1) or upward (i-1, j) directions.

Note: After collecting chocolates from a cell (i, j), that cell becomes empty, meaning mat[i][j] becomes 0 for next visit. If there is no valid path from (0, 0) to (n-1, n-1) or for the return trip, the result should be 0.

Example:

Input: mat[][] = [[0, 1, -1], 
                [1, 1, -1], 
                [1, 1, 2]]
Output: 7
Explanation:
  
One of the optimal paths is to move from (0,0) -> (1,0) -> (2,0) -> (2,1) -> (2,2) while going forward, and then from (2,2) -> (2,1) -> (1,1) -> (0,1) -> (0,0) while coming back. The total number of chocolates collected is 7.
Input: mat[][] = [[1, 1, 0], 
               [1, 1, 1], 
               [0, 1, 1]]
Output: 7
Explanation:
  
One of the optimal paths is to move from (0,0) -> (1,0) -> (2,0) -> (2,1) -> (2,2) while going forward, and then from (2,2) -> (1,2) -> (1,1) -> (0,1) -> (0,0) while coming back. The total number of chocolates collected is 7.
Input: mat[][] = [[1, 0, -1],
                [2, -1, -1],
                [1, -1, 3]]
Output: 0
Explanation:
  
It is impossible to reach the bottom-right cell (2,2) from (0,0) because every route is blocked. Since the destination cannot be reached, the total chocolates collected is 0.
Constraint:
1 ≤ n ≤ 50
-1 ≤ mat[i][j] ≤ 100
    
</pre>

---
```
class Solution:
    def chocolatePickup(self, grid):
        from functools import lru_cache

        n = len(grid)
        m = len(grid[0])

        @lru_cache(None)
        def dp(r1, c1, c2):
            r2 = r1 + c1 - c2
            if r1 >= n or c1 >= m or r2 >= n or c2 >= m or grid[r1][c1] == -1 or grid[r2][c2] == -1:
                return float('-inf')

            if r1 == n - 1 and c1 == m - 1:
                return grid[r1][c1]

            res = grid[r1][c1]
            if (r1, c1) != (r2, c2):
                res += grid[r2][c2]

            res += max(
                dp(r1 + 1, c1, c2 + 1),  # down, right
                dp(r1, c1 + 1, c2 + 1),  # right, right
                dp(r1 + 1, c1, c2),      # down, down
                dp(r1, c1 + 1, c2)       # right, down
            )
            return res

        result = dp(0, 0, 0)
        return max(0, result)


        
```
---
