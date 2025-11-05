# 05-11-25
---
## Get Minimum Squares
Difficulty: MediumAccuracy: 45.22%Submissions: 50K+Points: 4

<pre>


Given a positive integer n, find the minimum number of perfect squares (square of an integer) that sum up to n.

Note: Every positive integer can be expressed as a sum of square numbers since 1 is a perfect square, and any number can be represented as 1*1 + 1*1 + 1*1 + ....

Examples:

Input: n = 100
Output: 1
Explanation: 10 * 10 = 100
Input: n = 6
Output: 3
Explanation = 1 * 1 + 1 * 1 + 2 * 2 = 6 
Constraints:
1 ≤ n ≤ 104

    
</pre>

---
```
import math

class Solution:
    def minSquares(self, n: int) -> int:
        # helper: is x a perfect square?
        is_square = lambda x: int(x**0.5)**2 == x

        # 1) perfect square?
        if is_square(n): return 1

        # 2) remove factors of 4
        while n % 4 == 0: n //= 4

        # 3) if n % 8 == 7 then by Legendre's theorem answer is 4
        if n % 8 == 7: return 4

        # 4) check if sum of two squares -> answer 2
        return 2 if any(is_square(n - a*a) for a in range(1, math.isqrt(n)+1)) else 3
        
```
---
