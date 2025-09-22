# 22-09-2025
---
## Max of min for every window size
Difficulty: HardAccuracy: 42.9%Submissions: 75K+Points: 8Average Time: 45m

<pre>
You are given an integer array arr[], the task is to find the maximum of minimum values for every window size k where 1≤ k ≤ arr.size().

For each window size k, consider all contiguous subarrays of length k, determine the minimum element in each subarray, and then take the maximum among all these minimums.

Return the results as an array, where the element at index i represents the answer for window size i+1.

Examples :

Input: arr[] = [10, 20, 30, 50, 10, 70, 30]
Output: [70, 30, 20, 10, 10, 10, 10] 
Explanation: 
Window size 1: minimums are [10, 20, 30, 50, 10, 70, 30], maximum of minimums is 70.
Window size 2: minimums are [10, 20, 30, 10, 10, 30], maximum of minimums is 30.
Window size 3: minimums are [10, 20, 10, 10, 10], maximum of minimums is 20.
Window size 4–7: minimums are [10, 10, 10, 10], maximum of minimums is 10.
Input: arr[] = [10, 20, 30]
Output: [30, 20, 10]
Explanation: 
Window size 1: minimums of  [10], [20], [30], maximum of minimums is 30.
Window size 2: minimums of [10, 20], [20,30], maximum of minimums is 20.
Window size 3: minimums of [10,20,30], maximum of minimums is 10.
Constraints:
1 ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 106

	
</pre>

---
```
class Solution:
    def maxOfMins(self, arr):
        n = len(arr)
        left = [-1] * n
        right = [n] * n

        stack = []
        push, pop = stack.append, stack.pop

        for i in range(n):
            while stack and arr[stack[-1]] >= arr[i]:
                pop()
            left[i] = stack[-1] if stack else -1
            push(i)

        stack.clear()
        push, pop = stack.append, stack.pop

        for i in range(n - 1, -1, -1):
            while stack and arr[stack[-1]] >= arr[i]:
                pop()
            right[i] = stack[-1] if stack else n
            push(i)

        ans = [0] * (n + 1)
        for i in range(n):
            win = right[i] - left[i] - 1
            if arr[i] > ans[win]:
                ans[win] = arr[i]

        for i in range(n - 1, 0, -1):
            if ans[i] < ans[i + 1]:
                ans[i] = ans[i + 1]

        return ans[1:]
        
        
```
---
