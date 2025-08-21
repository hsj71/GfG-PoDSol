# 21-08-2025
---
## Maximize the minimum difference between k elements
Difficulty: MediumAccuracy: 65.42%Submissions: 10K+Points: 4
<pre>
Given an array arr[] of integers and an integer k, select k elements from the array such that the minimum absolute difference between any two of the selected elements is maximized. Return this maximum possible minimum difference.

Examples:

Input: arr[] = [2, 6, 2, 5], k = 3
Output: 1
Explanation: 3 elements out of 4 elements are to be selected with a minimum difference as large as possible. Selecting 2, 2, 5 will result in minimum difference as 0. Selecting 2, 5, 6 will result in minimum difference as 6 - 5 = 1.
Input: arr[] = [1, 4, 9, 0, 2, 13, 3], k = 4
Output: 4
Explanation: Selecting 0, 4, 9, 13 will result in minimum difference of 4, which is the largest minimum difference possible.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ arr[i] ≤ 106
2 ≤ k ≤ arr.size() 
</pre>

---
```
class Solution:
    def canPlace(self,arr,k,d):
        n=len(arr)
        count=1
        last=arr[0]
        for i in range(1,n):
            if arr[i]-last>=d:
                count+=1
                last=arr[i]
            if count>=k:
                return True
        return False
    
    def maxMinDiff(self, arr, k):
        arr.sort()
        n=len(arr)
        l,h=0,arr[-1]-arr[0]
        ans=0
        while l<=h:
            mid=(l+h)//2
            if self.canPlace(arr,k,mid):
                ans=mid
                l=mid+1
            else:
                h=mid-1
        return ans  

```
---
