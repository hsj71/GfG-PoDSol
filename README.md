# 19-11-25
---
## Path With Minimum Effort
Difficulty: MediumAccuracy: 53.13%Submissions: 59K+Points: 4Average Time: 25m
<pre>


You are given a 2D array mat[][], of size n*m. Your task is to find the minimum possible path cost from the top-left cell (0, 0) to the bottom-right cell (n-1, m-1) by moving up, down, left, or right between adjacent cells.

Note: The cost of a path is defined as the maximum absolute difference between the values of any two consecutive cells along that path.

Examples:

Input: mat[][] = [[7, 2, 6, 5],
               [3, 1, 10, 8]]
Output: 4
Explanation: The route of [7, 3, 1, 2, 6, 5, 8] has a minimum value of maximum absolute difference between any two consecutive cells in the route, i.e., 4.
   
Input: mat[][] = [[2, 2, 2, 1],
               [8, 1, 2, 7],
               [2, 2, 2, 8],
               [2, 1, 4, 7],
               [2, 2, 2, 2]]
Output: 0
Explanation: The route of [2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2] has a minimum value of maximum absolute difference between any two consecutive cells in the route, i.e., 0.
    
Constraints:
1 ≤ n, m ≤ 100
0 ≤ mat[i][j] ≤ 106
    
</pre>

---
```
class Solution:
    def minCostPath(self, mat):
        # code here
        hth=len(mat)
        wth=len(mat[0])
        tots=[[float('inf')]*wth for _ in range(hth)]
        import heapq
        hp=[(0,0,0,)]
        tots[0][0]=0
        while hp:
            tot,x,y=heapq.heappop(hp)
            if (x,y)==(wth-1,hth-1):
                return tot
            for dx,dy in [(0,1,),(0,-1,),(1,0,),(-1,0,),]:
                nx,ny=x+dx,y+dy
                if not 0<=nx<wth or not 0<=ny<hth:
                    continue
                cos=abs(mat[ny][nx]-mat[y][x])
                ntot=max(tot,cos)
                if ntot<tots[ny][nx]:
                    tots[ny][nx]=ntot
                    heapq.heappush(hp,(ntot,nx,ny,))
        

        
```
---
