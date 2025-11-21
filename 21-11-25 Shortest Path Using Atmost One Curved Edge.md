# 21-11-25
---
## Shortest Path Using Atmost One Curved Edge
Difficulty: HardAccuracy: 59.43%Submissions: 25K+Points: 8

<pre>

Given an undirected, connected graph with V vertices numbered from 0 to V-1 and E double-edges, represented as a 2D array edges[][]. Each double-edge is represented by a tuple (x, y, w1, w2), which indicates that there are two edges between vertices x and y: a straight edge with weight w1 and a curved edge with weight w2.

You are given two vertices a and b and you have to go from a to b through a series of edges such that in the entire path, you can use at most 1 curved edge. Your task is to find the shortest path from a to b satisfying the above condition.
If no such path exists that satisfies this restriction, return -1.

Note: It is guaranteed that the shortest path value will fit in a 32-bit integer.

Examples:

Input: V = 4, E = 4, a = 1, b = 3, edges[][] = [[0, 1, 1, 4], [0, 2, 2, 4], [0, 3, 3, 1], [1, 3, 6, 5]]

Output: 2
Explanation:
We can follow the path 1 -> 0 -> 3, this gives a distance of 1+3 = 4 if we follow all straight paths. But we can take the curved path  from 0 -> 3, which costs 1. This will result in a cost of 1 + 1 = 2.
Input: V = 2, E = 1, a = 0, b = 1, edges[][] = [[0, 1, 4, 1]]

Output: 1
Explanation:
Take the curved path from 0 to 1 which costs 1. 

Constraints:
1 ≤ V ≤ 106
0 ≤ E ≤ 106
0 ≤ a, b ≤ V - 1
0 ≤ edges[i][0], edges[i][1] ≤ V-1
0 ≤ edges[i][2], edges[i][3] ≤ 104
    
</pre>

---
```
class Solution:
    def shortestPath(self, V, a, b, edges):
        # code here 
        from collections import defaultdict
        from heapq import heappush, heappop
        
        g = defaultdict(list)
        for u, v, w, _ in edges:
            g[u].append((v, w))
            g[v].append((u, w))
            
        def dijkstra(src):
            nonlocal V
            INF = float('inf')
            dist = [INF] * V
            dist[src] = 0
            
            pq = [(0, src)]
            while pq:
                cost0, u = heappop(pq)
                if cost0 > dist[u]: 
                    continue
                
                for v, w in g[u]:
                    if dist[u]+w < dist[v]:
                        dist[v] = dist[u] + w
                        heappush(pq, (dist[v], v))
            return dist
        
        dist1 = dijkstra(a)
        dist2 = dijkstra(b)
        ans = dist1[b]
        
        for u, v, _, w in edges:
            ans = min(ans, dist1[u]+w+dist2[v]) # a -> u -> v -> b
            ans = min(ans, dist1[v]+w+dist2[u]) # b -> u -> v -> b
        return ans
        

        
```
---
