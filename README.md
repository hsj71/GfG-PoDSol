# 23-09-2025
---
## Queue Reversal
Difficulty: EasyAccuracy: 77.98%Submissions: 152K+Points: 2

<pre>
Given a queue q containing integer elements, your task is to reverse the queue.

Examples:

Input: q[] = [5, 10, 15, 20, 25]
Output: [25, 20, 15, 10, 5]
Explanation: After reversing the given elements of the queue, the resultant queue will be 25 20 15 10 5.
Input: q[] = [1, 2, 3, 4, 5]
Output: [5, 4, 3, 2, 1]
Explanation: After reversing the given elements of the queue, the resultant queue will be 5 4 3 2 1.
Constraints:
1 ≤ q.size() ≤ 103
0 ≤ q[i] ≤ 105



	
</pre>

---
```
class Solution:
    def reverseQueue(self, q):
        # code here
        return q.reverse()
        
        
```
---
