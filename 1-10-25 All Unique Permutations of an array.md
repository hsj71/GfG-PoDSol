# 1-10-2025
---
## All Unique Permutations of an array
Difficulty: MediumAccuracy: 52.85%Submissions: 49K+Points: 4Average Time: 15m

<pre>

Given an array arr[] that may contain duplicates. Find all possible distinct permutations of the array in sorted order.
Note: A sequence A is greater than sequence B if there is an index i for which Aj = Bj for all j<i and Ai > Bi.

Examples:

Input: arr[] = [1, 3, 3]
Output: [[1, 3, 3], [3, 1, 3], [3, 3, 1]]
Explanation: These are the only possible distinct permutations for the given array.
Input: arr[] = [2, 3]
Output: [[2, 3], [3, 2]]
Explanation: These are the only possible distinct permutations for the given array.
Constraints:
1 ≤ arr.size() ≤ 9


</pre>

---
```
class Solution:
    def uniquePerms(self, arr):
        # code here 
        arr.sort()
        n = len(arr)
        res = []
        used = [False]*n

        def backtrack(path):
            if len(path) == n:
                res.append(path[:])
                return
            for i in range(n):
                if used[i]: 
                    continue
                if i > 0 and arr[i] == arr[i-1] and not used[i-1]:
                    continue
                used[i] = True
                path.append(arr[i])
                backtrack(path)
                path.pop()
                used[i] = False

        backtrack([])
        return res
        
        
```
---
