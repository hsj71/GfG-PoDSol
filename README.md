# 4-10-2025
---
## Expression Add Operators
Difficulty: HardAccuracy: 61.49%Submissions: 28K+Points: 8Average Time: 40m

<pre>

Given a string s that contains only digits (0-9) and an integer target, return all possible strings by inserting the binary operator ' + ', ' - ', and/or ' * ' between the digits of s such that the resultant expression evaluates to the target value.

Note:

Operands in the returned expressions should not contain leading zeros. For example, 2 + 03 is not allowed whereas 20 + 3 is fine.
It is allowed to not insert any of the operators.
Driver code will print the final list of strings in lexicographically smallest order.
Examples:

Input: s = "124", target = 9
Output: ["1+2*4"]
Explanation: The valid expression that evaluate to 9 is 1 + 2 * 4
Input: s = "125", target = 7
Output: ["1*2+5", "12-5"]
Explanation: The two valid expressions that evaluate to 7 are 1 * 2 + 5 and 12 - 5.
Input: s = "12", target = 12
Output: ["12"] 
Explanation: s itself matches the target. No other expressions are possible.
Input: s = "987612", target = 200
Output: []
Explanation: There are no expressions that can be created from "987612" to evaluate to 200.
Constraints:
1 ≤ s.size() ≤ 9
s consists of only digits (0-9).
-231 ≤ target ≤ 231-1

</pre>

---
```
class Solution:
    def findExpr(self, s, target):
        res = []
        
        def backtrack(index, expr, value, prev):

            if index == len(s):
                if value == target:
                    res.append(expr)
                return
            
            for i in range(index, len(s)):
                # Avoid numbers with leading zeros
                if i > index and s[index] == '0':
                    break
                    
                num_str = s[index:i+1]
                num = int(num_str)
                
                if index == 0:
                    # First number (no operator before it)
                    backtrack(i+1, num_str, num, num)
                else:
                    # Addition
                    backtrack(i+1, expr + "+" + num_str, value + num, num)
                    # Subtraction
                    backtrack(i+1, expr + "-" + num_str, value - num, -num)
                    # Multiplication
                    backtrack(i+1, expr + "*" + num_str, value - prev + prev * num, prev * num)
        
        backtrack(0, "", 0, 0)
        res.sort()  # lexicographically smallest order
        return res
        

        
        
```
---
