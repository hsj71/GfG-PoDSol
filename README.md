# 15-12-25
---
## Count Indices to Balance Even and Odd Sums
Difficulty: MediumAccuracy: 75.22%Submissions: 6K+Points: 4
<pre>

Given an array arr[], count the number of indices such that deleting the element at that index and shifting all elements after it one position left results in an array where the sum of elements at even indices equals the sum at odd indices.

Examples:

Input: arr[] = [2, 1, 6, 4]
Output: 1
Explaination: After removing arr[1], the resulting array will be [2, 6, 4] the sums of elements at odd index is arr[1] = 6 and the sum of elements at even index is arr[0] + arr[2] = 6.
Input: arr[] = [1, 1, 1]
Output: 3
Explaination: Removing any element makes the sum of odd and even indexed elements equal.
Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ arr[i] ≤ 104

    
</pre>

---
```

class Solution:
    def cntWays(self, arr):
        # code here
        arr = [arr[i] if i%2 == 0 else -arr[i] for i in range(len(arr))]
        
        sols = []
        ls = 0
        s = sum(arr)
        for i in range(len(arr)):
            s = s - arr[i]
        
            if  ls - s == 0:
                sols.append(i)
        
            ls = ls + arr[i]
            
        return len(sols)

        
```
---
