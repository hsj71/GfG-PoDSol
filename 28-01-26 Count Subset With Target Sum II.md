# 28-01-26
# Count Subset With Target Sum II
Difficulty: MediumAccuracy: 43.16%Submissions: 18K+Points: 4

```

Given an array arr[] and an integer k, find the count of subsets whose sum is equals to k.

Note: It is guaranteed that the no of valid subsets will fit within a 32-bit integer.

Examples:

Input: arr[] = [1, 3, 2], k = 3
Output: 2
Explanation: The two subsets whose sum is equals to k are [1, 2] and [3].
Input: arr[] = [4, 2, 3, 1, 2], k = 4
Output: 3
Explanation: The three subsets whose sum is equals to k are [4], [2, 2] and [3, 1].
Input: arr[] = [10, 20, 30], k = 25
Output: 0
Explanation: No subsets exits with sum equals to k.
Constraints:
1 ≤ arr.size() ≤ 40
-107 ≤ arr[i], k ≤ 107

```
---
```
class Solution:
    def solve(self,arr,n,sums,curr):
        if n==0:
            sums[curr]=sums.get(curr,0)+1
            return
        self.solve(arr,n-1,sums,curr)
        self.solve(arr,n-1,sums,curr+arr[n-1])
        
    def sums(self, arr):
        n=len(arr)
        sums={}
        self.solve(arr,n,sums,0)
        return sums
        
    def countSubset(self, arr, k):
        n=len(arr)
        mid=n//2
        left=arr[:mid]
        right=arr[mid:]
        left_sums=self.sums(left)
        right_sums=self.sums(right)
        ans=0
        for s in left_sums:
            ans+=left_sums[s]*right_sums.get(k-s,0)
        return ans
```
