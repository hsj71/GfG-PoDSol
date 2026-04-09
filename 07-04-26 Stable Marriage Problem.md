```
Stable Marriage Problem
Difficulty: MediumAccuracy: 68.46%Submissions: 11K+Points: 4
You are given two arrays men[] and women[], each of length n, where:

men[i] represents the preference list of the i-th man, ranking all women in order of preference.
women[i] represents the preference list of the i-th woman, ranking all men in order of preference.
The task is to form n pairs (marriages) such that:

Each man is matched with exactly one woman, and each woman is matched with exactly one man.
The matching is stable, meaning there is no pair (man, woman) who both prefer each other over their current partners.
It is guaranteed that a stable matching always exists. Return the stable matching from the men’s perspective, i.e., the one where men are considered for the final output.
Return an array result[] of size n, where result[i] denotes the index (0-based) of the woman matched with the i-th man.

Examples: 

Input: n = 2, men[] = [[0, 1], [0, 1], women[] = [[0, 1], [0, 1]]
Output: [0, 1]
Explanation:
Man 0 is married to Woman 0 (his first choice and her first choice).
Man 1 is married to Woman 1 (his second choice and her second choice).
Input: n = 3, men[] = [[0, 1, 2], [0, 1, 2], [0, 1, 2]], women[] = [[2, 1, 0], [2, 1, 0], [2, 1, 0]]
Output: [2, 1, 0]
Explanation:
Man 0 is married to Woman 2 (his third choice and her third choice).
Man 1 is married to Woman 1 (his second choice and her second choice).
Man 2 is married to Woman 0 (his first choice and her first choice).
Constraints: 
2 ≤ n ≤ 103
0 ≤ men[i] ≤ n - 1
0 ≤ women[i] ≤ n - 1
```
```
class Solution:
     def stableMarriage(self, men, women):
          # code here
          n = len(men)
          rank = [[-1]*n for _ in range(n)]
          for w in range(n):
               for choice in range(n):
                    m = women[w][choice]
                    rank[w][m] = choice
          
          free_men = [-1] * n
          free_women = [-1] * n
          next_proposal = [0] * n

          while True:
               man = -1
               for i in range(n):
                    if free_men[i] == -1:
                         man = i
                         break
               if man == -1:
                    break
               
               woman = men[man][next_proposal[man]]
               next_proposal[man] += 1

               if free_women[woman] == -1:
                    free_women[woman] = man
                    free_men[man] = woman
               
               else:
                    rank_current = rank[woman][free_women[woman]]
                    rank_new = rank[woman][man]

                    if rank_new < rank_current:
                         free_men[free_women[woman]] = -1
                         free_women[woman] = man
                         free_men[man] = woman

          return free_men
```
