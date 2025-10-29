# 29-10-25
---
## Graph Diameter
Difficulty: MediumAccuracy: 72.38%Submissions: 7K+Points: 4

<pre>

You are given an undirected connected graph with V vertices numbered from 0 to V-1 and E edges, represented as a 2D array edges[][], where each element edges[i] = [u, v] represents an undirected edge between vertex u and vertex v.
Find the diameter of the graph.
The diameter of a graph (sometimes called the width) is the number of edges on the longest path between two vertices in the graph.

Note: Graph do not contains any cycle.

Examples :

Input: V = 6, E = 5, edges[][] = [[0, 1], [0, 4], [1, 3], [1, 2], [2, 5]]
    
Output: 4
Explanation: The longest path in the graph is from vertices 4 to vertices 5 (4 -> 0 -> 1 -> 2 -> 5).
Input: V = 7, E = 6, edges[][] = [[0, 2], [0, 4], [0, 3], [3, 1], [3, 5], [1, 6]]
    
Output: 4
Explanation: The longest path in the graph is from vertices 2 to vertices 6 (2 -> 0 -> 3 -> 1 -> 6).
Constraints:
2 ≤ V ≤  105
1 ≤ E ≤  V - 1
0 ≤ edges[i][0], edges[i][1] < V


    
</pre>

---
```
class Solution:
    def diameter(self, V, edges):
        from collections import defaultdict
        adj=defaultdict(set)
        for sta,sto in edges:
            adj[sta].add(sto)
            adj[sto].add(sta)
        ret=[0,-1]
        def dfs(cur=0,prv=None,dis=0):
            nonlocal adj,ret
            ret=max(ret,[dis,cur])
            for nxt in adj[cur]:
                if nxt==prv:
                    continue
                dfs(nxt,cur,dis+1)
        dfs()
        sta=ret[1]
        ret=[0,-1]
        dfs(sta)
        return ret[0]
        
```
---
