# 27-12-25
---
## Kth smallest element in a Matrix
Difficulty: MediumAccuracy: 61.42%Submissions: 82K+Points: 4Average Time: 35m

<pre>


Given a matrix mat[][] of size n*n, where each row and column is sorted in non-decreasing order. Find the kth smallest element in the matrix.

Examples:
Input: mat[][] = [[16, 28, 60, 64], k = 3
                [22, 41, 63, 91],
                [27, 50, 87, 93],
                [36, 78, 87, 94]]
Output: 27
Explanation: 27 is the 3rd smallest element.
Input: mat[][] = [[10, 20, 30, 40], k = 7
                [15, 25, 35, 45],
                [24, 29, 37, 48],
                [32, 33, 39, 50]] 
Output: 30
Explanation: 30 is the 7th smallest element.
Constraints:
1 ≤ n ≤ 500
1 ≤ mat[i][j] ≤ 104
1 ≤ k ≤ n*n
	
</pre>

---
```

class Solution:
    def kthSmallest(self, mat, k):
        # code here
        def help(mat,x):
            n=len(mat)
            i,j=0,n-1
            ans=0
            while j>=0 and i<=n-1:
                if mat[i][j]>x:
                    j-=1
                else:
                    i+=1
                    ans+=(j+1)
            return ans
            
        n=len(mat)
        l,h=mat[0][0],mat[n-1][n-1]
        while l<=h:
            mid=(l+h)//2
            if help(mat,mid)>=k:
                h=mid-1
            else:
                l=mid+1
        return h+1


        
```
---
