# 15-11-25
---
## Minimum Cost to Cut a Stick of length N
Difficulty: HardAccuracy: 78.81%Submissions: 5K+Points: 8
<pre>


You are given a wooden stick of length n, labeled from 0 to n. You are also given an integer array cuts[], where each element cuts[i] represents a position along the stick at which you can make a cut.
Each cut costs an amount equal to the length of the stick being cut at that moment. After performing a cut, the stick is divided into two smaller sticks.
You can perform the cuts in any order. Your task is to determine the minimum total cost required to perform all the cuts.

Example:

Input: n = 10, cuts[] = [2, 4, 7]
Output: 20
Explanation: 
    
If we cut the stick in the order [4, 2, 7], the cost will be 10 + 4 + 6 = 20, which is the minimum total cost.
Input: n = 8, cuts[] = [1, 6, 3, 5]
Output: 19
Explanation: If we cut the stick in the order [3, 6, 1, 5], the cost will be 8 + 5 + 3 + 3 = 19, which is the minimum total cost.
Constraints:
2 ≤ n ≤ 106
1 ≤ cuts[i] ≤ n - 1
1 ≤ cuts.size() ≤ 100

    
</pre>

---
```
class Solution:
    def minCutCost(self, n, cuts):
        cuts = [0] + sorted(cuts) + [n]
        m = len(cuts)

        dp = [[0] * m for _ in range(m)]

        for length in range(2, m):
            for i in range(m - length):
                j = i + length
                dp[i][j] = float("inf")
                for k in range(i + 1, j):
                    cost = dp[i][k] + dp[k][j] + (cuts[j] - cuts[i])
                    dp[i][j] = min(dp[i][j], cost)

        return dp[0][m - 1
        ]
        
```
---
