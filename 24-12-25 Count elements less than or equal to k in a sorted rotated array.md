# 24-12-25
---
## Count elements less than or equal to k in a sorted rotated array
Difficulty: MediumAccuracy: 58.52%Submissions: 10K+Points: 4Average Time: 15m
<pre>

Given a sorted array arr[] containing distinct positive integers that has been rotated at some unknown pivot, and a value x. Your task is to count the number of elements in the array that are less than or equal to x.

Examples:

Input: arr[] = [4, 5, 8, 1, 3], x = 6
Output: 4
Explanation: 1, 3, 4 and 5 are less than 6, so the count of all elements less than 6 is 4.
Input: arr[] = [6, 10, 12, 15, 2, 4, 5], x = 14
Output: 6
Explanation: All elements except 15 are less than 14, so the count of all elements less than 14 is 6.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ arr[i], x ≤ 109


	
</pre>

---
```

class Solution:
    def countLessEqual(self, arr, x):
        #code here
        arr.sort()
        n = len(arr)
        count = 0
    
        for i in range(n):
             if arr[i] > x:
                  break
             count += 1
    
        return count

        
```
---
