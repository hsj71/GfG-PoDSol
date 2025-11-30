# 30-11-25
---
## Count of distinct substrings
Difficulty: MediumAccuracy: 40.21%Submissions: 36K+Points: 4
<pre>


Given a string s consisting of lowercase English characters, determine the total number of distinct non-empty substrings present in the string. A substring is defined as a contiguous block of characters within the string.

Two substrings are considered distinct if their contents differ, even if they originate from different positions in the string.

Note: The empty substring is not counted.

Examples :

Input: s = "ababa"
Output: 9
Explanation: All distinct substrings of "ababa" are: "a", "b", "ab", "ba", "aba", "bab", "abab", "baba", "ababa".
Input: s = "aaa"
Output: 3
Explanation: The distinct substrings of "aaa" are: "a", "aa", "aaa".
Constraints:
1 ≤ s.size() ≤ 3000
    
</pre>

---
```
class Solution:
    def countSubs(self, s):
        # code here
        substrings = set()
        n = len(s)
        for i in range(n):
            for j in range(i + 1, n + 1):
                substrings.add(s[i:j])
        return len(substrings)
        
        
```
---
