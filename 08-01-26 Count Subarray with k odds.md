# 08-01-26
---
## Count Subarray with k odds
Difficulty: MediumAccuracy: 51.12%Submissions: 18K+Points: 4Average Time: 20m
<pre>

You are given an array arr[] of positive integers and an integer k. You have to count the number of subarrays that contain exactly k odd numbers.

Examples:

Input: arr[] = [2, 5, 6, 9], k = 2
Output: 2
Explanation: There are 2 subarrays with 2 odds: [2, 5, 6, 9] and [5, 6, 9].
Input: arr[] = [2, 2, 5, 6, 9, 2, 11], k = 2
Output: 8
Explanation: There are 8 subarrays with 2 odds: [2, 2, 5, 6, 9], [2, 5, 6, 9], [5, 6, 9], [2, 2, 5, 6, 9, 2], [2, 5, 6, 9, 2], [5, 6, 9, 2], [6, 9, 2, 11] and [9, 2, 11].
Constraint:
1 ≤ k ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 109    
</pre>

---
```
class Solution:
    def countSubarrays(self, arr, k):
        # Code here
        def calculate(n):
            i , j, count, total = [0] * 4
            while j < len(arr):
                count += arr[j] % 2
                while count > n:
                    count -= 1 if arr[i] % 2 == 1 else 0
                    i +=1
                j +=1
                total += (j - i)
            return total
        return calculate(k) - calculate(k - 1)

 
        
```
---
