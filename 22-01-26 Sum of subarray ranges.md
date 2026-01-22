# 22-01-26
---
## Sum of subarray ranges
Difficulty: MediumAccuracy: 50.82%Submissions: 14K+Points: 4Average Time: 30m
<pre>


Given an integer array arr[], the range of a subarray is defined as the difference between the largest and smallest elements within that subarray. Your task is to return the sum of the ranges of all possible subarrays in the array.

Note: It is guaranteed that the result will fit within a 32-bit integer.

Examples:

Input: arr[] = [1, 2, 3]
Output: 4
Explanation: The 6 subarray of arr are the following :
[1], range = largest - smallest = 1 - 1 = 0
[2], range = largest - smallest = 2 - 2 = 0
[3], range = largest - smallest = 3 - 3 = 0
[1, 2], range = largest - smallest = 2 - 1 = 1
[2, 3], range = largest - smallest = 3 - 2 = 1
[1, 2, 3], range = largest - smallest = 3 - 1 = 2
Sum of all ranges is 0 + 0 + 0 + 1 + 1 + 2 = 4
Input: arr[] = [-32, 0, -2, 72]
Output: 318
Explanation: 
[-32], range = largest - smallest = -32 - (-32) = 0
[-32, 0], range = largest - smallest = 0 - (-32) = 32
[-32, 0, -2], range = largest - smallest = 0 - (-32) = 32
[-32, 0, -2, 72], range= largest - smallest = 72 - (-32) = 104
[0], range = largest - smallest = 0 - 0 = 0
[0, -2], range = largest - smallest = 0 - (-2) = 2
[0, -2, 72], range = largest - smallest = 72 - (-2) = 74
[-2], range = largest - smallest = -2 - (-2) = 0
[-2, 72], range = largest - smallest = 72 - (-2) = 74
[72], range = largest - smallest = 72 - 72 = 0
Sum of all ranges is 0 + 32 + 32 + 104 + 0 + 2 + 74 + 0 + 74 + 0 = 318
Constraints:
1 ≤ arr.size() ≤ 106
10-9 ≤ arr[i]  ≤ 109
    
</pre>

---
```
class Solution:
    def subarrayRanges(self, arr):
        # Code here
        n = len(arr)
        def sumSubarrayMins():
            stack = []
            prev_less = [-1] * n
            next_less = [n] * n

            # Previous Less
            for i in range(n):
                while stack and arr[stack[-1]] > arr[i]:
                    stack.pop()
                prev_less[i] = stack[-1] if stack else -1
                stack.append(i)

            stack.clear()

            # Next Less or Equal
            for i in range(n - 1, -1, -1):
                while stack and arr[stack[-1]] >= arr[i]:
                    stack.pop()
                next_less[i] = stack[-1] if stack else n
                stack.append(i)

            total = 0
            for i in range(n):
                total += arr[i] * (i - prev_less[i]) * (next_less[i] - i)
            return total

        def sumSubarrayMaxs():
            stack = []
            prev_greater = [-1] * n
            next_greater = [n] * n

            # Previous Greater
            for i in range(n):
                while stack and arr[stack[-1]] < arr[i]:
                    stack.pop()
                prev_greater[i] = stack[-1] if stack else -1
                stack.append(i)

            stack.clear()

            # Next Greater or Equal
            for i in range(n - 1, -1, -1):
                while stack and arr[stack[-1]] <= arr[i]:
                    stack.pop()
                next_greater[i] = stack[-1] if stack else n
                stack.append(i)

            total = 0
            for i in range(n):
                total += arr[i] * (i - prev_greater[i]) * (next_greater[i] - i)
            return total

        return sumSubarrayMaxs() - sumSubarrayMins()
        
```
---
