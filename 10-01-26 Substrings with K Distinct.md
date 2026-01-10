# 10-01-26
---
## Substrings with K Distinct
Difficulty: MediumAccuracy: 20.46%Submissions: 187K+Points: 4Average Time: 20m
<pre>

You are given a string s consisting of lowercase characters and an integer k, You have to count all possible substrings that have exactly k distinct characters.

Examples :

Input: s = "abc", k = 2
Output: 2
Explanation: Possible substrings are ["ab", "bc"]
Input: s = "aba", k = 2
Output: 3
Explanation: Possible substrings are ["ab", "ba", "aba"]
Input: s = "aa", k = 1
Output: 3
Explanation: Possible substrings are ["a", "a", "aa"]
Constraints:
1 ≤ s.size() ≤ 106
1 ≤ k ≤ 26
</pre>

---
```
class Solution:
    def countSubstr (self, s, k):
        # Code here
        from collections import defaultdict
        
        def at_most_k(s, k):
            count = 0
            left = 0
            freq = defaultdict(int)
            
            for right in range(len(s)):
                freq[s[right]] += 1
                while len(freq) > k:
                    freq[s[left]] -= 1
                    if freq[s[left]] == 0:
                        del freq[s[left]]
                    left += 1
                count += right - left + 1
            return count
        
        return at_most_k(s, k) - at_most_k(s, k - 1)
        
```
---
