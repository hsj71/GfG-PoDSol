# 17-01-26
---
## Expression contains redundant bracket or not
Difficulty: MediumAccuracy: 48.71%Submissions: 42K+Points: 4
<pre>


Given a string of balanced expression s, check if it contains a redundant parenthesis or not. A set of parenthesis are redundant if the same sub-expression is surrounded by unnecessary or multiple brackets.
Note: Expression may contain + , - , *, and / operators. Given expression is valid and there are no white spaces present.

Examples:

Input: s = "((a+b))"
Output: true 
Explanation: ((a+b)) can reduced to (a+b).
Input: s = "(a+(b)/c)"
Output: true
Explanation: (a+(b)/c) can reduced to (a+b/c) because b is surrounded by () which is redundant.
Input: s = "(a+b+(c+d))"
Output: false
Explanation:(a+b+(c+d)) doesn't have any redundant or multiple brackets.
Constraints:
1 ≤ |s| ≤105
    
</pre>

---
```
class Solution():
    def checkRedundancy(self, s):
        # code here 
        stack = []
        for i in s :
            stack.append(i)
            if stack[-1] == ")" :
            
                if stack[-2] == "(" or stack[-3] == "(":
                    return True
                else :
                    while stack[-1] != "(":
                        stack.pop()
                    stack.pop()
        return False
```
---
