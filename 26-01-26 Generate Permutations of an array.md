# 26-01-26
---
## Generate Permutations of an array
Difficulty: MediumAccuracy: 82.08%Submissions: 8K+Points: 4
<pre>


Given an array arr[] of unique elements. Generate all possible permutations of the elements in the array.
Note: You can return the permutations in any order, the driver code will print them in sorted order.

Examples:

Input: arr[] = [1, 2, 3]
Output: [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
Explanation: There are 6 possible permutations (3! = 6) of the array.
Input: arr[] = [1, 3]
Output: [[1, 3], [3, 1]]
Explanation: There are 2 possible permutations (2! = 2) of the array.
Constraints:
1 ≤ arr.size() ≤ 9
    
</pre>

---
```
from itertools import permutations as pr
class Solution:
    def permuteDist(self, arr):
        # code here
        return list(pr(arr))
        
```
---
