# 10-12-25
---
## Missing And Repeating
Difficulty: EasyAccuracy: 24.83%Submissions: 664K+Points: 2Average Time: 30m
<pre>

Given an unsorted array arr[] of size n, containing elements from the range 1 to n, it is known that one number in this range is missing, and another number occurs twice in the array, find both the duplicate number and the missing number.

Examples:

Input: arr[] = [2, 2]
Output: [2, 1]
Explanation: Repeating number is 2 and the missing number is 1.
Input: arr[] = [1, 3, 3] 
Output: [3, 2]
Explanation: Repeating number is 3 and the missing number is 2.
Input: arr[] = [4, 3, 6, 2, 1, 1]
Output: [1, 5]
Explanation: Repeating number is 1 and the missing number is 5.
Constraints:
2 ≤ n ≤ 106
1 ≤ arr[i] ≤ n



    
</pre>

---
```

class Solution:
    def findTwoElement(self, arr):
        # code here
        from collections import Counter
        d=Counter(arr)
        res=[0,0]
        l=len(arr)
        for i in range(1,l+1):
            if i in d and d[i]==2:
                res[0]=i
            elif i not in d:
                res[1]=i
        return res
        
```
---
