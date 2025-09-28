# 28-09-2025
---
## Longest Bounded-Difference Subarray
Difficulty: MediumAccuracy: 58.27%Submissions: 25K+Points: 4

<pre>

Given an array of positive integers arr[] and a non-negative integer x, the task is to find the longest sub-array where the absolute difference between any two elements is not greater than x.
If multiple such subarrays exist, return the one that starts at the smallest index.

Examples:

Input: arr[] = [8, 4, 5, 6, 7], x = 3 
Output: [4, 5, 6, 7] 
Explanation: The sub-array described by index [1..4], i.e. [4, 5, 6, 7]
contains no two elements whose absolute differnce is greater than 3.
Input: arr[] = [1, 10, 12, 13, 14], x = 2 
Output: [12, 13, 14] 
Explanation: The sub-array described by index [2..4], i.e. [12, 13, 14]
contains no two elements whose absolute differnece is greater than 2. 
Constraints:
1 ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 109
0 ≤ x ≤ 109



	
</pre>

---
```
class Solution:
    def longestSubarray(self, arr, x):
        #code here
        from collections import deque
        n = len(arr)
        max_deque = deque()
        min_deque = deque()
        left = 0
        best_len = 0
        best_start = 0

        for right in range(n):
            # Maintain decreasing order in max_deque
            while max_deque and arr[right] > arr[max_deque[-1]]:
                max_deque.pop()
            max_deque.append(right)

            # Maintain increasing order in min_deque
            while min_deque and arr[right] < arr[min_deque[-1]]:
                min_deque.pop()
            min_deque.append(right)

            # Shrink window if condition violated
            while arr[max_deque[0]] - arr[min_deque[0]] > x:
                left += 1
                if max_deque[0] < left:
                    max_deque.popleft()
                if min_deque[0] < left:
                    min_deque.popleft()

            # Update best window
            if right - left + 1 > best_len:
                best_len = right - left + 1
                best_start = left

        return arr[best_start: best_start + best_len]
        
        
```
---
