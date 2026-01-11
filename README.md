# 11-01-26
---
## Minimum Window Subsequence
Difficulty: MediumAccuracy: 49.43%Submissions: 23K+Points: 4Average Time: 45m
<pre>


You are given two strings, s1 and s2. Your task is to find the smallest substring in s1 such that s2 appears as a subsequence within that substring.

The characters of s2 must appear in the same sequence within the substring of s1.
If there are multiple valid substrings of the same minimum length, return the one that appears first in s1.
If no such substring exists, return an empty string.
Note: Both the strings contain only lowercase english letters.

Examples:

Input: s1 = "geeksforgeeks", s2 = "eksrg"
Output: "eksforg"
Explanation: "eksforg" satisfies all required conditions. s2 is its subsequence and it is smallest and leftmost among all possible valid substrings of s1.
Input: s1 = "abcdebdde", s2 = "bde" 
Output: "bcde"
Explanation:  "bcde" and "bdde" are two substring of s1 where s2 occurs as subsequence but "bcde" occur first so we return that.
Input: s1 = "ad", s2 = "b" 
Output: ""
Explanation: There is no substring exists.
Constraints:
1 ≤ s1.length ≤ 104
1 ≤ s2.length ≤ 50


</pre>

---
```
class Solution:
    def minWindow(self, s1, s2):
        n,m=len(s1),len(s2)
        inf = 10**9
        dp = {}
        
        def solve(i,j):
            if j==m:
                return i
            
            if i==n:
                return inf
            
            if (i,j) in dp:
                return dp[(i,j)]
            
            if s1[i]==s2[j]:
                dp[(i,j)] = solve(i+1,j+1)
            else:
                dp[(i,j)] = solve(i+1,j)
            return dp[(i,j)]
        
        start=-1
        min_ = inf
        
        for i in range(n):
            if s1[i]==s2[0]:
                end = solve(i,0)
                if end!=inf and end-i<min_:
                    min_ = end-i
                    start = i
        
        return "" if start==-1 else s1[start:start+min_]
        
```
---
