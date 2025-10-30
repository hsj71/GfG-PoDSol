# 30-10-25
---
## Replace O's with X's
Difficulty: MediumAccuracy: 34.0%Submissions: 130K+Points: 4Average Time: 20m

<pre>


You are given a grid[][] of size n*m, where every element is either 'O' or 'X'. You have to replace all 'O' or a group of 'O' with 'X' that are surrounded by 'X'.

A 'O' (or a set of 'O') is considered to be surrounded by 'X' if there are 'X' at locations just below, just above, just left and just right of it.

Examples:

Input: 
grid[][] = [['X', 'X', 'X', 'X'], 
          ['X', 'O', 'X', 'X'], 
          ['X', 'O', 'O', 'X'], 
          ['X', 'O', 'X', 'X'], 
          ['X', 'X', 'O', 'O']]
Output: 
[['X', 'X', 'X', 'X'], 
['X', 'X', 'X', 'X'], 
['X', 'X', 'X', 'X'], 
['X', 'X', 'X', 'X'], 
['X', 'X', 'O', 'O']]
Explanation: We only changed those 'O' that are surrounded by 'X'
Input: 
grid[][] = [['X', 'O', 'X', 'X'], 
          ['X', 'O', 'X', 'X'], 
          ['X', 'O', 'O', 'X'], 
          ['X', 'O', 'X', 'X'], 
          ['X', 'X', 'O', 'O']]
Output: 
[['X', 'O', 'X', 'X'], 
['X', 'O', 'X', 'X'], 
['X', 'O', 'O', 'X'], 
['X', 'O', 'X', 'X'], 
['X', 'X', 'O', 'O']]
Explanation: There's no 'O' that's surround by 'X'.
Input: 
grid[][] = [['X', 'X', 'X'], 
          ['X', 'O', 'X'], 
          ['X', 'X', 'X']]
Output: 
[['X', 'X', 'X'], 
['X', 'X', 'X'], 
['X', 'X', 'X']]
Explanation: There's only one 'O' that's surround by 'X'.
Constraints:
1 ≤ grid.size() ≤ 100
1 ≤ grid[0].size() ≤ 100


    
</pre>

---
```
def fill(self, grid):
        from itertools import chain, product
        m, n = len(grid), len(grid[0])
        
        def neighbors(x, y):
            if x > 0:
                yield (x - 1, y)
            if (x1 := x + 1) < m:
                yield (x1, y)
            if y > 0:
                yield (x, y - 1)
            if (y1 := y + 1) < n:
                yield (x, y1)
                
        visited = [[False] * n for _ in range(m)]
        q = []
        for x, y in chain(
            product(range(m), [0, n - 1]),
            product([0, m - 1], range(1, n - 1))
        ):
            if grid[x][y] == "O":
                visited[x][y] = True
                q.append((x, y))
        while q:
            x, y = q.pop()
            for nx, ny in neighbors(x, y):
                if grid[nx][ny] == "O" and not visited[nx][ny]:
                    visited[nx][ny] = True
                    q.append((nx, ny))
        for x, y in product(range(m), range(n)):
            if grid[x][y] == "O" and not visited[x][y]:
                grid[x][y] = "X"
        
```
---
