# 12-11-25
---
## Wildcard Pattern Matching
Difficulty: MediumAccuracy: 31.13%Submissions: 94K+Points: 4
<pre>
  


Given two strings pat and txt which may be of different sizes, You have to return true if the wildcard pattern i.e. pat, matches with txt else return false.

The wildcard pattern pat can include the characters '?' and '*'.

'?' – matches any single character.
'*' – matches any sequence of characters (including the empty sequence).
Note: The matching should cover the entire txt (not partial txt).

Examples:

Input: txt = "abcde", pat = "a?c*"
Output: true
Explanation: '?' matches with 'b' and '*' matches with "de".
Input: txt = "baaabab", pat = "a*ab"
Output: false
Explanation: The pattern starts with a, but the text starts with b, so the pattern does not match the text.
Input: txt = "abc", pat = "*"
Output: true
Explanation: '*' matches with whole text "abc".
Constraints:
1 ≤ txt.size(), pat.size() ≤ 100

    
</pre>

---
```
class Solution:
    def wildCard(self, string: str, pattern: str) -> bool:
        n, m = len(string), len(pattern)
        dp = [[False]*(n+1) for _ in range(m+1)]
        dp[0][0] = True

        for i in range(1, m+1):
            dp[i][0] = pattern[i-1] == '*' and dp[i-1][0]

        for i in range(1, m+1):
            for j in range(1, n+1):
                if pattern[i-1] in ('?', string[j-1]):
                    dp[i][j] = dp[i-1][j-1]
                elif pattern[i-1] == '*':
                    dp[i][j] = dp[i-1][j] or dp[i][j-1]

        return dp[m][n]
        
```
---
