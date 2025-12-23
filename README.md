# 23-12-25
---
## Elements in range [a, b]
Difficulty: MediumAccuracy: 56.2%Submissions: 10K+Points: 4
<pre>


Given an unsorted array arr[] and a 2D array queries[][] of size q, where each query is in the form of [a, b]. For each query, count how many elements in arr[] lie within the range [a, b], i.e., elements satisfying a ≤ x ≤ b.

Return the results for all queries as a list of integers, where each integer corresponds to the count of elements in the respective query range.

Examples:

Input: arr[] = [1, 4, 2, 8, 5], queries[][] = [[1, 4], [3, 6], [0, 10]]
Output: [3, 2, 5]
Explanation: Query [1, 4]: Elements in range → [1, 4, 2] → Count = 3
Query [3, 6]: Elements in range → [4, 5] → Count = 2
Query [0, 10]: All elements → [1, 4, 2, 8, 5] → Count = 5
Input: arr[] = [10, 20, 30, 40, 50], queries[][] = [[5, 15], [25, 45], [10, 50]]
Output: [1, 2, 5]
Explanation: Query [5, 15]: Elements in range → [10] → Count = 1
Query [25, 45]: Elements in range → [30, 40] → Count = 2
Query [10, 50]: Elements in range → [10, 20, 30, 40, 50] → Count = 5
Constraints:
1 ≤ arr.size(), q ≤ 105
0 ≤ arr[i] ≤ 106
0 ≤ queries[i][0] ≤ queries[i][1] ≤ 106


	
</pre>

---
```

class Solution:
    def cntInRange(self, arr, queries):
        # code here
        from bisect import bisect_left, bisect_right
        l=[]
        arr.sort()
        for a,b in queries:
            l.append(bisect_right(arr,b)-bisect_left(arr,a))
        return l

        
```
---
