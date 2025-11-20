# 20-11-25
---
## Make Strings Equal
Difficulty: MediumAccuracy: 64.4%Submissions: 8K+Points: 4
<pre>


Given two strings s and t, consisting of lowercase English letters. You are also given, a 2D array transform[][], where each entry [x, y] means that you are allowed to transform character x into character y and an array cost[], where cost[i] is the cost of transforming transform[i][0] into transform[i][1]. You can apply any transformation any number of times on either string.

Your task is to find the minimum total cost required to make the strings identical. If it is impossible to make the two strings identical using the available transformations, return -1.

Examples:

Input: s = "abcc", t = "bccc", transform[][] = [['a', 'b'], ['b', 'c'], ['c', 'a']], cost[] = [2, 1, 4]
Output: 3
Explanation: We can convert both strings into "bccc" with a cost of 3 using these operations:
transform at Position 0 in s: a -> b (cost 2)
transform at Position 1 in s: b -> c (cost 1)
Other characters already match.
Input: s = "az", t = "dc", transform[][] = [['a', 'b'], ['b', 'c'], ['c', 'd'], ['a', 'd'], ['z', 'c']], cost[] = [5, 3, 2, 50, 10]
Output: 20
Explanation: We can convert both strings into "dc" with a cost of 20 using these operations:
transform at Position 0 in s: a -> d by path a -> b -> c -> d (cost 5 + 3 + 2 = 10)
transform at Position 1 in s: z -> c (cost 10)
Input: s = "xyz", t = "xzy", transform[][] = [['x', 'y'], ['x', 'z']], cost[] = [3, 3]
Output: -1
Explanation: It is not possible to make the two strings equal.
Constraints:
1 ≤ s.size() = t.size() ≤ 105
1 ≤ transform.size() = cost.size() ≤ 500
'a' ≤ transform[i][0], transform[i][1] ≤ 'z'
1 ≤ cost[i] ≤ 500
    
</pre>

---
```
class Solution:
    def minCost(self, s, t, transform, cost):
        # code here
        INF = 10**12
        dist = [[INF] * 26 for _ in range(26)]
        
        for i in range(26):
            dist[i][i] = 0
        for i, (x, y) in enumerate(transform):
            u = ord(x) - ord('a')
            v = ord(y) - ord('a')
            dist[u][v] = min(dist[u][v], cost[i])
        for k in range(26):
            for i in range(26):
                if dist[i][k] == INF:
                    continue
                for j in range(26):
                    if dist[k][j] == INF:
                        continue
                    if dist[i][j] > dist[i][k] + dist[k][j]:
                        dist[i][j] = dist[i][k] + dist[k][j]
        ans = 0
        for i in range(len(s)):
            a = ord(s[i]) - ord('a')
            b = ord(t[i]) - ord('a')
            if a == b:
                continue
            best = INF
            for c in range(26):
                if dist[a][c] < INF and dist[b][c] < INF:
                    best = min(best, dist[a][c] + dist[b][c])
            if best == INF:
                return -1
            ans += best
        return ans
        

        
```
---
