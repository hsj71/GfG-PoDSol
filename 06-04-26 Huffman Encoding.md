```
Huffman Encoding
Difficulty: HardAccuracy: 32.4%Submissions: 82K+Points: 8Average Time: 30m
Given a string s of distinct characters and their corresponding frequency f[ ] i.e. character s[i] has f[i] frequency. You need to build the Huffman tree and return all the huffman codes in preorder traversal of the tree.
Note: While merging, if two nodes have the same value (frequency), then the node whose subtree contains the character that appears earlier in the string s will be taken on the left of the Binary Tree and the other one to the right. Otherwise, the node with smaller value will be taken on the left of the subtree and the other one to the right.

Examples:

Input: s = "abcdef", f[] = {5, 9, 12, 13, 16, 45}
Output: [0, 100, 101, 1100, 1101, 111]
Explanation:

HuffmanCodes will be:
f : 0
c : 100
d : 101
a : 1100
b : 1101
e : 111
Constraints:
1 ≤ s.size() = f.size() ≤ 26
```
```
import heapq

class Node:
    def __init__(self, d, i, left=None, right=None):
        self.data = d  
        self.index = i  
        self.left = left
        self.right = right

class Solution:
    
    def preOrder(self, root, ans, curr):
        if root is None:
            return

        if root.left is None and root.right is None:
            if curr == "":
                curr = "0"
            ans.append(curr)
            return

        self.preOrder(root.left, ans, curr + '0')
        self.preOrder(root.right, ans, curr + '1')

    def huffmanCodes(self, s, freq):
        n = len(s)
        pq = []

        for i in range(n):
            tmp = Node(freq[i], i)
            heapq.heappush(pq, (tmp.data, tmp.index, tmp))

        if n == 1:
            return ["0"]

        while len(pq) >= 2:
            f1, i1, l = heapq.heappop(pq)
            f2, i2, r = heapq.heappop(pq)

            newNode = Node(l.data + r.data, min(l.index, r.index), l, r)
            heapq.heappush(pq, (newNode.data, newNode.index, newNode))

        root = pq[0][2]
        ans = []
        self.preOrder(root, ans, "")
        return ans
```
