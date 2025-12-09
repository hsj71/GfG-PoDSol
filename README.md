# 9-12-25
---
## Array Duplicates
Difficulty: EasyAccuracy: 18.95%Submissions: 876K+Points: 2Average Time: 20m
<pre>


Given an array arr[] of size n, containing elements from the range 1 to n, and each element appears at most twice, return an array of all the integers that appears twice.

Note: You can return the elements in any order but the driver code will print them in sorted order.

Examples:

Input: arr[] = [2, 3, 1, 2, 3]
Output: [2, 3] 
Explanation: 2 and 3 occur more than once in the given array.
Input: arr[] = [3, 1, 2] 
Output: []
Explanation: There is no repeating element in the array, so the output is empty.
Constraints:
1 ≤ n ≤ 106
1 ≤ arr[i] ≤ n



    
</pre>

---
```

class Solution:
    def findDuplicates(self, arr):
        # code here
        hashmap = {}
    
        for i in arr:
            if i in hashmap:
                hashmap[i] += 1
            else:
                hashmap[i] = 1
                
        
        ans = []
        
        for key, value in hashmap.items():
            if value == 2:
                ans.append(key)
                
        return ans
        
```
---
