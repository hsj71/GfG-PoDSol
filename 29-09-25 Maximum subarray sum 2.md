# 29-09-2025
---
## Maximum subarray sum 2
Difficulty: HardAccuracy: 57.52%Submissions: 9K+Points: 8

<pre>

You are given an array arr[] of integers and two integers a and b, You have to find the maximum possible sum of a contiguous subarray whose length is at least a and at most b.

Examples:

Input: arr[] = [4, 5, -1, -2, 6], a = 2, b = 4
Output: 9
Explanation: The subarray [4, 5] has length 2 and sum 9, which is the maximum among all subarrays of length between 2 and 4.
Input: arr[] = [-1, 3, -1, -2, 5, 3, -5, 2, 2], a = 3, b = 5
Output: 8
Explanation: The subarray [3, -1, -2, 5, 3] has length 5 and sum 8, which is the maximum among all subarrays of length between 3 and 5.
Constraints:
1 ≤ arr.size() ≤ 105
-105 ≤ arr[i] ≤ 105
1 ≤ a ≤ b ≤ arr.size()



	
</pre>

---
```
import heapq

class Solution:
    def maxSubarrSum(self, arr, a, b):
        n = len(arr)
        prefix = [0] * (n+1)
        for i in range(n):
            prefix[i+1] = prefix[i] + arr[i]

        heap = []
        res = float('-inf')

        for r in range(a, n+1):
            heapq.heappush(heap, (prefix[r-a], r-a))
            while heap and heap[0][1] < r-b:
                heapq.heappop(heap)
            res = max(res, prefix[r] - heap[0][0])

        return res
        
        
```
---
