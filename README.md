# 07-11-25
---
## Weighted Job Scheduling
Difficulty: MediumAccuracy: 70.0%Submissions: 6K+Points: 4

<pre>


Given a 2D array jobs[][] of size n × 3, where each row represents a single job with the following details:

jobs[i][0] : Start time of the job
jobs[i][1] : End time of the job
jobs[i][2] : Profit earned by completing the job
Find the maximum profit you can earn by scheduling non-overlapping jobs.

Note: Two jobs are said to be non-overlapping if the end time of one job is less than or equal to the start time of the next job. If a job ends at time X, another job can start exactly at time X.

Examples:

Input: jobs[][] =  [[1, 2, 50], 
                 [3, 5, 20],
                 [6, 19, 100],
                 [2, 100, 200]] 
Output: 250
Explanation: The first and fourth jobs with the time range [1, 2] and [2, 100] can be chosen to give maximum profit of 50 + 200 = 250.
Input: jobs[][] =  [[1, 3, 60], 
                 [2, 5, 50],
                 [4, 6, 70],
                 [5, 7, 30]] 
Output: 130
Explanation: The first and third jobs with the time range [1, 3] and [4, 6] can be chosen to give maximum profit of 60 + 70 = 130.
Constraints:
1 ≤ jobs.size() ≤ 105
1 ≤ jobs[i][0] < jobs[i][1] ≤ 109
1 ≤ jobs[i][2] ≤ 104
    
</pre>

---
```
class Solution: 
    def maxProfit(self, jobs):
        # code here
        from bisect import bisect_left
        n = len(jobs)
        jobs.sort(key=lambda j: (j[1], j[0]))
        dp = [0]*(n+1)
        for i in range(n):
            if i == 0:
                dp[i+1] = jobs[i][2]
                continue
            dp[i+1] = dp[i]
            start_time = jobs[i][0]
            j = bisect_left(jobs, start_time+1, key=lambda x: x[1])-1
            dp[i+1] = max(dp[i+1], jobs[i][2]+dp[j+1])
        return dp[-1]
        
```
---
