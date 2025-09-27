# 27-09-2025
---
## Minimum K Consecutive Bit Flips
Difficulty: HardAccuracy: 64.29%Submissions: 9K+Points: 8

<pre>


You are given a binary array arr[] (containing only 0's and 1's) and an integer k. In one operation, you can select a contiguous subarray of length k and flip all its bits (i.e., change every 0 to 1 and every 1 to 0).

Your task is to find the minimum number of such operations required to make the entire array consist of only 1's. If it is not possible, return -1.

Examples:

Input: arr = [1, 1, 0, 0, 0, 1, 1, 0, 1, 1, 1], k = 2
Output: 4 
Explanation: 4 operations are required to convert all 0's to 1's.
Select subarray [2, 3] and flip all bits resulting array will be [1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1]
Select subarray [4, 5] and flip all bits resulting array will be [1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1]
Select subarray [5, 6] and flip all bits resulting array will be [1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1]
Select subarray [6, 7] and flip all bits resulting array will be [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
Input: arr = [0, 0, 1, 1, 1, 0, 0], k = 3
Output: -1
Explanation: It is not possible to convert all elements to 1's by performing any number of operations.
Constraints:
1 ≤ arr.size() ≤ 106
1 ≤ k ≤ arr.size()



	
</pre>

---
```
class Solution:
    def kBitFlips(self, arr, k):
        # code here
        n = len(arr)
        flipped = [0] * n
        count = 0
        flip = 0

        for i in range(n):
            if i >= k:
                flip ^= flipped[i - k]
            if arr[i] ^ flip == 0:
                if i + k > n:
                    return -1
                count += 1
                flip ^= 1
                flipped[i] = 1

        return count
        
        
```
---
