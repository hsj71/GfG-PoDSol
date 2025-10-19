# 01-09-2025
---
## Sum of Mode
Difficulty: HardAccuracy: 54.28%Submissions: 11K+Points: 8Average Time: 20m
<pre>
Given an array arr[] of positive integers and an integer k. You have to find the sum of the modes of all the subarrays of size k.
Note: The mode of a subarray is the element that occurs with the highest frequency. If multiple elements have the same highest frequency, the smallest such element is considered the mode.

Examples:

Input: arr[] = [1, 2, 3, 2, 5, 2, 4, 4], k = 3
Output: 13
Explanation: The mode of each k size subarray is [1, 2, 2, 2, 2, 4] and sum of all modes is 13.
Input: arr[] = [1, 2, 1, 3, 5], k = 2
Output: 6
Explanation: The mode of each k size subarray is [1, 1, 1, 3] and sum of all modes is 6.
Constraints:
1 ≤ k ≤ arr.size() ≤105
1 ≤ arr[i] ≤ 105
</pre>

---
```
class Solution:
    def sumOfModes(self, arr, k):
        # code here
        from heapq import heappop,heappush
        from collections import defaultdict
        d=defaultdict(int)
        i=0
        h=[]
        n=len(arr)
        ans=0
        for j in range(n):
            d[arr[j]]+=1
            if j>=k:
                d[arr[j-k]]-=1
            heappush(h,(-d[arr[j]],arr[j]))
            
            while d[h[0][1]]!=-h[0][0]:
                heappop(h)
            if j>=k-1:
                ans+=h[0][1]
        return ans

```
---
