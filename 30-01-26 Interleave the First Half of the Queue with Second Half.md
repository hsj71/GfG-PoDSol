# 30-01-26
```
Interleave the First Half of the Queue with Second Half
Difficulty: MediumAccuracy: 62.41%Submissions: 27K+Points: 4Average Time: 20m
Given a queue q[] of even size. Your task is to rearrange the queue by interleaving its first half with the second half.

Interleaving is the process of mixing two sequences by alternating their elements while preserving their relative order.
In other words, Interleaving means place the first element from the first half and then first element from the 2nd half and again second element from the first half and then second element from the 2nd half and so on....

Examples:

Input: q[] = [2, 4, 3, 1]
Output: [2, 3, 4, 1]
Explanation: We place the first element of the first half 2 and after that 
place the first element of second half 3 and after that repeat
the same process one more time so the resulting queue will be [2, 3, 4, 1]
Input: q[] = [3, 5]
Output: [3, 5]
Explanation: We place the first element of the first half 3 and first element
of the second half 5 so the resulting queue is [3, 5]
Constraints:
1 ≤ queue.size() ≤ 103
1 ≤ queue[i] ≤ 105
```
---
```
from collections import deque

class Solution:
    def rearrangeQueue(self, q):
        l = len(q)
        half = l // 2
        
        q1, q2 = deque(), deque()
        
        # Split queue
        for _ in range(half):
            q1.append(q.popleft())
        for _ in range(half):
            q2.append(q.popleft())
            
        # Interleave
        while q1 and q2:
            q.append(q1.popleft())
            q.append(q2.popleft())
        
        return q
```
---
