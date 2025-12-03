# 3-12-25
---
## Travelling Salesman Problem
Difficulty: HardAccuracy: 46.35%Submissions: 36K+Points: 8Average Time: 25m
<pre>


Given a 2d matrix cost[][] of size n where cost[i][j] denotes the cost of moving from city i to city j. Your task is to complete a tour from city 0 (0-based index) to all other cities such that you visit each city exactly once and then at the end come back to city 0 at minimum cost.

Examples:

Input: cost[][] = [[0, 111], 
                [112, 0]]
Output: 223
Explanation: We can visit 0->1->0 and cost = 111 + 112.
Input: cost[][] = [[0, 1000, 5000],
                [5000, 0, 1000],
                [1000, 5000, 0]]
Output: 3000
Explanation: We can visit 0->1->2->0 and cost = 1000 + 1000 + 1000 = 3000
Constraints:
1 ≤ cost.size() ≤ 15
0 ≤ cost[i][j] ≤ 104
    
</pre>

---
```
class Solution:
	def tsp(self, cost):
        from functools import cache
        MAX_COST = 15 * 10**4
        n = len(cost)
        all_visited_mask = (1 << n) - 1
        
        @cache
        def dfs(u=0, visited_mask=1):
            if visited_mask == all_visited_mask:
                # All visited, returning to city "0"
                return cost[u][0]
            min_cost = MAX_COST
            for v in range(1, n):
                v_mask = 1 << v
                if visited_mask & v_mask == 0:
                    v_cost = dfs(v, visited_mask | v_mask) + cost[u][v]
                    if v_cost < min_cost:
                        min_cost = v_cost
            return min_cost
        
        return dfs()	
        
```
---
