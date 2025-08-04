# 04-08-2025
---
## Maximum sum Rectangle

Given a 2D matrix mat[][] with dimensions n×m. Find the maximum possible sum of any submatrix within the given matrix.

Examples:

Input: mat[][] = [[1, 2, -1, -4, -20], [-8, -3, 4, 2, 1], [3, 8, 10, 1, 3], [-4, -1, 1, 7, -6]]
Output: 29
Explanation: The matrix is as follows and the green rectangle denotes the maximum sum rectangle which is equal to 29.

Input: mat[][] = [[-1, -2], [-3, -4]]
Output: -1
Explanation: Taking only the first cell is the optimal choice.
Constraints:
1 ≤ n, m ≤ 300
-1000 ≤ mat[i][j] ≤ 1000


---
```
class Solution:
    def maxRectSum(self, mat):
        # code here
        n = len(mat)
        m = len(mat[0])
        max_sum = float('-inf')
    
        for top in range(n):
            temp = [0] * m
            for bottom in range(top, n):
                for col in range(m):
                    temp[col] += mat[bottom][col]
    
                # Apply 1D Kadane's algorithm on temp[]
                current_max = self.kadane(temp)
                max_sum = max(max_sum, current_max)
    
        return max_sum
    
    def kadane(self, arr):
        max_end = max_so_far = arr[0]
        for num in arr[1:]:
            max_end = max(num, max_end + num)
            max_so_far = max(max_so_far, max_end)
        return max_so_far
            
```
