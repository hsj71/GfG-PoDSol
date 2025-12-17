# 17-12-25
---
## Overlapping Intervals
Difficulty: MediumAccuracy: 57.41%Submissions: 123K+Points: 4Average Time: 20m
<pre>

Given an array of Intervals arr[][], where arr[i] = [starti, endi]. The task is to merge all of the overlapping Intervals.

Examples:

Input: arr[][] = [[1, 3], [2, 4], [6, 8], [9, 10]]
Output: [[1, 4], [6, 8], [9, 10]]
Explanation: In the given intervals we have only two overlapping intervals here, [1, 3] and [2, 4] which on merging will become [1, 4]. Therefore we will return [[1, 4], [6, 8], [9, 10]].
Input: arr[][] = [[6, 8], [1, 9], [2, 4], [4, 7]]
Output: [[1, 9]]
Explanation: In the given intervals all the intervals overlap with the interval [1, 9]. Therefore we will return [1, 9].
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ starti ≤ endi ≤ 106



    
</pre>

---
```

class Solution:
	def mergeOverlap(self, arr):
		# Code here
		arr.sort()
        ans = []
        running = arr[0]
        for i in range(1, len(arr)):
            if running[1] < arr[i][0]:
                ans.append(running)
                running = arr[i]
            else:
                running = (min(running[0], arr[i][0]), max(running[1], arr[i][1]))
              
        return ans + [running]

        
```
---
