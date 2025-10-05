# 5-10-2025
---
## Rat in a Maze
Difficulty: MediumAccuracy: 35.75%Submissions: 381K+Points: 4Average Time: 25m

<pre>


Consider a rat placed at position (0, 0) in an n x n square matrix maze[][]. The rat's goal is to reach the destination at position (n-1, n-1). The rat can move in four possible directions: 'U'(up), 'D'(down), 'L' (left), 'R' (right).

The matrix contains only two possible values:

0: A blocked cell through which the rat cannot travel.
1: A free cell that the rat can pass through.
Your task is to find all possible paths the rat can take to reach the destination, starting from (0, 0) and ending at (n-1, n-1), under the condition that the rat cannot revisit any cell along the same path. Furthermore, the rat can only move to adjacent cells that are within the bounds of the matrix and not blocked.
If no path exists, return an empty list.

Note: Return the final result vector in lexicographically smallest order.

Examples:

Input: maze[][] = [[1, 0, 0, 0], [1, 1, 0, 1], [1, 1, 0, 0], [0, 1, 1, 1]]
Output: ["DDRDRR", "DRDDRR"]
Explanation: The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.
Input: maze[][] = [[1, 0], [1, 0]]
Output: []
Explanation: No path exists as the destination cell (1, 1) is blocked.
Input: maze[][] = [[1, 1, 1], [1, 0, 1], [1, 1, 1]]
Output: ["DDRR", "RRDD"]
Explanation: The rat has two possible paths to reach the destination: DDRR and RRDD.
Constraints:
2 ≤ n ≤ 5
0 ≤ maze[i][j] ≤ 1

</pre>

---
```
class Solution:
    
    directions={
        "D":(1,0),
        "L":(0,-1),
        "R":(0,1),
        "U":(-1,0)
    }
    
    def solve(self,maze,path,res,i,j):
        n=len(maze)
        if i==n-1 and j==n-1:
            res.append("".join(path))
            return
        maze[i][j]=2
        for key,value in Solution.directions.items():
            x,y=i+value[0],j+value[1]
            if 0<=x<n and 0<=y<n and maze[x][y]==1:
                path.append(key)
                self.solve(maze,path,res,x,y)
                path.pop()
        maze[i][j]=1

    def ratInMaze(self, maze):
        n=len(maze)
        if maze[0][0]==0 or maze[n-1][n-1]==0:
            return []
        res=[]
        self.solve(maze,[],res,0,0)
        return res
        

        
        
```
---
