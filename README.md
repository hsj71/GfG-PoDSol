# 14-08-2025
---
## Count Reverse Pairs

You are given an array arr[] of positive integers, find the count of reverse pairs. A pair of indices (i, j) is said to be a reverse pair if both the following conditions are met:

0 ≤ i < j < arr.size()
arr[i] > 2 * arr[j]
Examples:
Input: arr[] = [3, 2, 4, 5, 1, 20]
Output: 3
Explanation:
The Reverse pairs are 
(0, 4), arr[0] = 3, arr[4] = 1, 3 > 2*1 
(2, 4), arr[2] = 4, arr[4] = 1, 4 > 2*1 
(3, 4), arr[3] = 5, arr[4] = 1, 5 > 2*1 
Input: arr[] = [5, 4, 3, 2, 2]
Output: 2
Explanation:
The Reverse pairs are
(0, 3), arr[0] = 5, arr[3] = 2, 5 > 2*2
(0, 4), arr[0] = 5, arr[4] = 2, 5 > 2*2
Constraints:
1 ≤ arr.size() ≤ 5*104
1 ≤ arr[i] ≤ 109


---
```
class Solution:
    def countRevPairs(self, arr):
        # Code here
        def merge_sort(nums, l, r):
            if l >= r:
                return 0
            mid = (l + r) // 2
            count = merge_sort(nums, l, mid) + merge_sort(nums, mid + 1, r)

            # Count reverse pairs across halves
            j = mid + 1
            for i in range(l, mid + 1):
                while j <= r and nums[i] > 2 * nums[j]:
                    j += 1
                count += j - (mid + 1)

            # Merge step
            temp = []
            p1, p2 = l, mid + 1
            while p1 <= mid and p2 <= r:
                if nums[p1] <= nums[p2]:
                    temp.append(nums[p1])
                    p1 += 1
                else:
                    temp.append(nums[p2])
                    p2 += 1
            temp.extend(nums[p1:mid + 1])
            temp.extend(nums[p2:r + 1])
            nums[l:r + 1] = temp

            return count

        return merge_sort(arr, 0, len(arr) - 1)

        return merge_sort(arr, 0, len(arr) - 1)
        
            
```
