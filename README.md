# 20-09-2025
---
## Longest Subarray Length
Difficulty: MediumAccuracy: 45.14%Submissions: 20K+Points: 4

<pre>
You are given an array of integers arr[]. Your task is to find the length of the longest subarray such that all the elements of the subarray are smaller than or equal to the length of the subarray.

Examples:

Input: arr[] = [1, 2, 3]
Output: 3
Explanation: The longest subarray is the entire array itself, which has a length of 3. All elements in the subarray are less than or equal to 3.
Input: arr[] = [6, 4, 2, 5]
Output: 0
Explanation: There is no subarray where all elements are less than or equal to the length of the subarray. The longest subarray is empty, which has a length of 0.
Constraints:
1 ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 109


	
</pre>

---
```
class Solution:
    def longestSubarray(self, arr):
        # code here
        stack = []
        nge_left = [-1] * len(arr)
        for i in range(len(arr)-1, -1, -1):
            while stack and arr[stack[-1]] < arr[i]:
                nge_left[stack.pop()] = i
            stack.append(i)

        stack = []
        nge_right = [len(arr)] * len(arr)
        for i in range(len(arr)):
            while stack and arr[stack[-1]] < arr[i]:
                nge_right[stack.pop()] = i
            stack.append(i)

        maxi = 0
        for i in range(len(arr)):
            l = nge_right[i] - nge_left[i] - 1
            v = arr[i]
            if v <= l:
                maxi = max(maxi, l)
        return maxi
        
        
```
---
