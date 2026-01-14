# 14-01-26
---
## Police and Thieves
Difficulty: MediumAccuracy: 34.03%Submissions: 54K+Points: 4
<pre>

Given an array arr[], where each element contains either a 'P' for policeman or a 'T' for thief. Find the maximum number of thieves that can be caught by the police. 
Keep in mind the following conditions :

Each policeman can catch only one thief.
A policeman cannot catch a thief who is more than k units away from him.
Examples:

Input: arr[] = ['P', 'T', 'T', 'P', 'T'], k = 1
Output: 2
Explanation: Maximum 2 thieves can be caught. First policeman catches first thief and second police man can catch either second or third thief.
Input: arr[] = ['T', 'T', 'P', 'P', 'T', 'P'], k = 2
Output: 3
Explanation: Maximum 3 thieves can be caught.
Constraints:
1 ≤ arr.size() ≤ 105
1 ≤ k ≤ 1000
arr[i] = 'P' or 'T'
</pre>

---
```
class Solution:
    def catchThieves(self, arr, k):
        #code here
        if arr.count("P") == 0 or arr.count("T")== 0:
            return 0
        police = []
        thief = []
    
        for i in range(len(arr)):
            if arr[i] == 'P':
                police.append(i)
            else:
                thief.append(i)
        
        i = j = 0
        caught = 0
        
        while i < len(police) and j < len(thief):
            if abs(police[i] - thief[j]) <= k:
                caught += 1
                i += 1
                j += 1
            elif police[i] < thief[j]:
                i += 1
            else:
                j += 1
        
        return caught
        
```
---
