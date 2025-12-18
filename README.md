# 18-12-25
---
## Sort in specific order
Difficulty: MediumAccuracy: 52.55%Submissions: 52K+Points: 4
<pre>

Given an array arr[] of positive integers. Your have to sort them so that the first part of the array contains odd numbers sorted in descending order, and the rest of the portion contains even numbers sorted in ascending order.

Examples:

Input: arr[] = [1, 2, 3, 5, 4, 7, 10]
Output: [7, 5, 3, 1, 2, 4, 10]
Explanation: 7, 5, 3, 1 are odd numbers in descending order and 2, 4, 10 are even numbers in ascending order.
Input: arr[] = [0, 4, 5, 3, 7, 2, 1]
Output: [7, 5, 3, 1, 0, 2, 4]
Explanation: 7, 5, 3, 1 are odd numbers in descending order and 0, 2, 4 are even numbers in ascending order.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ arri ≤ 109
	
</pre>

---
```

class Solution:
    def sortIt(self, arr):
        # code here
        arr.sort(key=lambda x : (1- x%2, -x if x%2 else x))
        return arr
    

        
```
---
