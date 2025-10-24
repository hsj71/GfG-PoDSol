# 24-10-25
---
## Split Array Subsequences
Difficulty: MediumAccuracy: 56.37%Submissions: 8K+Points: 4

<pre>


Given a sorted integer array arr[] and an integer k, determine if it is possible to split the array into one or more consecutive subsequences such that:

Each subsequence consists of consecutive integers (each number is exactly one greater than the previous).
Every subsequence has a length of at least k.
Return true if such a split is possible, otherwise return false.

Examples :

Input: arr[] = [2, 2, 3, 3, 4, 5], k = 2
Output: true
Explanation: arr can be split into three subsequence of length k - [2, 3], [2, 3], [4, 5].
Input: arr[] = [1, 1, 1, 1, 1], k = 4
Output: false
Explanation: It is impossible to split arr into consecutive increasing subsequences of length 4 or more.
Constraints:
1 ≤ arr.size()  ≤ 105
1 ≤ arr[i] ≤ 105
1 ≤  k ≤  arr.size() 
    
</pre>

---
```
from collections import Counter, defaultdict

class Solution:
    def isPossible(self, arr, k):
        freq = Counter(arr)
        end = defaultdict(int)

        for num in arr:
            if freq[num] == 0:
                continue

            # Try to extend a previous subsequence
            if end[num - 1] > 0:
                end[num - 1] -= 1
                end[num] += 1
                freq[num] -= 1
            else:
                # Try to start a new subsequence of length k
                for next_num in range(num, num + k):
                    if freq[next_num] <= 0:
                        return False
                    freq[next_num] -= 1
                end[num + k - 1] += 1

        return True
        
```
---
