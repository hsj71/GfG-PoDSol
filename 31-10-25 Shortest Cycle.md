# 31-10-25
---
## Shortest Cycle
Difficulty: HardAccuracy: 71.19%Submissions: 7K+Points: 8

<pre>

You are given an undirected graph with V vertices numbered from 0 to V-1 and E edges, represented as a 2D array edges[][], where each element edges[i] = [u, v] represents an undirected edge between vertex u and v.
Find the length of the shortest cycle in the graph. If the graph does not contain any cycle, return -1.


Note: A cycle is a path that starts and ends at the same vertex without repeating any edge or vertex (except the start/end vertex). The shortest cycle is the one with the minimum number of edges.

Examples

Input: V = 7, E = 8, edges[][] = [[0, 5], [0, 6], [5, 1], [6, 1], [6, 2], [2, 3], [3, 4], [1, 4]]

Output: 4
Explanation: Possible cycles are: 
0 → 5 → 1 → 6 → 0 (length = 4)
1 → 4 → 3 → 2 → 6 → 1 (length = 5)
The smallest one is 0 → 5 → 1 → 6 → 0, with length 4. 
Input: V = 7, E = 9, edges[][] = [[0, 5], [0, 6], [1, 2], [1, 4], [1, 5], [1, 6], [2, 6], [2, 3], [3, 4]]

Output: 3
Explanation: Possible cycles include:
1 → 2 → 6 → 1 (length = 3)
1 → 2 → 3 → 4 → 1 (length = 4)
0 → 5 → 1 → 6 → 0 (length = 4)
The smallest one is 1 → 2 → 6 → 1, with length 3.
Constraints:
1 ≤ V ≤ 103
0 ≤ E ≤ 103
0 ≤ edges[i][0], edges[i][1] < V

    
</pre>

---
```
from collections import deque
class Solution:
    
    def shortCycle(self, V, edges):
        adj=[[] for _ in range(V)]
        for u,v in edges:
            adj[u].append(v)
            adj[v].append(u)
        ans=float("inf")
        for start in range(V):
            dist=[-1]*V
            parent=[-1]*V
            q=deque([start])
            dist[start]=0
            while q:
                u=q.popleft()
                for v in adj[u]:
                    if dist[v]==-1:
                        q.append(v)
                        dist[v]=dist[u]+1
                        parent[v]=u
                    elif parent[u]!=v:
                        ans=min(ans,dist[v]+dist[u]+1)
        return ans if ans!=float("inf") else -1
        
```
---
