# 28-11-25
---
## Subset XOR
Difficulty: MediumAccuracy: 75.05%Submissions: 6K+Points: 4
<pre>


Given an positive integer n, find a subset of numbers from 1 to n (inclusive), where each number can be used at most once, such that:

The XOR of all elements in the subset is exactly n.
The size of the subset is as large as possible.
If multiple such subsets exist, choose the lexicographically smallest one.
Lexicographical Order : A subset A[] is lexicographically smaller than subset B[] if at the first index where they differ, A[i] < B[i] (based on character ASCII/Unicode values).
If all elements match but one subset ends earlier, the shorter subset is considered smaller.

Examples:

Input: n = 4
Output: [1, 2, 3, 4]
Explanation: We choose all the elements from 1 to 4. Its xor value is equal to n. This is the maximum possible size of the subset.
Input: n = 3
Output: [1, 2]
Explanation: 1 ^ 2 = 3, This is the smallest lexicographical answer possible with maximum size of subset i.e 2.
Constraints:
1 ≤ n ≤ 105
    
</pre>

---
```
class Solution:
    def subsetXOR(self, n : int):
        x = 0
        for i in range(1, n + 1):
            x ^= i
        if x == n:
            return [i for i in range(1, n + 1)]
            
        k = x ^ n
        
        if 1 <= k <= n:
            return [i for i in range(1, n + 1) if i != k]
            
        return [i for i in range(1, n)]
        
        
```
---
