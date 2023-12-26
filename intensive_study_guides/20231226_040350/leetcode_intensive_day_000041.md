
# Leetcode Intensive Tutorial Day 41 
> [Difficulty Score: 22]

> [Version: 20231226_040350]

> [Including this day, you had studied : 336 leetcode problems]


## Courses overview of the day

- 93 Restore IP Addresses [Medium]
  - 131 Palindrome Partitioning [Medium]
    - 132 Palindrome Partitioning II [Hard]
    - 291 Word Pattern II [Hard]
      - 52 N-Queens II [Hard]
        - 51 N-Queens [Hard]
          - 351 Android Unlock Patterns [Medium]

#### Step by step

 - [1. From 93 Restore IP Addresses [Medium] to 131 Palindrome Partitioning [Medium]](#1-from-93-restore-ip-addresses-medium-to-131-palindrome-partitioning-medium))

 - [2. From 131 Palindrome Partitioning [Medium] to 132 Palindrome Partitioning II [Hard]](#2-from-131-palindrome-partitioning-medium-to-132-palindrome-partitioning-ii-hard))

 - [3. From 131 Palindrome Partitioning [Medium] to 291 Word Pattern II [Hard]](#3-from-131-palindrome-partitioning-medium-to-291-word-pattern-ii-hard))

 - [4. From 291 Word Pattern II [Hard] to 52 N-Queens II [Hard]](#4-from-291-word-pattern-ii-hard-to-52-n-queens-ii-hard))

 - [5. From 52 N-Queens II [Hard] to 51 N-Queens [Hard]](#5-from-52-n-queens-ii-hard-to-51-n-queens-hard))

 - [6. From 51 N-Queens [Hard] to 351 Android Unlock Patterns [Medium]](#6-from-51-n-queens-hard-to-351-android-unlock-patterns-medium))

    

#### Summary


- 93 Restore IP Addresses : The essence of the problem is to generate all possible valid IP addresses that can be obtained from the input string.
- 291 Word Pattern II : The essence of this problem is to find a bijection between a pattern and a string by trying different substrings for each character in the pattern.
- 131 Palindrome Partitioning : The essence of the problem is to generate all possible palindrome partitions of a given string.
- 132 Palindrome Partitioning II : The essence of the problem is to find the minimum cuts needed for a palindrome partitioning of a given string.
- 351 Android Unlock Patterns : The essence of this problem is to generate all possible patterns and count the number of valid patterns within a given range.
- 51 N-Queens : The essence of this problem is to find all distinct solutions to the N-Queens puzzle using backtracking.
- 52 N-Queens II : The essence of this problem is to find the number of distinct solutions to the N-Queens puzzle using backtracking.
> Similarity Diameter of these problems: 0.6516


---
# 1. From 93 Restore IP Addresses [Medium] to 131 Palindrome Partitioning [Medium]
> Similarity Distance: 0.4790

### >> 93 Restore IP Addresses [Medium]
Given a string s containing only digits, return all possible valid IP addresses that can be obtained from s. You can return them in any order.
##### Sample input:
"25525511135"
##### Sample output:
["255.255.11.135","255.255.111.35"]

##### Questions to ask to clarify requirements:
What is the maximum length of the input string? Can the input string contain leading zeros?

##### Optimal Python solution:
```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        def backtrack(s, path, res):
            if len(s) > (4 - len(path)) * 3:
                return
            if not s and len(path) == 4:
                res.append('.'.join(path))
                return
            for i in range(min(3, len(s))):
                curr = s[:i+1]
                if (curr[0] == '0' and len(curr) >= 2) or int(curr) > 255:
                    continue
                backtrack(s[i+1:], path + [curr], res)
        res = []
        backtrack(s, [], res)
        return res
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. Use backtracking to generate all possible IP addresses.
2. Use a helper function to recursively generate the IP addresses.
3. Use a list to keep track of the current IP address.
4. Use a list to store the valid IP addresses.
5. Use a loop to iterate through the string and generate the IP addresses.
6. Use a condition to check if the current IP address is valid.
7. Use a condition to check if the current IP address is complete.
8. Use a condition to check if the remaining string is too long.
9. Use a condition to check if the current segment is valid.
10. Use a condition to check if the current segment is too long.
11. Use a condition to check if the current segment is too short.
12. Use a condition to check if the current segment is zero.
13. Use a condition to check if the current segment is greater than 255.
14. Use a condition to check if the current segment has leading zeros.
15. Use a condition to check if the current segment is the last segment.
1. Use a helper function to recursively generate the IP addresses.
2. Use a list to keep track of the current IP address.
3. Use a list to store the valid IP addresses.
4. Use a loop to iterate through the string and generate the IP addresses.
5. Use conditions to check if the current IP address is valid, complete, and if the remaining string is too long.
6. Use conditions to check if the current segment is valid, too long, too short, zero, greater than 255, has leading zeros, and if it is the last segment.
1. Handling leading zeros in the IP address.
2. Handling segments greater than 255.
3. Handling segments with leading zeros.
4. Handling the last segment of the IP address.
1. Avoid using a brute force approach to generate all possible IP addresses.
2. Avoid using a nested loop to iterate through the string.
3. Avoid using a separate function to check if a segment is valid.
4. Avoid using a separate function to check if a segment is complete.
5. Avoid using a separate function to check if the remaining string is too long.
6. Avoid using a separate function to check if the current segment is valid.
7. Avoid using a separate function to check if the current segment is too long.
8. Avoid using a separate function to check if the current segment is too short.
9. Avoid using a separate function to check if the current segment is zero.
10. Avoid using a separate function to check if the current segment is greater than 255.
11. Avoid using a separate function to check if the current segment has leading zeros.
12. Avoid using a separate function to check if the current segment is the last segment.
    
### >> 131 Palindrome Partitioning [Medium]
Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.
##### Sample input:
"aab"
##### Sample output:
[["a","a","b"],["aa","b"]]

##### Questions to ask to clarify requirements:
What is the maximum length of the input string? Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def backtrack(start, path):
            if start == len(s):
                res.append(path[:])
                return
            for i in range(start, len(s)):
                if s[start:i+1] == s[start:i+1][::-1]:
                    path.append(s[start:i+1])
                    backtrack(i+1, path)
                    path.pop()
        res = []
        backtrack(0, [])
        return res
```
##### Time complexity:
O(n * 2^n)
##### Space complexity:
O(n)
##### Notes:
1. Use backtracking to generate all possible partitions.
2. Check if each substring is a palindrome.
3. Keep track of the current partition using a path list.
4. Append the path to the result list when reaching the end of the string.
1. Use recursion and backtracking to generate all possible partitions.
2. Check if each substring is a palindrome using string slicing.
3. Keep track of the current partition using a path list.
4. Append the path to the result list when reaching the end of the string.
1. Use backtracking to generate all possible partitions.
2. Check if each substring is a palindrome.
3. Keep track of the current partition using a path list.
4. Append the path to the result list when reaching the end of the string.
1. Avoid using a nested loop to generate all possible partitions.
2. Avoid checking if each substring is a palindrome using a separate function.
3. Avoid using a global variable to store the result list.
    
### >> Comparison: 93 Restore IP Addresses [Medium] *VS* 131 Palindrome Partitioning [Medium]
> Similarity distance: 0.4790
##### Similarities

- Both questions are categorized as medium difficulty level.
- Both questions involve string manipulation and partitioning.
- Both questions require finding valid combinations or partitions.
- Both questions involve backtracking to explore all possible solutions.
##### Differences

- Question 93 involves restoring IP addresses, while question 131 involves partitioning a string into palindromes.
- Question 93 requires forming valid IP addresses with a given string, while question 131 requires partitioning a string into palindromic substrings.
- Question 93 has a fixed length of 4 for each IP address segment, while question 131 has no fixed length for the palindromic substrings.
- Question 93 has a constraint on the range of each IP address segment, while question 131 does not have any specific constraints.
##### New Insights in 131 Palindrome Partitioning [Medium]

- Both questions require careful consideration of valid combinations or partitions.
- Both questions can be solved using backtracking algorithms.
- Both questions require handling different cases and constraints.
- Both questions provide opportunities to improve string manipulation skills.


---
# 2. From 131 Palindrome Partitioning [Medium] to 132 Palindrome Partitioning II [Hard]
> Similarity Distance: 0.3596

### >> Reminder: 131 Palindrome Partitioning [Medium]
Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.
##### Optimal Python solution:
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def backtrack(start, path):
            if start == len(s):
                res.append(path[:])
                return
            for i in range(start, len(s)):
                if s[start:i+1] == s[start:i+1][::-1]:
                    path.append(s[start:i+1])
                    backtrack(i+1, path)
                    path.pop()
        res = []
        backtrack(0, [])
        return res
```
The essence of the problem is to generate all possible palindrome partitions of a given string.
    
### >> 132 Palindrome Partitioning II [Hard]
Given a string s, partition s such that every substring of the partition is a palindrome. Return the minimum cuts needed for a palindrome partitioning of s.
##### Sample input:
"aab"
##### Sample output:
1

##### Questions to ask to clarify requirements:
What is the maximum length of the input string? Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def minCut(self, s: str) -> int:
        n = len(s)
        dp = [0] * n
        pal = [[False] * n for _ in range(n)]
        for i in range(n):
            min_cut = i
            for j in range(i + 1):
                if s[i] == s[j] and (i - j < 2 or pal[j + 1][i - 1]):
                    pal[j][i] = True
                    min_cut = 0 if j == 0 else min(min_cut, dp[j - 1] + 1)
            dp[i] = min_cut
        return dp[n - 1]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:
1. Use dynamic programming to find the minimum cuts.
2. Create a 2D array to store whether a substring is a palindrome.
3. Initialize the minimum cuts array with the maximum possible value.
4. Iterate through the string and update the minimum cuts based on the palindromic substrings.
1. Use dynamic programming to find the minimum cuts.
2. Create a 2D array to store whether a substring is a palindrome.
3. Initialize the minimum cuts array with the maximum possible value.
4. Iterate through the string and update the minimum cuts based on the palindromic substrings.
1. Use dynamic programming to find the minimum cuts.
2. Create a 2D array to store whether a substring is a palindrome.
3. Initialize the minimum cuts array with the maximum possible value.
4. Iterate through the string and update the minimum cuts based on the palindromic substrings.
1. Avoid using a nested loop to check if each substring is a palindrome.
2. Avoid using a recursive function to find the minimum cuts.
3. Avoid using a global variable to store the minimum cuts array.
    
### >> Comparison: 131 Palindrome Partitioning [Medium] *VS* 132 Palindrome Partitioning II [Hard]
> Similarity distance: 0.3596
##### Similarities

- Both questions involve partitioning a string into palindromic substrings.
##### Differences

- 131 Palindrome Partitioning is a medium-level question, while 132 Palindrome Partitioning II is a hard-level question.
- 131 Palindrome Partitioning asks for the minimum number of partitions needed, while 132 Palindrome Partitioning II asks for the minimum cuts needed.
##### New Insights in 132 Palindrome Partitioning II [Hard]

- Both questions can be solved using dynamic programming.
- 131 Palindrome Partitioning can be solved using backtracking as well.
- 132 Palindrome Partitioning II can be solved using Manacher's algorithm to find the longest palindromic substring.


---
# 3. From 131 Palindrome Partitioning [Medium] to 291 Word Pattern II [Hard]
> Similarity Distance: 0.4704

### >> Reminder: 131 Palindrome Partitioning [Medium]
Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.
##### Optimal Python solution:
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def backtrack(start, path):
            if start == len(s):
                res.append(path[:])
                return
            for i in range(start, len(s)):
                if s[start:i+1] == s[start:i+1][::-1]:
                    path.append(s[start:i+1])
                    backtrack(i+1, path)
                    path.pop()
        res = []
        backtrack(0, [])
        return res
```
The essence of the problem is to generate all possible palindrome partitions of a given string.
    
### >> 291 Word Pattern II [Hard]
Given a pattern and a string s, find if s follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty substring in s.


Example 1:

Input: pattern = "abab", s = "redblueredblue"
Output: true
Explanation: One possible mapping is as follows:
a -> "red"
b -> "blue"

Example 2:

Input: pattern = "aaaa", s = "asdasdasdasd"
Output: true
Explanation: One possible mapping is as follows:
a -> "asd"

Example 3:

Input: pattern = "aabb", s = "xyzabcxzyabc"
Output: false


Constraints:

You may assume both pattern and s consists of only lowercase letters.

##### Sample input:
pattern = "abab"
s = "redblueredblue"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the maximum length of pattern and s?
Can the pattern or s be empty?


##### Optimal Python solution:
```python
class Solution:
    def wordPatternMatch(self, pattern: str, s: str) -> bool:
        return self.backtrack(pattern, s, {}, set())

    def backtrack(self, pattern, s, mapping, used):
        if not pattern:
            return not s
        char = pattern[0]
        if char in mapping:
            word = mapping[char]
            if not s.startswith(word):
                return False
            return self.backtrack(pattern[1:], s[len(word):], mapping, used)
        for i in range(1, len(s) - len(pattern) + 2):
            word = s[:i]
            if word in used:
                continue
            mapping[char] = word
            used.add(word)
            if self.backtrack(pattern[1:], s[i:], mapping, used):
                return True
            del mapping[char]
            used.remove(word)
        return False
```
##### Time complexity:
O(N^M)
##### Space complexity:
O(M)
##### Notes:
1. Use backtracking to find a bijection between pattern and s.
2. Start with the first character of pattern and try to match it with a substring in s.
3. If a match is found, recursively check if the remaining pattern and s can be matched.
4. If a match is not found, try different substrings in s until a match is found or all possibilities are exhausted.
5. Keep track of the mapping between characters in pattern and substrings in s to ensure a bijection.
6. Use a set to keep track of used substrings to avoid duplicate mappings.

1. Use recursion to implement backtracking algorithms.
2. Keep track of the current state and backtrack when necessary.
3. Use data structures like dictionaries and sets to store and retrieve information efficiently.

The main challenge is to find a bijection between pattern and s.

Avoid using a brute force approach to check all possible mappings.

    
### >> Comparison: 131 Palindrome Partitioning [Medium] *VS* 291 Word Pattern II [Hard]
> Similarity distance: 0.4704
##### Similarities

- Both questions involve pattern matching and backtracking.
- Both questions require finding a valid combination of substrings.
##### Differences

- 131 Palindrome Partitioning involves partitioning a string into palindromic substrings.
- 291 Word Pattern II involves finding a pattern in a string and mapping it to a pattern in another string.
##### New Insights in 291 Word Pattern II [Hard]

- 131 Palindrome Partitioning teaches us how to efficiently generate all possible palindromic partitions of a string.
- 291 Word Pattern II teaches us how to efficiently generate all possible mappings between two patterns.


---
# 4. From 291 Word Pattern II [Hard] to 52 N-Queens II [Hard]
> Similarity Distance: 0.5003

### >> Reminder: 291 Word Pattern II [Hard]
Given a pattern and a string s, find if s follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty substring in s.


Example 1:

Input: pattern = "abab", s = "redblueredblue"
Output: true
Explanation: One possible mapping is as follows:
a -> "red"
b -> "blue"

Example 2:

Input: pattern = "aaaa", s = "asdasdasdasd"
Output: true
Explanation: One possible mapping is as follows:
a -> "asd"

Example 3:

Input: pattern = "aabb", s = "xyzabcxzyabc"
Output: false


Constraints:

You may assume both pattern and s consists of only lowercase letters.

##### Optimal Python solution:
```python
class Solution:
    def wordPatternMatch(self, pattern: str, s: str) -> bool:
        return self.backtrack(pattern, s, {}, set())

    def backtrack(self, pattern, s, mapping, used):
        if not pattern:
            return not s
        char = pattern[0]
        if char in mapping:
            word = mapping[char]
            if not s.startswith(word):
                return False
            return self.backtrack(pattern[1:], s[len(word):], mapping, used)
        for i in range(1, len(s) - len(pattern) + 2):
            word = s[:i]
            if word in used:
                continue
            mapping[char] = word
            used.add(word)
            if self.backtrack(pattern[1:], s[i:], mapping, used):
                return True
            del mapping[char]
            used.remove(word)
        return False
```
The essence of this problem is to find a bijection between a pattern and a string by trying different substrings for each character in the pattern.
    
### >> 52 N-Queens II [Hard]
The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other. Given an integer n, return the number of distinct solutions to the n-queens puzzle.
##### Sample input:
4
##### Sample output:
2

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def totalNQueens(self, n: int) -> int:
        def backtrack(row, diagonals, anti_diagonals, cols):
            nonlocal count
            if row == n:
                count += 1
                return
            for col in range(n):
                diagonal = row - col
                anti_diagonal = row + col
                if col in cols or diagonal in diagonals or anti_diagonal in anti_diagonals:
                    continue
                cols.add(col)
                diagonals.add(diagonal)
                anti_diagonals.add(anti_diagonal)
                backtrack(row + 1, diagonals, anti_diagonals, cols)
                cols.remove(col)
                diagonals.remove(diagonal)
                anti_diagonals.remove(anti_diagonal)
        count = 0
        backtrack(0, set(), set(), set())
        return count
```
##### Time complexity:
O(N!)
##### Space complexity:
O(N)
##### Notes:
Backtracking
None
None
None
    
### >> Comparison: 291 Word Pattern II [Hard] *VS* 52 N-Queens II [Hard]
> Similarity distance: 0.5003
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve pattern matching or arrangement.
- Both questions require finding a solution that satisfies certain constraints.
##### Differences

- Word Pattern II involves matching a pattern in a string, while N-Queens II involves arranging queens on a chessboard.
- Word Pattern II focuses on matching individual characters to words, while N-Queens II focuses on placing queens on the board without attacking each other.
- Word Pattern II has a fixed pattern and a variable string, while N-Queens II has a fixed board size and a variable number of queens.
##### New Insights in 52 N-Queens II [Hard]

- Word Pattern II teaches us how to use backtracking to match a pattern in a string.
- N-Queens II teaches us how to use backtracking to solve a constraint satisfaction problem.
- Both questions provide insights into the power and versatility of backtracking algorithms.


---
# 5. From 52 N-Queens II [Hard] to 51 N-Queens [Hard]
> Similarity Distance: 0.0971

### >> Reminder: 52 N-Queens II [Hard]
The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other. Given an integer n, return the number of distinct solutions to the n-queens puzzle.
##### Optimal Python solution:
```python
class Solution:
    def totalNQueens(self, n: int) -> int:
        def backtrack(row, diagonals, anti_diagonals, cols):
            nonlocal count
            if row == n:
                count += 1
                return
            for col in range(n):
                diagonal = row - col
                anti_diagonal = row + col
                if col in cols or diagonal in diagonals or anti_diagonal in anti_diagonals:
                    continue
                cols.add(col)
                diagonals.add(diagonal)
                anti_diagonals.add(anti_diagonal)
                backtrack(row + 1, diagonals, anti_diagonals, cols)
                cols.remove(col)
                diagonals.remove(diagonal)
                anti_diagonals.remove(anti_diagonal)
        count = 0
        backtrack(0, set(), set(), set())
        return count
```
The essence of this problem is to find the number of distinct solutions to the N-Queens puzzle using backtracking.
    
### >> 51 N-Queens [Hard]
The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other. Given an integer n, return all distinct solutions to the n-queens puzzle.
##### Sample input:
4
##### Sample output:
[
 [".Q..",  // Solution 1
  "...Q",
  "Q...",
  "..Q."],

 ["..Q.",  // Solution 2
  "Q...",
  "...Q",
  ".Q.."]
]

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def backtrack(row, diagonals, anti_diagonals, cols, path):
            if row == n:
                result.append(path)
                return
            for col in range(n):
                diagonal = row - col
                anti_diagonal = row + col
                if col in cols or diagonal in diagonals or anti_diagonal in anti_diagonals:
                    continue
                cols.add(col)
                diagonals.add(diagonal)
                anti_diagonals.add(anti_diagonal)
                backtrack(row + 1, diagonals, anti_diagonals, cols, path + ["." * col + "Q" + "." * (n - col - 1)])
                cols.remove(col)
                diagonals.remove(diagonal)
                anti_diagonals.remove(anti_diagonal)
        result = []
        backtrack(0, set(), set(), set(), [])
        return [['.' * col + 'Q' + '.' * (n - col - 1) for col in solution] for solution in result]
```
##### Time complexity:
O(N!)
##### Space complexity:
O(N)
##### Notes:
Backtracking
None
None
None
    
### >> Comparison: 52 N-Queens II [Hard] *VS* 51 N-Queens [Hard]
> Similarity distance: 0.0971
##### Similarities

- Both 52 N-Queens II and 51 N-Queens are hard-level LeetCode questions.
- Both questions involve solving the N-Queens problem.
- Both questions require finding all possible solutions to the N-Queens problem.
##### Differences

- 52 N-Queens II asks for the total number of distinct solutions, while 51 N-Queens asks for all distinct solutions.
- 52 N-Queens II provides a more efficient solution using backtracking and bit manipulation.
- 51 N-Queens provides a solution using backtracking and recursion.
##### New Insights in 51 N-Queens [Hard]

- 52 N-Queens II introduces the concept of using bit manipulation to optimize the solution.
- Both questions provide insights into solving the N-Queens problem using backtracking.


---
# 6. From 51 N-Queens [Hard] to 351 Android Unlock Patterns [Medium]
> Similarity Distance: 0.6038

### >> Reminder: 51 N-Queens [Hard]
The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other. Given an integer n, return all distinct solutions to the n-queens puzzle.
##### Optimal Python solution:
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def backtrack(row, diagonals, anti_diagonals, cols, path):
            if row == n:
                result.append(path)
                return
            for col in range(n):
                diagonal = row - col
                anti_diagonal = row + col
                if col in cols or diagonal in diagonals or anti_diagonal in anti_diagonals:
                    continue
                cols.add(col)
                diagonals.add(diagonal)
                anti_diagonals.add(anti_diagonal)
                backtrack(row + 1, diagonals, anti_diagonals, cols, path + ["." * col + "Q" + "." * (n - col - 1)])
                cols.remove(col)
                diagonals.remove(diagonal)
                anti_diagonals.remove(anti_diagonal)
        result = []
        backtrack(0, set(), set(), set(), [])
        return [['.' * col + 'Q' + '.' * (n - col - 1) for col in solution] for solution in result]
```
The essence of this problem is to find all distinct solutions to the N-Queens puzzle using backtracking.
    
### >> 351 Android Unlock Patterns [Medium]
Given an Android 3x3 key lock screen and two integers m and n, where 1 ≤ m ≤ n ≤ 9, count the total number of unlock patterns of the Android lock screen, which consist of minimum of m keys and maximum n keys.
##### Sample input:
1
1
##### Sample output:
9

##### Questions to ask to clarify requirements:
What is the range of m and n? Can m be greater than n?

##### Optimal Python solution:
```python
class Solution:
    def numberOfPatterns(self, m: int, n: int) -> int:
        skip = [[0] * 10 for _ in range(10)]
        skip[1][3] = skip[3][1] = 2
        skip[1][7] = skip[7][1] = 4
        skip[3][9] = skip[9][3] = 6
        skip[7][9] = skip[9][7] = 8
        skip[2][8] = skip[8][2] = skip[4][6] = skip[6][4] = skip[1][9] = skip[9][1] = skip[3][7] = skip[7][3] = 5

        def dfs(visited: List[bool], cur: int, remain: int) -> int:
            if remain < 0:
                return 0
            if remain == 0:
                return 1
            visited[cur] = True
            res = 0
            for i in range(1, 10):
                if not visited[i] and (skip[cur][i] == 0 or visited[skip[cur][i]]):
                    res += dfs(visited, i, remain - 1)
            visited[cur] = False
            return res

        res = 0
        visited = [False] * 10
        for i in range(m, n + 1):
            res += dfs(visited, 1, i - 1) * 4
            res += dfs(visited, 2, i - 1) * 4
            res += dfs(visited, 5, i - 1)
        return res
```
##### Time complexity:
O(9!)
##### Space complexity:
O(1)
##### Notes:
1. Use backtracking to generate all possible patterns
2. Use dynamic programming to skip invalid patterns
3. Count the number of valid patterns
Use a skip matrix to skip invalid patterns and optimize the backtracking process.
The skip matrix is used to skip invalid patterns
Avoid using brute force to generate all possible patterns
    
### >> Comparison: 51 N-Queens [Hard] *VS* 351 Android Unlock Patterns [Medium]
> Similarity distance: 0.6038
##### Similarities

- Both questions involve finding a valid configuration of elements.
- Both questions require considering constraints and rules.
- Both questions involve searching for a solution using backtracking.
##### Differences

- 51 N-Queens is about placing queens on a chessboard without attacking each other.
- 351 Android Unlock Patterns is about finding valid patterns to unlock an Android device.
- 51 N-Queens has a fixed board size of 8x8, while 351 Android Unlock Patterns has a variable board size.
- 51 N-Queens has a single solution, while 351 Android Unlock Patterns has multiple possible solutions.
- 51 N-Queens requires considering the constraints of the chessboard and the rules of chess, while 351 Android Unlock Patterns requires considering the constraints of the Android device's lock screen and the rules of pattern formation.
##### New Insights in 351 Android Unlock Patterns [Medium]

- From 51 N-Queens, we can learn how to efficiently solve a constraint satisfaction problem using backtracking.
- From 351 Android Unlock Patterns, we can learn how to generate and validate patterns based on given constraints.

