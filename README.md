# 10-08-2025
---
## Palindrome SubStrings

Given a string s, count all palindromic sub-strings present in the string. The length of the palindromic sub-string must be greater than or equal to 2.

Note: A substring is palindromic if it reads the same forwards and backwards.

Examples:

Input: s = "abaab"
Output: 3
Explanation: All palindromic substrings (of length > 1) are: "aba", "aa", "baab".
Input: s = "aaa"
Output: 3
Explanation: All palindromic substrings (of length > 1) are: "aa", "aa", "aaa".
Input: s = "abbaeae"
Output: 4
Explanation: All palindromic substrings (of length > 1) are: "bb", "abba", "aea", "eae".
Constraints:
2 ≤ s.size() ≤ 5 * 103
s contains only lowercase english characters


---

```
class Solution:
    def countPS(self, s):
        # code here
        n = len(s)
        count = 0
    
        def expand(l, r):
            nonlocal count
            while l >= 0 and r < n and s[l] == s[r]:
                if r - l + 1 >= 2:  # length >= 2
                    count += 1
                l -= 1
                r += 1
    
        for i in range(n):
            # Odd length palindromes
            expand(i, i)
            # Even length palindromes
            expand(i, i + 1)
    
        return count
            
```
