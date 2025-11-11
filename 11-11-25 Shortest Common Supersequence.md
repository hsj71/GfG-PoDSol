# 11-11-25
---
## Shortest Common Supersequence
Difficulty: MediumAccuracy: 55.62%Submissions: 139K+Points: 4
<pre>
  


Given two strings s1 and s2, find the length of the smallest string which has both s1 and s2 as its sub-sequences.
Note: s1 and s2 can have both uppercase and lowercase English letters.

Examples:

Input: s1 = "geek", s2 = "eke"
Output: 5
Explanation: String "geeke" has both string "geek" and "eke" as subsequences.
Input: s1 = "AGGTAB", s2 = "GXTXAYB"
Output: 9
Explanation: String "AGXGTXAYB" has both string "AGGTAB" and "GXTXAYB" as subsequences.
Input: s1 = "geek", s2 = "ek"
Output: 4
Explanation: String "geek" has both string "geek" and "ek" as subsequences.
Constraints:
1 ≤ s1.size(), s2.size() ≤ 500


    
</pre>

---
```
class Solution:
    def minSuperSeq(self, s1, s2):
        # code here
        l1, l2 = len(s1), len(s2)
        dp = [[0] * (l2 + 1) for _ in range(l1 + 1)]
        for i in range(1, l1 + 1):
            for j in range(1, l2 + 1):
                if s1[i-1] == s2[j-1]:
                    dp[i][j] = dp[i-1][j-1] + 1
                else:
                    dp[i][j] = max(dp[i][j-1], dp[i-1][j])
        return l1 + l2 - dp[-1][-1]

        
```
---
