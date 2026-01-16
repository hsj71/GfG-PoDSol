# 16-01-26
---
## Candy
Difficulty: HardAccuracy: 55.27%Submissions: 48K+Points: 8Average Time: 45m
<pre>

Minimum Number of Workers
Difficulty: MediumAccuracy: 64.13%Submissions: 8K+Points: 4
You are given an array arr[], where arr[i] denotes the range of working hours a person at position i can cover.

If arr[i] ≠ -1, the person at index i can work and cover the time interval [i - arr[i], i + arr[i]].
If arr[i] = -1, the person is unavailable and cannot cover any time.
The task is to find the minimum number of people required to cover the entire working day from 0 to n - 1. If it is not possible to fully cover the day, return -1.

Examples:

Input: arr[] = [1, 2, 1, 0]
Output: 1
Explanation: The person at index 1 can cover the interval [-1, 3]. After adjusting to valid bounds, this becomes [0, 3], which fully covers the entire working day 0 to n -1. Therefore, only 1 person is required to cover the whole day.
Input: arr[] = [2, 3, 4, -1, 2, 0, 0, -1, 0]
Output: -1
Explanation: Persons up to index 2 cover interval [0…6], but working hour 7 cannot be cover as arr[7] = -1, Since the 7th hour cannot be covered by any person, it is impossible to cover the full working day.
Input: arr[] = [0, 1, 0, -1]
Output: -1
Explanation: The last hour cannot be covered by any person, so it is impossible to cover the full working day.
Constraints:
1 ≤ arr.size() ≤105
-1 ≤ arr[i] ≤ arr.size()
    
</pre>

---
```
class Solution:
    def minMen(self, arr):
        #code here 
        stack = []
        for i in range(len(arr)):
            left = max(0, i - arr[i])
            right = min(len(arr) - 1, i + arr[i])
            while stack and stack[-1][0] >= left and stack[-1][1] <= right:
                stack.pop()
            if len(stack) == 0:
                stack.append([left, right])
            elif stack[-1][1] < right:
                stack.append([max(stack[-1][1] + 1, left), right])
        if stack[0][0] == 0 and stack[-1][1] == len(arr) - 1:
            for i in range(1, len(stack)):
                if stack[i][0] - stack[i - 1][1] > 1:
                    return -1
            return len(stack)
        return -1
        
```
---
