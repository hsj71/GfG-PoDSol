# 10-09-2025
---
## Largest number in one swap
Difficulty: EasyAccuracy: 48.67%Submissions: 18K+Points: 2
<pre>
Given a string s, return the lexicographically largest string that can be obtained by swapping at most one pair of characters in s.

Examples:

Input: s = "768"
Output: "867"
Explanation: Swapping the 1st and 3rd characters(7 and 8 respectively), gives the lexicographically largest string.
Input: s = "333"
Output: "333"
Explanation: Performing any swaps gives the same result i.e "333".
Constraints:
1 ≤ |s| ≤ 105
'0' ≤ s[i] ≤ '9'
</pre>

---
```
class Solution:
    def largestSwap(self, s):
        #code here
        a = sorted(s, key=lambda e: -ord(e))
        i = 0
        while i < len(s):
            if s[i] < a[i]:
                break
            i += 1
        else:
            return s
        
        j = s.rfind(a[i])
        a = list(s)
        a[i], a[j] = a[j], a[i]
        return "".join(a)
```
---
