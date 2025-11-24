# 24-11-25
---
## Second Best Minimum Spanning Tree
Difficulty: MediumAccuracy: 61.32%Submissions: 8K+Points: 4

<pre>


Given an undirected graph of V vertices numbered from (0 to V-1) and E edges represented by a 2D array edges[][], where each edges[i] contains three integers [u, v, w], representing an undirected edge from u to v, having weight w.
Your task is to find the weight of the second best minimum spanning tree of the given graph.
A second best MST is defined as the minimum-weight spanning tree whose total weight is strictly greater than the weight of the minimum spanning tree.

Note: If no such second best MST exists, return -1. 

Examples:

Input: V = 5, E = 7, edges[][] = [[0, 1, 4], [0, 2, 3], [1, 2, 1], [1, 3, 5], [2, 4, 10], [2, 3, 7], [3, 4, 2]]
Output: 12
Explanation: Graph through red edges represents MST.
   
Input: V = 5, E = 4, edges[][] = [[0, 1, 2], [1, 2, 3], [2, 3, 4], [3, 4, 5]] 
Output: -1
Explanation: No second best MST exists for this graph.
   
Constraints:
1 ≤ V ≤ 100
V-1 ≤ E ≤ V*(V-1)/2
0 ≤ edges[i][2] ≤ 103
    
</pre>

---
```
class Solution:
    def secondMST(self, V, edges):
        # code here
        def find(i, parent):
            if parent[i] != i:
                parent[i] = find(parent[i], parent)
            return parent[i]
        
        edges.sort(key=lambda x: x[2])
        

        def mst_tree(forbidden=set()):
            nonlocal edges, V
            parent = [i for i in range(V)]
            rank = [0]*V

            cost0 = 0
            mst = []
            
            for u, v, w in edges:
                if len(mst) == V-1:
                    break
                if (u, v) in forbidden:
                    continue
                
                r1 = find(u, parent)
                r2 = find(v, parent)
                if r1 == r2:
                    continue
                mst.append((u, v))
                cost0 += w
                if rank[r1] == rank[r2]:
                    parent[r2] = r1
                    rank[r1] += 1
                elif rank[r1] > rank[r2]:
                    parent[r2] = r1
                else:
                    parent[r1] = r2
            return mst, cost0
        mst, cost0 = mst_tree()

        ans = float('inf')
        for e in mst:
            m, c = mst_tree({e})
            if len(m) != V-1:
                continue
            if c > cost0:
                ans = min(ans, c)
        return ans if ans != float('inf') else -1
        
        
```
---
