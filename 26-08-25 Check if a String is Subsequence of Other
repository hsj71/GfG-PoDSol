# 26-08-2025
---
## Check if a String is Subsequence of Other
Difficulty: EasyAccuracy: 51.68%Submissions: 31K+Points: 2
<pre>
Given two strings s1 and s2. You have to check that s1 is a subsequence of s2 or not.
Note: A subsequence is a sequence that can be derived from another sequence by deleting some elements without changing the order of the remaining elements.

Examples:

Input: s1 = "AXY", s2 = "YADXCP"
Output: false
Explanation: s1 is not a subsequence of s2 as 'Y' appears before 'A'.
Input: s1 = "gksrek", s2 = "geeksforgeeks"
Output: true
Explanation: If we combine the bold character of "geeksforgeeks", it equals to s1. So s1 is a subsequence of s2. 
Constraints:
1 ≤ s1.size(), s2.size() ≤ 106
</pre>

---
```
class Solution:
    def isSubSeq(self, s1, s2):
        # code here
        l = len(s1)
        mi = 0
        
        for ch in s2:
            if mi < l and s1[mi] == ch:
                mi += 1
     
        return mi == l

```
---
