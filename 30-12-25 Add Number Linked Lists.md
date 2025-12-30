# 30-12-25
---
## Add Number Linked Lists
Difficulty: MediumAccuracy: 34.52%Submissions: 371K+Points: 4Average Time: 30m

<pre>


You are given the head of two singly linked lists head1 and head2 representing two non-negative integers. You have to return the head of the linked list representing the sum of these two numbers.

Note: There can be leading zeros in the input lists, but there should not be any leading zeros in the output list.

Examples:

Input: 
    
Output:  1 -> 1 -> 2 -> 2
Explanation: Given numbers are 123 and 999. There sum is 1122.
    
Input: 
    
Output: 7 -> 0 
Explanation: Given numbers are 63 and 7. There sum is 70.
    
Constraints:
1 ≤ Number of nodes in head1, head2 ≤ 105
0 ≤ node->data ≤ 9
	
</pre>

---
```

'''
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
'''

class Solution:
    def find(self, head):
        if head.next == None:
            return 1
        return 1 + self.find(head.next)
    
    def generate(self, head1, head2, skip):
        if head1 == None and head2 == None:
            return None, 0
        val = head1.data
        if skip <= 0:
            val += head2.data
        node_next, rem = self.generate(
            head1.next,
            head2 if skip > 0 else head2.next,
            skip - 1
        )
        val += rem
        node = Node(val%10)
        node.next = node_next
        return node, val//10
        
    def addTwoLists(self, head1, head2):
        # code here
        len_1 = self.find(head1)
        len_2 = self.find(head2)
        out = []
        if len_1 > len_2:
            out, car = self.generate(head1, head2, len_1 - len_2)
        else:
            out, car = self.generate(head2, head1, len_2 - len_1)
        if car:
            node = Node(car)
            node.next = out
            return node
        while out.data == 0:
            out = out.next
        return out
        
        
        

        
```
---
