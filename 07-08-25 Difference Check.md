# 07-08-2025
---
## Difference Check

Given an array arr[] of time strings in 24-hour clock format "HH:MM:SS", return the minimum difference in seconds between any two time strings in the arr[].
The clock wraps around at midnight, so the time difference between "23:59:59" and "00:00:00" is 1 second.

Examples:

Input: arr[] = ["12:30:15", "12:30:45"]
Output: 30
Explanation: The minimum time difference is 30 seconds.
Input: arr[] = ["00:00:01", "23:59:59", "00:00:05"]
Output: 2
Explanation: The time difference is minimum between "00:00:01" and "23:59:59".
Constraints:
2 ≤ arr.size() ≤ 105
arr[i] is in "HH:MM:SS" format.


---
```
class Solution:
    def minDifference(self, arr):
        def time_to_seconds(t):
            h, m, s = map(int, t.split(':'))
            return h * 3600 + m * 60 + s
    
        seconds = sorted(time_to_seconds(t) for t in arr)
        min_diff = float('inf')
        n = len(seconds)
    
        for i in range(n):
            curr = seconds[i]
            nxt = seconds[(i + 1) % n]
            diff = (nxt - curr) if i < n - 1 else (86400 - curr + seconds[0])
            min_diff = min(min_diff, diff)
    
        return min_diff
```
