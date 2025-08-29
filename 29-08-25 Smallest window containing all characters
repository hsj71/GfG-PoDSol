# 29-08-2025
---
## Smallest window containing all characters
Difficulty: HardAccuracy: 30.19%Submissions: 184K+Points: 8Average Time: 30m
<pre>
Given two strings s and p. Find the smallest substring in s consisting of all the characters (including duplicates) of the string p. Return empty string in case no such substring is present.
If there are multiple such substring of the same length found, return the one with the least starting index.

Examples:

Input: s = "timetopractice", p = "toc"
Output: "toprac"
Explanation: "toprac" is the smallest substring in which "toc" can be found.
Input: s = "zoomlazapzo", p = "oza"
Output: "apzo"
Explanation: "apzo" is the smallest substring in which "oza" can be found.
Input: s = "zoom", p = "zooe"
Output: ""
Explanation: No substring is present containing all characters of p.
Constraints: 
1 ≤ s.length(), p.length() ≤ 106
s, p consists of lowercase english letters
</pre>

---
```
class Solution:
    def smallestWindow(self, s, p):
        # code here
        from collections import Counter
        
        pct = Counter(p)
        counter = 0  
        left = 0
        ans = None
        sct = Counter()
        
        for r, e in enumerate(s):
            if e not in p: 
                continue
            
            sct[e] += 1
            if sct[e] <= pct[e]:  
                counter += 1
            
            while left <= r and counter >= len(p):
                if ans is None or len(ans) > r-left+1:
                    ans = s[left:r+1]
                leftc = s[left]
                if leftc in sct:
                    sct[leftc] -= 1
                    if sct[leftc] < pct[leftc]:
                        counter -= 1
                left += 1
            
        return "" if not ans else ans
 

```
---
