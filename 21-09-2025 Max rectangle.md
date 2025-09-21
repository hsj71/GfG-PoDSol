# 21-09-2025
---
## Max rectangle
Difficulty: HardAccuracy: 36.43%Submissions: 126K+Points: 8Average Time: 35m

<pre>
You are given a 2D binary matrix mat[ ][ ], where each cell contains either 0 or 1. Your task is to find the maximum area of a rectangle that can be formed using only 1's within the matrix.

Examples:

Input: mat[][] = [[0, 1, 1, 0],
                [1, 1, 1, 1],
                [1, 1, 1, 1],
                [1, 1, 0, 0]]
Output: 8
Explanation: The largest rectangle with only 1’s is from (1, 0) to (2, 3) which is
[1, 1, 1, 1]
[1, 1, 1, 1]
and area is 4 * 2 = 8.
Input: mat[][] = [[0, 1, 1],
                [1, 1, 1],
                [0, 1, 1]]
Output: 6
Explanation: The largest rectangle with only 1’s is from (0, 1) to (2, 2) which is
[1, 1]
[1, 1]
[1, 1]
and area is 2 * 3 = 6.
Constraints:
1 ≤ mat.size(), mat[0].size() ≤1000
0 ≤ mat[][] ≤1

	
</pre>

---
```
class Solution:
    def maxArea(self, mat):
        def largestHistogramArea(heights):
            # Add sentinel zeros to simplify edge handling
            heights = [0] + heights + [0]
            stack = []
            max_area = 0

            for i, h in enumerate(heights):
                while stack and heights[stack[-1]] > h:
                    height = heights[stack.pop()]
                    width = i - stack[-1] - 1
                    max_area = max(max_area, height * width)
                stack.append(i)

            return max_area

        if not mat or not mat[0]:
            return 0

        max_area = largestHistogramArea(mat[0])

        for i in range(1, len(mat)):
            for j in range(len(mat[0])):
                if mat[i][j] == 1:
                    mat[i][j] += mat[i - 1][j]
            max_area = max(max_area, largestHistogramArea(mat[i]))

        return max_area
        
        
```
---
