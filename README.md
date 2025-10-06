# 6-10-2025
---
## The Knight's tour problem
Difficulty: MediumAccuracy: 55.21%Submissions: 10K+Points: 4

<pre>



You are given an integer n, there is a n × n chessboard with a Knight starting at the top-left corner (0, 0). Your task is to determine a valid Knight's Tour, where the Knight visits every square exactly once, following the standard movement rules of a chess Knight (two steps in one direction and one step perpendicular), for example if a Knight is placed at cell (2, 2), in one move it can move to any of the following cells: (4, 3), (4, 1), (0, 3), (0, 1), (3, 4), (3, 0), (1, 4) and (1, 0).

You have to return the order in which each cell is visited. If a solution exists, return the sequence of numbers (starting from 0) representing the order of visited squares. If no solution is possible, return an empty list.

Note: You can return any valid ordering, if it is correct the driver code will print true else it will print false.

Examples:

Input: n = 5
Output: true
Explanation: A possible Knight's Tour in a 5x5 chessboard is given below where Each number represents the step at which the Knight visits that cell, starting from (0, 0) as step 0.
[[0, 11, 2, 17, 20],
 [3, 16, 19, 12, 7],
 [10, 1, 6, 21, 18],
 [15, 4, 23, 8, 13], 
 [24, 9, 14, 5, 22]]
Input: n = 4
Output: true
Explanation: For n = 4, it is not possible for a valid Knight's Tour so you have to return [].
Constraints:
1 ≤ n ≤ 6


</pre>

---
```
class Solution:
    def knightTour(self, n):
        # code here
        if n == 1:
            return [[0]]
        if n <= 4:
            return []
        
        moves = [
            (-2, -1), (-2, 1), (-1, -2), (-1, 2),
            (1, -2), (1, 2), (2, -1), (2, 1)
        ]
        
        board = [[-1 for _ in range(n)] for _ in range(n)]
        
        def is_safe(x, y):
            return 0 <= x < n and 0 <= y < n and board[x][y] == -1
        
        def get_degree(x, y):
            count = 0
            for dx, dy in moves:
                if is_safe(x + dx, y + dy):
                    count += 1
            return count
        
        def solve(x, y, move_count):
            board[x][y] = move_count
            
            if move_count == n * n - 1:
                return True
            
            next_moves = []
            for dx, dy in moves:
                next_x, next_y = x + dx, y + dy
                if is_safe(next_x, next_y):
                    degree = get_degree(next_x, next_y)
                    next_moves.append((degree, next_x, next_y))
            
            next_moves.sort() 
            
            for _, next_x, next_y in next_moves:
                if solve(next_x, next_y, move_count + 1):
                    return True
            
            board[x][y] = -1
            return False
        
        if solve(0, 0, 0):
            return board
        else:
            return []
        

        
        
```
---
