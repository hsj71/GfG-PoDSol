# 27-01-26
---
## Word Search
Difficulty: MediumAccuracy: 32.69%Submissions: 90K+Points: 4Average Time: 20m
<pre>


You are given a matrix mat[][] of size n*m containing english alphabets and a string word. Check if the word exists on the mat[][] or not. The word can be constructed by using letters from adjacent cells, either horizontally or vertically. The same cell cannot be used more than once.

Examples :

Input: mat[][] = [['T', 'E', 'E'], ['S', 'G', 'K'], ['T', 'E', 'L']], word = "GEEK"
Output: true
Explanation: Word "GEEK" can be found in the given grid as follows.

Input: mat[][] = [['T', 'E', 'U'], ['S', 'G', 'K'], ['T', 'E', 'L']], word = "GEEK"
Output: false
Explanation: Word "GEEK" cannot be found in the given grid.

Input: mat[][] = [['A', 'B', 'A'], ['B', 'A', 'B']], word = "AB"
Output: true
Explanation: There are multiple ways to construct the word "AB".

Constraints:
1 ≤ n, m ≤ 6
1 ≤ word.size() ≤ 15
mat and word consists of only lowercase and uppercase English letters.
    
</pre>

---
```
class Solution:
    def isWordExist(self, mat, word):
        n, m = len(mat), len(mat[0])

        # Early prune: if word contains more occurrences of a letter
        # than the board, no need to search.
        from collections import Counter
        board_count = Counter(sum(mat, []))
        word_count = Counter(word)
        for ch in word_count:
            if word_count[ch] > board_count.get(ch, 0):
                return False

        def dfs(i, j, idx):
            if idx == len(word):
                return True

            # boundary conditions or mismatch
            if i < 0 or j < 0 or i >= n or j >= m or mat[i][j] != word[idx]:
                return False

            temp = mat[i][j]
            mat[i][j] = "#"     # mark visited

            # explore 4 directions
            found = (
                dfs(i+1, j, idx+1) or
                dfs(i-1, j, idx+1) or
                dfs(i, j+1, idx+1) or
                dfs(i, j-1, idx+1)
            )

            mat[i][j] = temp    # restore
            return found

        # Try starting from each position
        for i in range(n):
            for j in range(m):
                if mat[i][j] == word[0]:
                    if dfs(i, j, 0):
                        return True

        return False
        
```
---
