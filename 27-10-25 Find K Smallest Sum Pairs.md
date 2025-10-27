# 27-10-25
---
## Find K Smallest Sum Pairs
Difficulty: MediumAccuracy: 59.44%Submissions: 9K+Points: 4

<pre>


Given two integer arrays arr1[] and arr2[] sorted in ascending order and an integer k, your task is to find k pairs with the smallest sums, such that one element of each pair belongs to arr1[] and the other belongs to arr2[].

Return the list of these k pairs, where each pair is represented as [arr1[i], arr2[j]].

Note: You can return any possible k pairs with the smallest sums, the driver code will print true if it is correct else it will print false.

Examples:

Input: arr1[] = [1, 7, 11], arr2[] = [2, 4, 6], k = 3
Output: true
Explanation: All possible combinations of elements from the two arrays are:
[1, 2], [1, 4], [1, 6], [7, 2], [7, 4], [7, 6], [11, 2], [11, 4], [11, 6]. 
Among these, the three pairs with the minimum sums are [1, 2], [1, 4], [1, 6].
Input: arr1[] = [1, 3], arr2[] = [2, 4] k = 2
Output: true
Explanation: All possible combinations are [1, 2], [1, 4], [3, 2], [3, 4]. 
Among these, the two pairs with the minimum sums are [1, 2], [3, 2].
Constraints:
1 ≤ arr1.size(), arr2.size() ≤ 5*104
1 ≤ arr1[i], arr2[j] ≤ 109
1 ≤ k ≤ 103
    
</pre>

---
```
from heapq import *
class Solution:
    def kSmallestPair(self, arr1, arr2, k):
        m, n = len(arr1), len(arr2)
        heap = []
        ans = []
        for i in range(min(k, m)):
            heappush(heap, (arr1[i] + arr2[0], i, 0))
        while k and heap:
            _, i, j = heappop(heap)
            ans.append((arr1[i], arr2[j]))
            if j + 1 < n:
                heappush(heap, (arr1[i] + arr2[j + 1], i, j + 1))
            k-=1
        return ans
        
```
---
