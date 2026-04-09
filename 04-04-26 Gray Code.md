```
Gray Code
Difficulty: MediumAccuracy: 60.49%Submissions: 20K+Points: 4
Given a number n, generate bit patterns from 0 to 2n-1 such that successive patterns differ by one bit. 
A Gray code sequence must begin with 0.
 
Examples:
Input: n = 2
Output: ["00", "01", "11", "10"]
Explanation: 
00 and 01 differ by one bit.
01 and 11 differ by one bit.
11 and 10 also differ by one bit.
Input: n = 3
Output: ["000", "001", "011", "010", "110", "111", "101", "100"]
Explanation:
000 and 001 differ by one bit.
001 and 011 differ by one bit.
011 and 010 differ by one bit.
Similarly, every successive pattern 
differs by one bit.
Constraints :
1 ≤ n ≤ 16
```
```
class Solution:
    def graycode(self,n):
        #code here
        result = []
        
        for i in range(1 << n):  # 0 to 2^n - 1
            gray = i ^ (i >> 1)
            result.append(format(gray, '0{}b'.format(n)))
        
        return result
```
