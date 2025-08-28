# 28-08-2025
---
## Maximize Number of 1's
Difficulty: MediumAccuracy: 39.46%Submissions: 67K+Points: 4Average Time: 20m
<pre>
Given a binary array arr[] containing only 0s and 1s and an integer k, you are allowed to flip at most k 0s to 1s. Find the maximum number of consecutive 1's that can be obtained in the array after performing the operation at most k times.

Examples:

Input: arr[] = [1, 0, 1], k = 1
Output: 3
Explanation: By flipping the zero at index 1, we get the longest subarray from index 0 to 2 containing all 1’s.
Input: arr[] = [1, 0, 0, 1, 0, 1, 0, 1], k = 2
Output: 5
Explanation: By flipping the zeroes at indices 4 and 6, we get the longest subarray from index 3 to 7 containing all 1’s.
Input: arr[] = [1, 1], k = 2
Output: 2
Explanation: Since the array is already having the max consecutive 1's, hence we dont need to perform any operation. Hence the answer is 2.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ k ≤ arr.size()
0 ≤ arr[i] ≤ 1
</pre>

---
```
class Solution:
    def maxOnes(self, arr, k):
        # code here
        m=0
        left=0
        kk=k
        for right,ve in enumerate(arr):
            if ve==0:
                kk-=1
            if kk<0:
                if arr[left]==0:
                    kk+=1
                left+=1
            if kk>=0:
                m=max(m,right-left+1)
        return m
 

```
---
