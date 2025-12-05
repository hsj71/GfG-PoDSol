# 5-12-25
---
## Walls Coloring II
Difficulty: HardAccuracy: 50.15%Submissions: 32K+Points: 8
<pre>

You are given n walls arranged in a row, and each wall must be painted using one of the k available colors. The cost of painting ith wall with jth color is given by costs[i][j]. Your task is to determine the minimum total cost required to paint all the walls in such a way that no two adjacent walls share the same color. If it is impossible to paint the walls under this condition, you must return -1.

Examples:

Input: n = 4, k = 3,
costs[][] = [[1, 5, 7],
           [5, 8, 4],
           [3, 2, 9],
           [1, 2, 4]]

Output: 8
Explanation:
Paint wall 0 with color 0. Cost = 1
Paint wall 1 with color 2. Cost = 4
Paint wall 2 with color 1. Cost = 2
Paint wall 3 with color 0. Cost = 1
Total Cost = 1 + 4 + 2 + 1 = 8
Input: n = 5, k = 1,
costs[][] = [[5],
           [4],
           [9],
           [2],
           [1]]
Output: -1
Explanation: It is not possible to color all the walls under the given conditions.
Constraints:
0 ≤ n  ≤ 103
0 ≤ k  ≤ 103
1 ≤ costs[i][j]  ≤ 105


    
</pre>

---
```
class Solution:
    def minCost(self, costs : list[list[int]]) -> int:
        # code here
        if not costs:
            return 0
        n=len(costs)
        k=len(costs[0])
        if k==1 and n==1:
            return costs[0][0]
        if k<2:
            return -1
        
        dp=[0]*k
        m1=[0,0]
        m2=[0,1]
        for i in range(n):
            temp=[0]*k
            d1=[float('inf'),0]
            d2=[float("inf"),0]
            for j in range(k):
                if j==m1[1]:
                    temp[j]=m2[0]+costs[i][j]
                else:
                    temp[j]=m1[0]+costs[i][j]
                if temp[j]<d1[0]:
                    d2=d1
                    d1=[temp[j],j]
                elif temp[j]<d2[0]:
                    d2=[temp[j],j]
            m1=d1
            m2=d2
            dp=temp
        return m1[0]
        
```
---
