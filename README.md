# 31-12-25
---
## Palindrome Linked List
Difficulty: MediumAccuracy: 41.48%Submissions: 382K+Points: 4Average Time: 20m
<pre>


You are given the head of a singly linked list of positive integers. You have to check if the given linked list is palindrome or not.

Examples:

Input:
   
Output: true
Explanation: The given linked list is 1 -> 2 -> 1 -> 1 -> 2 -> 1, which is a palindrome.
Input:
   
Output: false
Explanation: The given linked list is 10 -> 20 -> 30 -> 40 -> 50, which is not a palindrome.
Constraints:
1 ≤ number of nodes ≤ 105
0 ≤ node->data ≤ 103
	
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
    def isPalindrome(self, head):
        # code here
        s=[]
        while head:
            s.append(str(head.data))
            head = head.next
        return all(s[i] == s[len(s) - i - 1] for i in range(len(s) // 2))
        
        
        
        

        
```
---
