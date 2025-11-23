# 23-11-25
---
## Maximum Stone Removal
Difficulty: MediumAccuracy: 49.82%Submissions: 26K+Points: 4Average Time: 30m
<pre>

Given an 2D array of non-negative integers stones[][] where stones[i] = [xi , yi] represents the location of the ith stone on a 2D plane, the task is to return the maximum possible number of stones that you can remove.

A stone can be removed if it shares either the same row or the same column as another stone that has not been removed.

Note: Each coordinate point may have at most one stone.

Examples:

Input: stones[][] = [[0, 0], [0, 1], [1, 0], [1, 2], [2, 1], [2, 2]]
Output: 5
Explanation:
      
One way to remove 5 stones is as follows:
1. Remove stone [2, 2] because it shares the same row as [2, 1].
2. Remove stone [2, 1] because it shares the same column as [0, 1].
3. Remove stone [1, 2] because it shares the same row as [1, 0].
4. Remove stone [1, 0] because it shares the same column as [0, 0].
5. Remove stone [0, 1] because it shares the same row as [0, 0].
Stone [0, 0] cannot be removed since it does not share any row/column with another stone still on the plane.
Input: stones[][] = [[0, 0], [0, 2], [1, 1], [2, 0], [2, 2]]
Output: 3
Explanation:
     
One way to remove 3 stones is as follows:
1. Remove stone [2, 2] because it shares the same row as [2, 0].
2. Remove stone [2, 0] because it shares the same column as [0, 0].
3. Remove stone [0, 2] because it shares the same row as [0, 0].
Stones [0, 0] and [1, 1] cannot be removed since they do not share any row/column with another stone still on the plane.
Constraints:
1 ≤ stones.size() ≤ 1000
0 ≤ xi, yi ≤ 104
No two stones are at same position.
    
</pre>

---
```
class Solution:
    def maxRemove(self, stones):
        # Code here
        parent = {}
        rank = {}

        def find(u):
            # Path compression
            if parent[u] != u:
                parent[u] = find(parent[u])
            return parent[u]

        def union(u, v):
            # Initialize if not present
            if u not in parent:
                parent[u] = u
                rank[u] = 0
            if v not in parent:
                parent[v] = v
                rank[v] = 0

            pu, pv = find(u), find(v)
            if pu == pv:
                return
            # Union by rank
            if rank[pu] < rank[pv]:
                parent[pu] = pv
            elif rank[pu] > rank[pv]:
                parent[pv] = pu
            else:
                parent[pv] = pu
                rank[pu] += 1

        # Union row index with column index (using negative for column)
        for x, y in stones:
            union(x, ~y)   # use bitwise NOT (~y) instead of -y to avoid collision

        # Count distinct connected components
        unique_roots = {find(u) for u in parent}
        return len(stones) - len(unique_roots)

        
```
---
