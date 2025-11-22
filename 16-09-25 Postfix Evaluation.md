# 16-09-2025
---
## Postfix Evaluation
Difficulty: MediumAccuracy: 63.04%Submissions: 125K+Points: 4

<pre>
You are given an array of strings arr[] that represents a valid arithmetic expression written in Reverse Polish Notation (Postfix Notation). Your task is to evaluate the expression and return an integer representing its value.

Note: A postfix expression is of the form operand1 operand2 operator (e.g., "a b +"). 
And the division operation between two integers always computes the floor value, i.e floor(5 / 3) = 1 and floor(-5 / 3) = -2.
It is guaranteed that the result of the expression and all intermediate calculations will fit in a 32-bit signed integer.

Examples:

Input: arr[] = ["2", "3", "1", "*", "+", "9", "-"]
Output: -4
Explanation: If the expression is converted into an infix expression, it will be 2 + (3 * 1) – 9 = 5 – 9 = -4.
Input: arr[] = ["2", "3", "^", "1", "+"]
Output: 9
Explanation: If the expression is converted into an infix expression, it will be 2 ^ 3 + 1 = 8 + 1 = 9.
Constraints:
3 ≤ arr.size() ≤ 103
arr[i] is either an operator: "+", "-", "*", "/" or "^", or an integer in the range [-104, 104]
	
</pre>

---
```
class Solution:
    def evaluatePostfix(self, arr):
        # code here
        arithmetic = {
            '+' : lambda a, b : a + b,
            '-' : lambda a, b : a - b,
            '*' : lambda a, b : a * b,
            '/' : lambda a, b : a // b,
            '^' : lambda a, b : a ** b
        }

        bt = []
        for i in arr:
            res = i
            if i in arithmetic:
                arg2 = int(bt.pop())
                arg1 = int(bt.pop())
                res = arithmetic[i](arg1, arg2)
            bt.append(res)

        return bt[-1]
        

```
---
