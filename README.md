# 07-01-26
---
## Count distinct elements in every window
Difficulty: MediumAccuracy: 41.83%Submissions: 172K+Points: 4Average Time: 20m
<pre>

Given an integer array arr[] and a number k. Find the count of distinct elements in every window of size k in the array.

Examples:

Input: arr[] = [1, 2, 1, 3, 4, 2, 3], k = 4
Output: [3, 4, 4, 3]
Explanation:
First window is [1, 2, 1, 3], count of distinct numbers is 3.
Second window is [2, 1, 3, 4] count of distinct numbers is 4.
Third window is [1, 3, 4, 2] count of distinct numbers is 4.
Fourth window is [3, 4, 2, 3] count of distinct numbers is 3.
Input: arr[] = [4, 1, 1], k = 2
Output: [2, 1]
Explanation:
First window is [4, 1], count of distinct numbers is 2.
Second window is [1, 1], count of distinct numbers is 1.
Input: arr[] = [1, 1, 1, 1, 1], k = 3
Output: [1, 1, 1]
Explanation: Every window of size 3 in the array [1, 1, 1, 1, 1], contains only the element 1, so the number of distinct elements in each window is 1.
Constraints:
1 ≤ k ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 105


    
</pre>

---
```
class Solution:
    def countDistinct(self, arr, k):
        n=len(arr)
        res=[]
        d={}
        for i in range(k):
            if arr[i] in d:
                d[arr[i]]+=1
            else:
                d[arr[i]]=1
        l=0
        res.append(len(d))
        for r in range(k,n):
            if arr[r] in d:
                d[arr[r]]+=1
            else:
                d[arr[r]]=1
            d[arr[l]]-=1
            if d[arr[l]]==0:
                del d[arr[l]]
            l+=1
            res.append(len(d))
        return res


 
        
```
---
