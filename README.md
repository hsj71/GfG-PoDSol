# 14-11-25
---
## Minimum Cost to Merge Stones
Difficulty: HardAccuracy: 71.64%Submissions: 7K+Points: 8Average Time: 45m
<pre>

Given an array stones[], where the ith element represents the number of stones in the ith pile.
In one move, you can merge exactly k consecutive piles into a single pile, and the cost of this move is equal to the total number of stones in these k piles.
Determine the minimum total cost required to merge all the piles into one single pile. If it is not possible to merge all piles into one according to the given rules, return -1.

Examples:

Input: stones[] = [1, 2, 3], k = 2
Output: 9
Explanation: Initially the array looks like [1, 2, 3].
First, we merge first 2 stones, i.e., 1 and 2, array becomes [3, 3] and cost is 1 + 2 = 3.
Then, we merge remaining stones, i.e., 3 and 3, array becomes [6] and the cost = 3 + 3 = 6.
Total cost = 3 + 6 = 9.
Input: stones[] = [1, 5, 3, 2, 4], k = 2
Output: 35
Explanation: Initially the array looks like [1, 5, 3, 2, 4].
First, we merge 1 and 5, array becomes [6, 3, 2, 4] and cost is 1 + 5 = 6.
Then, we merge 3 and 2, array becomes [6, 5, 4] and the cost = 3 + 2 = 5.
Then, we merge 5 and 4, array becomes [6, 9] and the cost = 5 + 4 = 9.
Finally, we merge 6 and 9, array becomes [15] and the cost = 6 + 9 = 15.
Total cost = 6 + 5 + 9 + 15 = 35.
Input: stones[] = [1, 5, 3, 2, 4], k = 4
Output: -1
Explanation: There is no possible way to combine the stones in piles of 4 to get 1 stone in the end.
Constraints:
1 ≤ stones.size() ≤ 30
2 ≤ k ≤ 30
1 ≤ stones[i] ≤ 100

    
</pre>

---
```
class Solution:
    def mergeStones(self, stones, k):
        n = len(stones)
        if (n - 1) % (k - 1) != 0:
            return -1

        # Prefix sum for quick range-sum queries
        pref = [0] * (n + 1)
        for i in range(n):
            pref[i + 1] = pref[i] + stones[i]

        def get_sum(l, r):
            return pref[r + 1] - pref[l]

        INF = 10**15
        
        # dp[i][j] = minimum cost to merge stones[i..j] into ( (j-i) % (k-1) + 1 ) piles
        dp = [[0] * n for _ in range(n)]

        # len is the segment length
        for length in range(k, n + 1):
            for i in range(n - length + 1):
                j = i + length - 1
                dp[i][j] = INF

                # Try merging subsegments
                for mid in range(i, j, k - 1):
                    dp[i][j] = min(dp[i][j], dp[i][mid] + dp[mid+1][j])

                # If this range can be merged into 1 pile, add the sum cost
                if (length - 1) % (k - 1) == 0:
                    dp[i][j] += get_sum(i, j)

        return dp[0][n-1]
        
```
---
