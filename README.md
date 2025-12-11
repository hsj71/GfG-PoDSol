# 11-12-25
---
## Construct an array from its pair-sum array
Difficulty: EasyAccuracy: 56.62%Submissions: 9K+Points: 2Average Time: 10m
<pre>

Given a pair-sum array arr[] construct the original array. A pair-sum array for an array is the array that contains sum of all pairs in ordered form, i.e., arr[0] is sum of res[0] and res[1], arr[1] is sum of res[0] and res[2] and so on.

Note: If the size of original array res[] is n, then the size of pair-sum array arr[] would be n * (n -1) /2. We may assume that the pair-sum array arr[] is appropriate in size.
Note that, if the original array is correct then the driver code will print true, else false;

Examples:

Input: arr[] = [4, 5, 3]
Output: true
Explanation: A valid original array is [3, 1, 2], pairwise sums are (3 + 1), (3 + 2) and (1 + 2).
Input: arr[] = [3]
Output: true
Explanation: One of the valid original array is [1, 2].
Constraints: 
1 ≤ n ≤ 103
1 ≤ arr[i] ≤ 109



    
</pre>

---
```

class Solution:
    def constructArr(self, arr):
        # code here
        m = len(arr)
        disc = 1 + 8 * m
        r = int(disc**0.5)
        while (r+1)*(r+1) <= disc:
            r += 1
        while r*r > disc:
            r -= 1
        n = (1 + r) // 2

        if n == 2:
            return [0, arr[0]]
       
        a0 = (arr[0] + arr[1] - arr[n-1]) // 2
        res = [0] * n
        res[0] = a0

        for i in range(1, n):
            res[i] = arr[i-1] - a0

        return res
        
```
---
