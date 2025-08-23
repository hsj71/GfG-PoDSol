# 23-08-2025
---
## Allocate Minimum Pages
Difficulty: MediumAccuracy: 35.51%Submissions: 322K+Points: 4Average Time: 35m
<pre>

Given an array arr[] of integers, where each element arr[i] represents the number of pages in the i-th book. You also have an integer k representing the number of students. The task is to allocate books to each student such that:

Each student receives atleast one book.
Each student is assigned a contiguous sequence of books.
No book is assigned to more than one student.
The objective is to minimize the maximum number of pages assigned to any student. In other words, out of all possible allocations, find the arrangement where the student who receives the most pages still has the smallest possible maximum.

Note: If it is not possible to allocate books to all students, return -1.

Examples:

Input: arr[] = [12, 34, 67, 90], k = 2
Output: 113
Explanation: Allocation can be done in following ways:
=> [12] and [34, 67, 90] Maximum Pages = 191
=> [12, 34] and [67, 90] Maximum Pages = 157
=> [12, 34, 67] and [90] Maximum Pages = 113.
The third combination has the minimum pages assigned to a student which is 113.
Input: arr[] = [15, 17, 20], k = 5
Output: -1
Explanation: Since there are more students than total books, it's impossible to allocate a book to each student.
Constraints:
1 ≤ arr.size() ≤ 106
1 ≤ arr[i], k ≤ 103
</pre>

---
```
class Solution:
    def isPossible(self,arr,val,k):
        count,curr=1,0
        for pages in arr:
            curr+=pages
            if curr>val:
                curr=pages
                count+=1
            if count>k or pages>val:
                return False
        return True
    
    def findPages(self, arr, k):
        if len(arr)<k:
            return -1
        l,h,ans=0,sum(arr),-1
        while l<=h:
            mid=(l+h)//2
            if self.isPossible(arr,mid,k):
                ans=mid
                h=mid-1
            else:
                l=mid+1
        return ans

```
---
