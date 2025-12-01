# 1-12-25
---
## XOR Pairs less than K
Difficulty: MediumAccuracy: 68.92%Submissions: 6K+Points: 4
<pre>


Given an array arr[] and an integer k, we need to count the number of pairs from the given array such that the Bitwise XOR of each pair is less than k.

Examples:

Input: arr = [1, 2, 3, 5], k = 5 
Output: 4
Explanation: Bitwise XOR of all possible pairs that satisfy the given conditions are:
arr[0] ^ arr[1] = 1 ^ 2 = 3 
arr[0] ^ arr[2] = 1 ^ 3 = 2 
arr[0] ^ arr[3] = 1 ^ 5 = 4 
arr[1] ^ arr[2] = 2 ^ 3 = 1 
Therefore, the required output is 4.
Input: arr[] = [3, 5, 6, 8], k = 7 
Output: 3
Explnation: Bitwise XOR of all possible pairs that satisfy the given conditions are:
arr[0] ^ arr[1] = 6
arr[0] ^ arr[2] = 5
arr[1] ^ arr[2] = 3
Therefore, the required output is 3. 
Constraints:
1 ≤ arr.size(), k ≤ 5*104
1 ≤ arr[i] ≤ 5*104
    
</pre>

---
```
class TrieNode:
    def __init__(self):
        self.child = [None, None]
        self.count = 0

class Solution:
    def cntPairs(self, arr, k):
        root = TrieNode()

        def insert(num):
            node = root
            for i in range(15, -1, -1):
                bit = (num >> i) & 1
                if not node.child[bit]:
                    node.child[bit] = TrieNode()
                node = node.child[bit]
                node.count += 1

        def query(num, k):
            node = root
            total = 0
            for i in range(15, -1, -1):
                if not node:
                    break

                bit = (num >> i) & 1
                kbit = (k >> i) & 1

                if kbit == 1:
                    # If kbit = 1, add matches for XOR < k at this bit
                    if node.child[bit]:
                        total += node.child[bit].count
                    node = node.child[1 - bit]
                else:
                    node = node.child[bit]
            return total

        ans = 0
        for x in arr:
            ans += query(x, k)
            insert(x)

        return ans
        
        
```
---
