# 06-01-26
---
## Max Xor Subarray of size K
Difficulty: MediumAccuracy: 55.63%Submissions: 13K+Points: 4Average Time: 15m
<pre>


Given an array of integers arr[]  and a number k. Return the maximum xor of a subarray of size k.

Note: A subarray is a contiguous part of any given array.

Examples:

Input: arr[] = [2, 5, 8, 1, 1, 3], k = 3
Output: 15
Explanation: arr[0] ^ arr[1] ^ arr[2] = 15, which is maximum.
Input: arr[] = [1, 2, 4, 5, 6] , k = 2
Output: 6
Explanation: arr[1] ^ arr[2] = 6, which is maximum.
Constraints:
1 ≤ arr.size() ≤ 106
0 ≤ arr[i] ≤ 106
1 ≤ k ≤ arr.size()
    
</pre>

---
```
class Solution:
    def maxSubarrayXOR(self, arr, k):
        sub = 0
        for i in range(k):
            sub ^= arr[i]
        ans = sub
        for i in range(k,len(arr)):
            sub ^= arr[i-k]
            sub ^= arr[i]
            ans = max(ans,sub)
        return ans
 
        
```
---
