# 13-09-2025
---
## Minimum Cost to cut a board into squares
Difficulty: MediumAccuracy: 60.83%Submissions: 25K+Points: 4


<pre>
Given a board of dimensions n × m that needs to be cut into n*m squares. The cost of making a cut along a horizontal or vertical edge is provided in two arrays:

x[]: Cutting costs along the vertical edges (length-wise).
y[]: Cutting costs along the horizontal edges (width-wise).
Find the minimum total cost required to cut the board into squares optimally.

Examples:

Input: n = 4, m = 6, x[] = [2, 1, 3, 1, 4], y[] = [4, 1, 2]
Output: 42
Explanation:

Initially no. of horizontal segments = 1 & no. of vertical segments = 1.
Optimal way to cut into square is:
• Pick 4 (from x) -> vertical cut, Cost = 4 × horizontal segments = 4,
  Now, horizontal segments = 1, vertical segments = 2.
• Pick 4 (from y) -> horizontal cut, Cost = 4 × vertical segments = 8,
  Now, horizontal segments = 2, vertical segments = 2.
• Pick 3 (from x) -> vertical cut, Cost = 3 × horizontal segments = 6,
  Now, horizontal segments = 2, vertical segments = 3.
• Pick 2 (from x) -> vertical cut, Cost = 2 × horizontal segments = 4,
  Now, horizontal segments = 2, vertical segments = 4.
• Pick 2 (from y) -> horizontal cut, Cost = 2 × vertical segments = 8,
  Now, horizontal segments = 3, vertical segments = 4.
• Pick 1 (from x) -> vertical cut, Cost = 1 × horizontal segments = 3,
  Now, horizontal segments = 3, vertical segments = 5.
• Pick 1 (from x) -> vertical cut, Cost = 1 × horizontal segments = 3,
  Now, horizontal segments = 3, vertical segments = 6.
• Pick 1 (from y) -> horizontal cut, Cost = 1 × vertical segments = 6,
  Now, horizontal segments = 4, vertical segments = 6.
So, the total cost = 4 + 8 + 6 + 4 + 8 + 3 + 3 + 6 = 42.
Input: n = 4, m = 4, x[] = [1, 1, 1], y[] = [1, 1, 1]
Output: 15
Explanation: 

Initially no. of horizontal segments = 1 & no. of vertical segments = 1.
Optimal way to cut into square is: 
• Pick 1 (from y) -> horizontal cut, Cost = 1 × vertical segments = 1,
  Now, horizontal segments = 2, vertical segments = 1.
• Pick 1 (from y) -> horizontal cut, Cost = 1 × vertical segments = 1,
  Now, horizontal segments = 3, vertical segments = 1.
• Pick 1 (from y) -> horizontal cut, Cost = 1 × vertical segments = 1,
  Now, horizontal segments = 4, vertical segments = 1.
• Pick 1 (from x) -> vertical cut, Cost = 1 × horizontal segments = 4,
  Now, horizontal segments = 4, vertical segments = 2.
• Pick 1 (from x) -> vertical cut, Cost = 1 × horizontal segments = 4,
  Now, horizontal segments = 4, vertical segments = 3.
• Pick 1 (from x) -> vertical cut, Cost = 1 × horizontal segments = 4,
  Now, horizontal segments = 4, vertical segments = 4
So, the total cost = 1 + 1 + 1 + 4 + 4 + 4 = 15.
Constraints:
2 ≤ n, m ≤ 103
1 ≤ x[i], y[j] ≤103
	
</pre>

---
```
class Solution:
    def minCost(self, n, m, x, y):
        # code here
        x.sort(reverse=True)
        y.sort(reverse=True)

        horizontal_pieces = 1
        vertical_pieces = 1

        i = j = 0
        total_cost = 0

        while i < len(x) and j < len(y):
            if x[i] > y[j]:
                total_cost += x[i] * horizontal_pieces
                vertical_pieces += 1
                i += 1
            else:
                total_cost += y[j] * vertical_pieces
                horizontal_pieces += 1
                j += 1

        while i < len(x):
            total_cost += x[i] * horizontal_pieces
            i += 1


        while j < len(y):
            total_cost += y[j] * vertical_pieces
            j += 1

        return total_cost
        
        
        

```
---
