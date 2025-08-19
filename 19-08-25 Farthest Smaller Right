# 19-08-2025
---
## Farthest Smaller Right
Difficulty: MediumAccuracy: 50.08%Submissions: 13K+Points: 4
<pre>
You are given an array arr[]. For each element at index i (0-based indexing), find the farthest index j to the right (i.e., j > i) such that arr[j] < arr[i]. If no such index exists for a given position, return -1 for that index. Return the resulting array of answers.

Examples:

Input: arr[] = [2, 5, 1, 3, 2]
Output: [2, 4, -1, 4, -1]
Explanation: arr[0] = 2: Farthest smaller element to the right is arr[2] = 1.
arr[1] = 5: Farthest smaller element to the right is arr[4] = 2.
arr[2] = 1: No smaller element to the right → -1.
arr[3] = 3: Farthest smaller element to the right is arr[4] = 2.
arr[4] = 2: No elements to the right → -1.
Input: arr[] = [2, 3, 5, 4, 1] 
Output: [4, 4, 4, 4, -1]
Explanation: arr[4] is the farthest smallest element to the right for arr[0], arr[1], arr[2] and arr[3].
Constraints:
1 ≤ arr.size() ≤ 106
1 ≤ arr[i] ≤ 106
</pre>

---
```
class Solution:
    def bs(self,arr,l,h,x):
            while l<=h:
                mid=(l+h)//2
                if arr[mid]>=x:
                    h=mid-1
                else:
                    l=mid+1
            return l-1
    def farMin(self, arr):
        # Code Here
        n=len(arr)
        right=[0]*n
        right[n-1]=arr[n-1]
        for i in range(n-2,-1,-1):
            right[i]=min(arr[i],right[i+1])
        ans=[None]*n
        for i in range(n):
            if i==n-1 or right[i+1]>=arr[i]:
                ans[i]=-1
            else:
                ans[i]=self.bs(right,i+1,n-1,arr[i])
        return ans
            
```
---
