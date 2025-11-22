# 15-08-2025
---
## Insert Interval
Difficulty: MediumAccuracy: 50.61%Submissions: 52K+Points: 4Average Time: 30m
<pre>
Geek has an array of non-overlapping intervals intervals[][] where intervals[i] = [starti , endi] represent the start and the end of the ith event and intervals is sorted in ascending order by starti . He wants to add a new interval newInterval[] = [newStart, newEnd] where newStart and newEnd represent the start and end of this interval.
Help Geek to insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Examples:

Input: intervals[][] = [[1, 3], [4, 5], [6, 7], [8, 10]], newInterval[] = [5, 6]
Output: [[1, 3], [4, 7], [8, 10]]
Explanation: The newInterval [5, 6] overlaps with [4, 5] and [6, 7]. So, they are merged into one interval [4, 7].
Input: intervals[][] = [[1, 2], [3, 5], [6, 7], [8, 10], [12, 16]], newInterval[] = [4, 9]
Output: [[1, 2], [3, 10], [12, 16]]
Explanation: The new interval [4, 9] overlaps with [3, 5], [6, 7] and [8, 10]. So, they are merged into one interval [3, 10].
Constraints:
1 ≤ intervals.size() ≤  105
0 ≤ starti ≤ endi ≤ 109
0 ≤ newStart ≤ newEnd ≤ 109
</pre>

---
```
class Solution:
    def insertInterval(self, intervals, newInterval):
        # Code here
        l, r = 0, len(intervals)-1
        ansl = -1
        while l<=r:
            mid = (l+r)//2
            
            if intervals[mid][0] <= newInterval[0] <= intervals[mid][1]:
                ansl = mid
                break
            elif intervals[mid][1] < newInterval[0]:
                l = mid + 1
            else:
                r = mid - 1
        
        nl, nr = 0, len(intervals)-1
        ansr = -1
        while nl<=nr:
            mid = (nl+nr)//2
            
            if intervals[mid][0] <= newInterval[1] <= intervals[mid][1]:
                ansr = mid
                break
            elif intervals[mid][0] < newInterval[1]:
                nl = mid + 1
            else:
                nr = mid - 1
            #print(nl, nr)
        
        
        if ansl!=-1 and ansr!=-1:
            res = intervals[:ansl]
            res.append([intervals[ansl][0], intervals[ansr][1]])
            res += intervals[ansr+1:]
            return res
        #print(ansr, ansl)
        if ansl==-1:
            res = intervals[:l]
            if ansr==-1:
                res.append(newInterval)
                res += intervals[nr+1:]
            else:
                res.append([newInterval[0], intervals[ansr][1]])
                res += intervals[ansr+1:]
            return res
            
        res = intervals[:ansl]
        res.append([intervals[ansl][0], newInterval[1]])
        res += intervals[nr+1:]
        return res
        
            
```
---
