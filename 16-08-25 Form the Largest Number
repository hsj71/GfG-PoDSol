# 16-08-2025
---
## Form the Largest Number
Difficulty: MediumAccuracy: 37.82%Submissions: 183K+Points: 4
<pre>
Given an array of integers arr[] representing non-negative integers, arrange them so that after concatenating all of them in order, it results in the largest possible number. Since the result may be very large, return it as a string.

Examples:

Input: arr[] = [3, 30, 34, 5, 9]
Output: 9534330
Explanation: Given numbers are [3, 30, 34, 5, 9], the arrangement [9, 5, 34, 3, 30] gives the largest value.
Input: arr[] = [54, 546, 548, 60]
Output: 6054854654
Explanation: Given numbers are [54, 546, 548, 60], the arrangement [60, 548, 546, 54] gives the largest value.
Input: arr[] = [3, 4, 6, 5, 9]
Output: 96543
Explanation: Given numbers are [3, 4, 6, 5, 9], the arrangement [9, 6, 5, 4, 3] gives the largest value.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ arr[i] ≤ 105
</pre>

---
```
class Solution:

	def findLargest(self, arr):
	    # code here
	    s=list(map(str,arr))
        s.sort(key=lambda x : x*10 ,reverse=True)
        result="".join(s)
        if result[0]=="0":
            return 0
        else:
            return result
        
            
```
---
