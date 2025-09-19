# 19-09-2025
---
## Min Add to Make Parentheses Valid
Difficulty: MediumAccuracy: 61.08%Submissions: 10K+Points: 4

<pre>
You are given a string s consisting only of the characters '(' and ')'. Your task is to determine the minimum number of parentheses (either '(' or ')') that must be inserted at any positions to make the string s a valid parentheses string.

A parentheses string is considered valid if:

Every opening parenthesis '(' has a corresponding closing parenthesis ')'.
Every closing parenthesis ')' has a corresponding opening parenthesis '('.
Parentheses are properly nested.
Examples:

Input: s = "(()("
Output: 2
Explanation: There are two unmatched '(' at the end, so we need to add two ')' to make the string valid.
Input: s = ")))"
Output: 3
Explanation: Three '(' need to be added at the start to make the string valid.
Input: s = ")()()"
Output: 1 
Explanation: The very first ')' is unmatched, so we need to add one '(' at the beginning.
Constraints:
1 ≤ s.size() ≤ 105
s[i] ∈ { '(' , ')' }

	
</pre>

---
```
class Solution:
    def minParentheses(self, s):
        # code here
        op=0
        res=0
        for i in s:
            if i=='(':
                op+=1
            elif op>0:
                op-=1
            else:
                res+=1
        res+=op
        return res
        
```
---
