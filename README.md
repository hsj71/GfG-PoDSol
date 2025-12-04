# 4-12-25
---
## Optimal binary search tree
Difficulty: HardAccuracy: 50.02%Submissions: 17K+Points: 8
<pre>

You are given a set of distinct keys in sorted order, which is represent by keys[]. Each key ki represents a data record that is accessed during a seach operation. For all the keys, you are also given a frequency array freq[], which denotes how many times key ki is searched for.
The cost of accessing a key in a binary search tree is calculated by multiplying its access frequency by the level at which it appears in the tree. Therefore different arrangements of keys in the BST gives different total search costs.

Your task is to calculate the minimum total search cost required to construct a binary search tree containing all the keys.

Note: Consider the root of the BST is at level 1.

Examples:

Input: keys[] = [10, 12], freq[] = [34, 50]
Output: 118
Explaination: There can be following two possible BSTs
                                
The cost of tree I is 34*1 + 50*2 = 134
The cost of tree II is 50*1 + 34*2 = 118
Input: keys[] = [10, 12, 20], freq[] = [34, 8, 50]
Output: 142
Explaination: There can be many possible BSTs
 
Among all possible BSTs, 
cost of the 5th BST is minimum.  
Cost of this BST is 1*50 + 2*34 + 3*8 = 142
Constraints:
1 ≤ keys.size() = freq.size() ≤ 100
1 ≤ keys[i], freq[i] ≤ 104


    
</pre>

---
```
class Solution:
    def minCost(self, keys, freq):
        n = len(keys)
        dp = [[0]*n for _ in range(n)]
        opt = [[0]*n for _ in range(n)]
        pre = [0]*(n+1)

        for i in range(n):
            pre[i+1] = pre[i] + freq[i]
            dp[i][i] = freq[i]
            opt[i][i] = i

        for length in range(2, n+1):
            for i in range(n - length + 1):
                j = i + length - 1
                dp[i][j] = 10**18
                L, R = opt[i][j-1], opt[i+1][j]
                for k in range(L, R+1):
                    left = dp[i][k-1] if k > i else 0
                    right = dp[k+1][j] if k < j else 0
                    cost = left + right + (pre[j+1] - pre[i])
                    if cost < dp[i][j]:
                        dp[i][j] = cost
                        opt[i][j] = k

        return dp[0][n-1]
        
```
---
