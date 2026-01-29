# 29-01-26
```
Stream First Non-repeating
Difficulty: MediumAccuracy: 31.65%Submissions: 235K+Points: 4Average Time: 15m
Given a string s consisting of only lowercase alphabets, for each index i in the string (0 ≤ i < n), find the first non-repeating character in the prefix s[0..i]. If no such character exists, use '#'.

Examples:

Input: s = "aabc"
Output: a#bb
Explanation: 
At i=0 ("a"): First non-repeating character is 'a'.
At i=1 ("aa"): No non-repeating character, so '#'.
At i=2 ("aab"): First non-repeating character is 'b'.
At i=3 ("aabc"): Non-repeating characters are 'b' and 'c'; 'b' appeared first, so 'b'. 
Input: s = "bb" 
Output: "b#" 
Explanation: 
At i=0 ("b"): First non-repeating character is 'b'.
At i=1 ("bb"): No non-repeating character, so '#'.
Constraints:
1 ≤ s.size() ≤ 105
```
---
```
class Solution:
	def firstNonRepeating(self, s):
		# code here
		char=[0]*26
        res=''
        fn=''
        for i in s:
            c=ord(i)-ord('a')
            if char[c]==0:
                a= i if not fn else fn[0]
                fn+=i
            else:
                fn= fn.replace(i, '')
                a=fn[0] if fn else '#'
            res+=a
            char[c]+=1
        return res
```
