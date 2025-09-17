# 17-09-2025
---
## Decode the string
Difficulty: MediumAccuracy: 44.28%Submissions: 67K+Points: 4Average Time: 10m

<pre>
Given an encoded string s, decode it by expanding the pattern k[substring], where the substring inside brackets is written k times. k is guaranteed to be a positive integer, and encodedString contains only lowercase english alphabets. Return the final decoded string.

Note: The test cases are generated so that the length of the output string will never exceed 105 .

Examples:

Input: s = "3[b2[ca]]"
Output: "bcacabcacabcaca"
Explanation:
Inner substring “2[ca]” breakdown into “caca”.
Now, new string becomes “3[bcaca]”
Similarly “3[bcaca]” becomes “bcacabcacabcaca” which is final result.
Input: s = "3[ab]"
Output: "ababab"
Explanation: The substring "ab" is repeated 3 times giving "ababab".
Constraints:
1 ≤ |s| ≤ 105 
1 ≤ k ≤ 100
	
</pre>

---
```
class Solution:
    def decodedString(self, s):
        # code here
        stack = []
        for i in s:
            if i == ']':
                expand = ''
                while stack[-1] != '[':
                    expand = stack.pop() + expand
                stack.pop()

                m = ''
                while stack and stack[-1].isdigit():
                    m = stack.pop() + m
                
                stack.append(int(m) * expand)
                continue
            
            stack.append(i)
            
        return ''.join(stack)

```
---
