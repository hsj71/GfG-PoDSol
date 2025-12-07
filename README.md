# 7-12-25
---
## Number of distinct subsequences
Difficulty: HardAccuracy: 30.43%Submissions: 75K+Points: 8
<pre>


Given a string str consisting of lowercase english alphabets, the task is to find the number of distinct subsequences of the string
Note: Answer can be very large, so, ouput will be answer modulo 109+7.

Examples:

Input: str = "gfg"
Output: 7
Explanation: 
The seven distinct subsequences are "", "g", "f", "gf", "fg", "gg" and "gfg" .
Input: str = "ggg"
Output: 4
Explanation: 
The four distinct subsequences are "", "g", "gg", "ggg".
Constraints:
1 ≤ |str| ≤ 105
str contains lower case English alphabets


    
</pre>

---
```

class Solution:
	def distinctSubseq(self, str):
		# code here
		mod = 10**9 + 7
        n = len(s)
        dp = [0] * (n + 1)
        last = [-1] * 26
        
        dp[0] = 1
        
        for i in range(1, n + 1):
            dp[i] = (dp[i - 1] * 2) % mod
            c = ord(s[i - 1]) - 97
            if last[c] != -1:
                dp[i] = (dp[i] - dp[last[c] - 1] + mod) % mod
            last[c] = i
        
        return dp[n]
        
```
---
