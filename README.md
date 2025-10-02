# 2-10-2025
---
## Unique K-Number Sum
Difficulty: MediumAccuracy: 73.03%Submissions: 8K+Points: 4

<pre>


Given two integers n and k, the task is to find all valid combinations of k numbers that adds up to n based on the following conditions:

Only numbers from the range [1, 9] used.
Each number can only be used at most once.
Note: You can return the combinations in any order, the driver code will print them in sorted order.

Examples:

Input: n = 9, k = 3
Output: [[1, 2, 6], [1, 3, 5], [2, 3, 4]]
Explanation: There are three valid combinations of 3 numbers that sum to 9: [1 ,2, 6], [1, 3, 5] and [2, 3, 4].
Input: n = 3, k = 3
Output: []
Explanation: It is not possible to pick 3 distinct numbers from 1 to 9 that sum to 3, so no valid combinations exist.
Constraints:
1 ≤ n ≤ 50
1 ≤ k ≤ 9

</pre>

---
```
class Solution:
    def solve(self,n,digit,temp,res,k):
        if len(temp)==k:
            if n==0:
                res.append(temp.copy())
            return
        if n<=0 or digit==0:
            return
        temp.append(digit)
        self.solve(n-digit,digit-1,temp,res,k)
        temp.pop()
        self.solve(n,digit-1,temp,res,k)

    def combinationSum(self, n, k):
        res=[]
        self.solve(n,9,[],res,k)
        return res
        
        
```
---
