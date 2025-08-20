# 20-08-2025
---
## Search in fully rotated sorted 2D matrix
Difficulty: MediumAccuracy: 56.77%Submissions: 11K+Points: 4Average Time: 20m
<pre>
You are given a 2D matrix mat[][] of size n x m that was initially filled in the following manner:


Each row is sorted in increasing order from left to right.
The first element of every row is greater than the last element of the previous row.

This implies that if the matrix is flattened row-wise, it forms a strictly sorted 1D array.
Later, this sorted 1D array was rotated at some unknown pivot. The rotated array was then written back into the matrix row-wise to form the current matrix.


Given such a matrix mat[][] and an integer x, determine whether x exists in the matrix.


Examples:

Input: x = 3,
mat[][] = [[7, 8, 9, 10],           
          [11, 12, 13, 1],
          [2, 3, 4, 5]] 
Output: true
Explanation: 3 is located at the 3rd row and 2nd column.
Input: x = 10,
mat[][] = [[6, 7, 8],                         
          [9, 1, 2],
          [3, 4, 5]]
Output: false
Explanation: The value 10 does not exist in the matrix.
Constraint:
1 ≤ n × m ≤ 105
1 ≤ mat[i][j], x ≤ 106
</pre>

---
```
class Solution:
    def searchMatrix(self, mat, x):
        # code here
        for arr in mat:
            if arr[-1]<arr[0]:
                if x in arr:
                    return True
            elif x>=arr[0] and x<=arr[-1]:
                if x in arr:
                    return True
        return False
            
```
---
