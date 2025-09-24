# 24-09-2025
---
## Design MinMax Queue
Difficulty: MediumAccuracy: 72.97%Submissions: 8K+Points: 4

<pre>
Design a SpecialQueue data structure that functions like a normal queue but with additional support for retrieving the minimum and maximum element efficiently.
The SpecialQueue must support the following operations:

enqueue(x): Insert an element x at the rear of the queue.
dequeue(): Remove the element from the front of the queue.
getFront(): Return the front element without removing.
getMin(): Return the minimum element in the queue in O(1) time.
getMax(): Return the maximum element in the queue in O(1) time.
There will be a sequence of queries queries[][]. The queries are represented in numeric form:

1 x : Call enqueue(x)
2:  Call dequeue()
3: Call getFront()
4: Call getMin()
5: Call getMax()
The driver code will process the queries, call the corresponding functions, and print the outputs of getFront(), getMin(), getMax() operations.
You only need to implement the above five functions.

Note: It is guaranteed that all the queries are valid.

Examples:

Input: q = 6, queries[][] = [[1, 4], [1, 2], [3], [4], [2], [5]]
Output: [4, 2, 2]
Explanation: Queries on queue are as follows:
enqueue(4): Insert 4 at the rear of the queue.
enqueue(2): Insert 2 at the rear of the queue.
return the front element i.e 4
return minimum element from the queue i.e 2
dequeue(): Remove the front element 4 from the queue
return maximum element from the queue i.e 2
Input: q = 4, queries[][] = [[1, 3], [4], [1, 5], [5]]
Output: [3, 5]
Explanation: Queries on queue are as follows:
enqueue(3): Insert 3 at the rear of the queue.
return minimum element from the queue i.e 3
enqueue(5): Insert 5 at the rear of the queue.
return maximum element from the queue i.e 5
Constraints:
1 ≤ queries.size() ≤ 105
0 ≤ values in the queue ≤ 109

	
</pre>

---
```
from collections import deque
class SpecialQueue:
    def __init__(self):
        self.queue=deque()
        self.minDeque=deque()
        self.maxDeque=deque()

    def enqueue(self, x):
        self.queue.append(x)
        while self.minDeque and self.minDeque[-1]>x:
            self.minDeque.pop()
        self.minDeque.append(x)
        while self.maxDeque and self.maxDeque[-1]<x:
            self.maxDeque.pop()
        self.maxDeque.append(x)

    def dequeue(self):
        if not self.queue:
            return -1
        val=self.queue.popleft()
        if val==self.minDeque[0]:
            self.minDeque.popleft()
        if val==self.maxDeque[0]:
            self.maxDeque.popleft()
    
    def getFront(self):
        if self.queue:
            return self.queue[0]
        return -1
    
    def getMin(self):
        if self.minDeque:
            return self.minDeque[0]
        return -1

    def getMax(self):
        if self.maxDeque:
            return self.maxDeque[0]
        return -1
        
        
```
---
