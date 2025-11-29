# 29-11-25
---
## Count set bits
Difficulty: MediumAccuracy: 35.77%Submissions: 251K+Points: 4
<pre>


You are given a number n. Find the total count of set bits for all numbers from 1 to n (both inclusive).

Examples :

Input: n = 4
Output: 5
Explanation: For numbers from 1 to 4. for 1: 0 0 1 => 1 set bit, for 2: 0 1 0 => 1 set bit, for 3: 0 1 1 => 2 set bits, for 4: 1 0 0 => 1 set bit. Therefore, the total set bits are 5.
Input: n = 17
Output: 35
Explanation: From numbers 1 to 17(both inclusive), the total number of set bits are 35.
Constraints:
1 ≤ n ≤ 108
    
</pre>

---
```
class Solution:
    def countSetBits(self, n):
        count = 0
        i = 0
        while (1 << i) <= n:
            next_power = 1 << (i + 1)
            half_power = 1 << i
            complete_blocks = (n + 1) // next_power
            count += complete_blocks * half_power
            remainder = (n + 1) % next_power
            count += max(0, remainder - half_power)
            i += 1
        return count
        
        
```
---
