
# Leetcode Intensive Tutorial Day 61 
> [Difficulty Score: 35]

> [Version: 20231225_200427]

## Courses overview of the day

- 118 Pascal's Triangle [Easy]
  - 140 Word Break II [Hard]
    - 472 Concatenated Words [Hard]
    - 44 Wildcard Matching [Hard]
      - 10 Regular Expression Matching [Hard]
      - 583 Delete Operation for Two Strings [Medium]
        - 97 Interleaving String [Hard]
        - 403 Frog Jump [Hard]
      - 471 Encode String with Shortest Length [Hard]
      - 139 Word Break [Medium]
    - 464 Can I Win [Medium]

#### Steps by steps

 - [1. From 118 Pascal's Triangle [Easy] to 140 Word Break II [Hard]](#1-from-118-pascal's-triangle-easy-to-140-word-break-ii-hard)

 - [2. From 140 Word Break II [Hard] to 472 Concatenated Words [Hard]](#2-from-140-word-break-ii-hard-to-472-concatenated-words-hard)

 - [3. From 140 Word Break II [Hard] to 44 Wildcard Matching [Hard]](#3-from-140-word-break-ii-hard-to-44-wildcard-matching-hard)

 - [4. From 44 Wildcard Matching [Hard] to 10 Regular Expression Matching [Hard]](#4-from-44-wildcard-matching-hard-to-10-regular-expression-matching-hard)

 - [5. From 44 Wildcard Matching [Hard] to 583 Delete Operation for Two Strings [Medium]](#5-from-44-wildcard-matching-hard-to-583-delete-operation-for-two-strings-medium)

 - [6. From 583 Delete Operation for Two Strings [Medium] to 97 Interleaving String [Hard]](#6-from-583-delete-operation-for-two-strings-medium-to-97-interleaving-string-hard)

 - [7. From 583 Delete Operation for Two Strings [Medium] to 403 Frog Jump [Hard]](#7-from-583-delete-operation-for-two-strings-medium-to-403-frog-jump-hard)

 - [8. From 44 Wildcard Matching [Hard] to 471 Encode String with Shortest Length [Hard]](#8-from-44-wildcard-matching-hard-to-471-encode-string-with-shortest-length-hard)

 - [9. From 44 Wildcard Matching [Hard] to 139 Word Break [Medium]](#9-from-44-wildcard-matching-hard-to-139-word-break-medium)

 - [10. From 140 Word Break II [Hard] to 464 Can I Win [Medium]](#10-from-140-word-break-ii-hard-to-464-can-i-win-medium)

#### Summary


- 118 Pascal's Triangle : Generate Pascal's triangle using dynamic programming.
- 97 Interleaving String : The essence of this problem is to find a way to combine two strings in a specific order to form a third string.
- 472 Concatenated Words : The essence of this problem is to find all concatenated words in a given list of words.
- 44 Wildcard Matching : The essence of this problem is to implement wildcard pattern matching using dynamic programming and handle wildcard characters '?' and '*'.
- 140 Word Break II : The essence of the word break II problem is to generate all possible sentences that can be formed from a string using words from a dictionary using dynamic programming and backtracking.
- 139 Word Break : The essence of the word break problem is to determine if a string can be segmented into words from a dictionary using dynamic programming.
- 471 Encode String with Shortest Length : The essence of this problem is to find the optimal way to encode a given string to minimize its length.
- 464 Can I Win : Given the maximum choosable integer and desired total, determine if the first player can force a win in a game where players take turns choosing integers.
- 10 Regular Expression Matching : Implement regular expression matching using dynamic programming.
- 403 Frog Jump : Dynamic programming is used to solve the problem by breaking it down into smaller subproblems and using the solutions of those subproblems to solve the larger problem.
- 583 Delete Operation for Two Strings : The essence of this problem is finding the minimum number of steps required to make two strings the same.
> Similarity Diameter of these problems: 0.6293


---
# 1. From 118 Pascal's Triangle [Easy] to 140 Word Break II [Hard]
> Similarity Distance: 0.4902

### >> 118 Pascal's Triangle [Easy]
Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.
##### Sample input:
5
##### Sample output:
[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

##### Questions to ask to clarify requirements:
What should be the return type of the function? Can numRows be negative?

##### Optimal Python solution:
```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        triangle = []
        for i in range(numRows):
            row = [1] * (i + 1)
            for j in range(1, i):
                row[j] = triangle[i - 1][j - 1] + triangle[i - 1][j]
            triangle.append(row)
        return triangle
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:
1. Generate each row of Pascal's triangle
2. Use dynamic programming to calculate each element
3. Return the generated triangle
Use dynamic programming to calculate each element of the triangle.
Calculating each element using dynamic programming
Using recursion
    
### >> 140 Word Break II [Hard]
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.
##### Sample input:
"catsanddog", ["cat", "cats", "and", "sand", "dog"]
##### Sample output:
["cats and dog", "cat sand dog"]

##### Questions to ask to clarify requirements:
Can the words in the dictionary be used multiple times? Can the words in the dictionary overlap?

##### Optimal Python solution:
```python
def wordBreak(s, wordDict):
    memo = {}
    def backtrack(s):
        if s in memo:
            return memo[s]
        if not s:
            return []
        res = []
        for word in wordDict:
            if s.startswith(word):
                if len(word) == len(s):
                    res.append(word)
                else:
                    rest = backtrack(s[len(word):])
                    for item in rest:
                        res.append(word + ' ' + item)
        memo[s] = res
        return res
    return backtrack(s)
```
##### Time complexity:
O(n^3)
##### Space complexity:
O(n^3)
##### Notes:
1. Use dynamic programming and backtracking to solve the problem.
2. Create a memoization dictionary to store the results of subproblems.
3. Define a backtrack function that takes a string s as input and returns a list of all possible sentences that can be formed from s using words from the dictionary.
4. If the string s is empty, return an empty list.
5. Iterate through all words in the dictionary and check if the string s starts with each word.
6. If a word is found, recursively call the backtrack function on the remaining part of the string and append the word to the result.
7. Memoize the result for the current string s and return the result.
1. Use a combination of dynamic programming and backtracking to solve the problem.
2. Create a memoization dictionary to store the results of subproblems.
3. Define a backtrack function that takes a string s as input and returns a list of all possible sentences that can be formed from s using words from the dictionary.
4. If the string s is empty, return an empty list.
5. Iterate through all words in the dictionary and check if the string s starts with each word.
6. If a word is found, recursively call the backtrack function on the remaining part of the string and append the word to the result.
7. Memoize the result for the current string s and return the result.
1. Use dynamic programming and backtracking to solve the problem.
2. Create a memoization dictionary to store the results of subproblems.
3. Define a backtrack function that takes a string s as input and returns a list of all possible sentences that can be formed from s using words from the dictionary.
4. If the string s is empty, return an empty list.
5. Iterate through all words in the dictionary and check if the string s starts with each word.
6. If a word is found, recursively call the backtrack function on the remaining part of the string and append the word to the result.
7. Memoize the result for the current string s and return the result.
1. Avoid using a brute force approach to check all possible combinations of words from the dictionary.
2. Avoid using recursion without memoization, as it can lead to exponential time complexity.
3. Avoid using a greedy approach, as it may not always give the correct solution.
    
### >> Comparison: 118 Pascal's Triangle [Easy] *VS* 140 Word Break II [Hard]
> Similarity distance: 0.4902
##### Similarities

- Both questions involve manipulating strings or arrays.
- Both questions require dynamic programming techniques.
- Both questions have a time complexity of O(n^2).
##### Differences

- Pascal's Triangle generates a triangle of numbers based on a given number of rows, while Word Break II determines all possible word break combinations for a given string.
- Pascal's Triangle is an easy-level question, while Word Break II is a hard-level question.
- Pascal's Triangle has a space complexity of O(n^2), while Word Break II has a space complexity of O(n^3).
##### New Insights in 140 Word Break II [Hard]

- Pascal's Triangle can be solved using a dynamic programming approach by building the triangle row by row.
- Word Break II can be solved using backtracking and memoization to generate all possible word break combinations.


---
# 2. From 140 Word Break II [Hard] to 472 Concatenated Words [Hard]
> Similarity Distance: 0.3419

### >> Reminder: 140 Word Break II [Hard]
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.
##### Optimal Python solution:
```python
def wordBreak(s, wordDict):
    memo = {}
    def backtrack(s):
        if s in memo:
            return memo[s]
        if not s:
            return []
        res = []
        for word in wordDict:
            if s.startswith(word):
                if len(word) == len(s):
                    res.append(word)
                else:
                    rest = backtrack(s[len(word):])
                    for item in rest:
                        res.append(word + ' ' + item)
        memo[s] = res
        return res
    return backtrack(s)
```
The essence of the word break II problem is to generate all possible sentences that can be formed from a string using words from a dictionary using dynamic programming and backtracking.
    
### >> 472 Concatenated Words [Hard]
Given a list of words, find all concatenated words in the given list of words.
##### Sample input:
["cat","cats","catsdogcats","dog","dogcatsdog","hippopotamuses","rat","ratcatdogcat"]
##### Sample output:
["catsdogcats","dogcatsdog","ratcatdogcat"]

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def findAllConcatenatedWordsInADict(self, words: List[str]) -> List[str]:
        def dfs(word, word_set, memo):
            if word in memo:
                return memo[word]
            for i in range(1, len(word)):
                prefix = word[:i]
                suffix = word[i:]
                if prefix in word_set and suffix in word_set:
                    memo[word] = True
                    return True
                if prefix in word_set and dfs(suffix, word_set, memo):
                    memo[word] = True
                    return True
            memo[word] = False
            return False
        word_set = set(words)
        memo = {}
        result = []
        for word in words:
            word_set.remove(word)
            if dfs(word, word_set, memo):
                result.append(word)
            word_set.add(word)
        return result
```
##### Time complexity:
O(n * m^2)
##### Space complexity:
O(n)
##### Notes:
1. Use recursion and dynamic programming to find all concatenated words.
2. Iterate through all possible prefixes and suffixes of each word.
3. Check if both the prefix and suffix are in the word set.
4. Use memoization to optimize the recursion.
5. Return the list of concatenated words.
None
None
None
    
### >> Comparison: 140 Word Break II [Hard] *VS* 472 Concatenated Words [Hard]
> Similarity distance: 0.3419
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve string manipulation and dynamic programming.
- Both questions require finding valid combinations of words.
- Both questions have multiple possible solutions.
##### Differences

- Question 140 focuses on breaking a given string into valid words, while question 472 focuses on finding concatenated words from a given list.
- Question 140 allows duplicate words in the word list, while question 472 does not.
- Question 140 requires returning all possible valid combinations, while question 472 only requires returning the concatenated words.
- Question 140 has a time complexity of O(n^3), while question 472 has a time complexity of O(n^2 * m), where n is the length of the input string and m is the length of the word list.
##### New Insights in 472 Concatenated Words [Hard]

- Question 140 can be solved using backtracking and memoization to optimize the time complexity.
- Question 472 can be solved using a trie data structure to efficiently check if a word is a concatenated word.


---
# 3. From 140 Word Break II [Hard] to 44 Wildcard Matching [Hard]
> Similarity Distance: 0.3779

### >> Reminder: 140 Word Break II [Hard]
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.
##### Optimal Python solution:
```python
def wordBreak(s, wordDict):
    memo = {}
    def backtrack(s):
        if s in memo:
            return memo[s]
        if not s:
            return []
        res = []
        for word in wordDict:
            if s.startswith(word):
                if len(word) == len(s):
                    res.append(word)
                else:
                    rest = backtrack(s[len(word):])
                    for item in rest:
                        res.append(word + ' ' + item)
        memo[s] = res
        return res
    return backtrack(s)
```
The essence of the word break II problem is to generate all possible sentences that can be formed from a string using words from a dictionary using dynamic programming and backtracking.
    
### >> 44 Wildcard Matching [Hard]
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*'.
##### Sample input:
"aa"
"a*"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the maximum length of the input strings? Can the input strings be empty?

##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        m, n = len(s), len(p)
        dp = [[False] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = True
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 1]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[m][n]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem
2. Initialize the DP table
3. Iterate through the input strings
4. Handle wildcard characters '?' and '*'
5. Update the DP table based on the matching conditions
1. Use a 2D array to represent the DP table
2. Use nested loops to iterate through the input strings
3. Handle wildcard characters separately
4. Use logical OR operator to update the DP table
Handling wildcard characters
Using brute force matching
    
### >> Comparison: 140 Word Break II [Hard] *VS* 44 Wildcard Matching [Hard]
> Similarity distance: 0.3779
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve string matching and pattern matching.
- Both questions require dynamic programming to solve efficiently.
- Both questions have multiple possible solutions.
##### Differences

- Word Break II involves breaking a given string into valid words, while Wildcard Matching involves matching a given string with a wildcard pattern.
- Word Break II requires generating all possible valid word combinations, while Wildcard Matching requires checking if a string matches a given pattern.
- Word Break II has a time complexity of O(n^3), while Wildcard Matching has a time complexity of O(n*m).
- Word Break II can be solved using backtracking or dynamic programming, while Wildcard Matching can be solved using dynamic programming or recursive backtracking.
##### New Insights in 44 Wildcard Matching [Hard]

- Word Break II can be solved using memoization to optimize the dynamic programming solution.
- Wildcard Matching can be solved using a two-pointer approach to optimize the dynamic programming solution.


---
# 4. From 44 Wildcard Matching [Hard] to 10 Regular Expression Matching [Hard]
> Similarity Distance: 0.2770

### >> Reminder: 44 Wildcard Matching [Hard]
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*'.
##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        m, n = len(s), len(p)
        dp = [[False] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = True
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 1]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[m][n]
```
The essence of this problem is to implement wildcard pattern matching using dynamic programming and handle wildcard characters '?' and '*'.
    
### >> 10 Regular Expression Matching [Hard]
Given an input string (s) and a pattern (p), implement regular expression matching with support for '.' and '*'.
##### Sample input:
"aa"
"a*"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What are the possible characters in the input string and pattern?

##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        dp = [[False] * (len(p) + 1) for _ in range(len(s) + 1)]
        dp[0][0] = True
        for j in range(1, len(p) + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 2]
        for i in range(1, len(s) + 1):
            for j in range(1, len(p) + 1):
                if p[j - 1] == '.' or p[j - 1] == s[i - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 2]
                    if p[j - 2] == '.' or p[j - 2] == s[i - 1]:
                        dp[i][j] = dp[i][j] or dp[i - 1][j]
        return dp[-1][-1]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem
2. Time complexity: O(m * n), where m is the length of the input string and n is the length of the pattern
Break down the problem into smaller subproblems and use dynamic programming to solve them.
Handling the '*' wildcard character
Using recursion to solve the problem
    
### >> Comparison: 44 Wildcard Matching [Hard] *VS* 10 Regular Expression Matching [Hard]
> Similarity distance: 0.2770
##### Similarities

- Both questions involve pattern matching with wildcard characters
- Both questions are classified as 'Hard' level difficulty
##### Differences

- Wildcard Matching uses '?' to match any single character, while Regular Expression Matching uses '.' for the same purpose
- Wildcard Matching only supports '?' and '*', while Regular Expression Matching supports more complex regular expression patterns
- Wildcard Matching is more focused on matching file names or simple patterns, while Regular Expression Matching is more general and can handle complex matching scenarios
##### New Insights in 10 Regular Expression Matching [Hard]

- Wildcard Matching can be solved using dynamic programming with a 2D table
- Regular Expression Matching can be solved using recursive backtracking or dynamic programming with a 2D table
- Both problems require careful handling of edge cases and special characters


---
# 5. From 44 Wildcard Matching [Hard] to 583 Delete Operation for Two Strings [Medium]
> Similarity Distance: 0.3703

### >> Reminder: 44 Wildcard Matching [Hard]
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*'.
##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        m, n = len(s), len(p)
        dp = [[False] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = True
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 1]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[m][n]
```
The essence of this problem is to implement wildcard pattern matching using dynamic programming and handle wildcard characters '?' and '*'.
    
### >> 583 Delete Operation for Two Strings [Medium]
Given two strings word1 and word2, return the minimum number of steps required to make word1 and word2 the same.
##### Sample input:
"sea"
"eat"
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the definition of a step? Can we only delete characters or can we also insert or replace characters?

##### Optimal Python solution:
```python
def minDistance(word1: str, word2: str) -> int:
    m, n = len(word1), len(word2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if word1[i - 1] == word2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
            else:
                dp[i][j] = min(dp[i - 1][j], dp[i][j - 1]) + 1
    return dp[m][n]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Initialize a 2D array to store the minimum number of steps required to make substrings of word1 and word2 the same.
3. Iterate through the substrings and update the array based on the characters.
4. Return the value at the bottom-right corner of the array.
1. Break down the problem into smaller subproblems.
2. Use a 2D array to store the intermediate results.
3. Optimize the space complexity by using a 1D array instead of a 2D array.
The trickiest part of this problem is understanding how to update the dynamic programming array.
Avoid using a recursive approach as it will result in exponential time complexity.
    
### >> Comparison: 44 Wildcard Matching [Hard] *VS* 583 Delete Operation for Two Strings [Medium]
> Similarity distance: 0.3703
##### Similarities

- Both questions involve string matching
- Both questions require determining if two strings match
- Both questions involve the use of wildcard characters
##### Differences

- Wildcard Matching is a harder problem compared to Delete Operation for Two Strings
- Wildcard Matching allows the use of '?' to match any single character, while Delete Operation for Two Strings does not
- Delete Operation for Two Strings allows the deletion of characters to match the strings, while Wildcard Matching does not
##### New Insights in 583 Delete Operation for Two Strings [Medium]

- Wildcard Matching requires the use of backtracking or dynamic programming to solve efficiently
- Delete Operation for Two Strings can be solved using the Longest Common Subsequence (LCS) algorithm


---
# 6. From 583 Delete Operation for Two Strings [Medium] to 97 Interleaving String [Hard]
> Similarity Distance: 0.3990

### >> Reminder: 583 Delete Operation for Two Strings [Medium]
Given two strings word1 and word2, return the minimum number of steps required to make word1 and word2 the same.
##### Optimal Python solution:
```python
def minDistance(word1: str, word2: str) -> int:
    m, n = len(word1), len(word2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if word1[i - 1] == word2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
            else:
                dp[i][j] = min(dp[i - 1][j], dp[i][j - 1]) + 1
    return dp[m][n]
```
The essence of this problem is finding the minimum number of steps required to make two strings the same.
    
### >> 97 Interleaving String [Hard]
Given strings s1, s2, and s3, find whether s3 is formed by an interleaving of s1 and s2.
##### Sample input:
"aabcc", "dbbca", "aadbbcbcac"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can we use any character from s1 and s2 to form s3? Can we change the order of characters in s1 and s2?

##### Optimal Python solution:
```python
def isInterleave(s1: str, s2: str, s3: str) -> bool:
    m, n = len(s1), len(s2)
    if len(s3) != m + n:
        return False
    dp = [[False] * (n + 1) for _ in range(m + 1)]
    dp[0][0] = True
    for i in range(m + 1):
        for j in range(n + 1):
            if i > 0 and s1[i - 1] == s3[i + j - 1]:
                dp[i][j] |= dp[i - 1][j]
            if j > 0 and s2[j - 1] == s3[i + j - 1]:
                dp[i][j] |= dp[i][j - 1]
    return dp[m][n]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Create a 2D DP array to store the intermediate results.
3. Initialize the DP array with base cases.
4. Use a nested loop to iterate through the DP array and update the values.
5. Return the final result from the DP array.
1. Use a 2D DP array to store intermediate results.
2. Initialize the DP array with base cases.
3. Use a nested loop to iterate through the DP array and update the values.
1. Be careful with the indices when accessing characters in the strings.
2. Handle the base cases properly.
1. Avoid using recursion as it may lead to exponential time complexity.
2. Avoid using brute force approach as it may be too slow for large inputs.
    
### >> Comparison: 583 Delete Operation for Two Strings [Medium] *VS* 97 Interleaving String [Hard]
> Similarity distance: 0.3990
##### Similarities

- Both questions involve manipulating strings.
- Both questions require finding the minimum number of operations to transform one string into another.
##### Differences

- Question 583 involves deleting characters from the strings, while question 97 involves interleaving characters from two strings.
- Question 583 is rated as medium difficulty, while question 97 is rated as hard difficulty.
##### New Insights in 97 Interleaving String [Hard]

- Question 583 introduces the concept of finding the longest common subsequence between two strings.
- Question 97 introduces the concept of using dynamic programming to solve string manipulation problems.


---
# 7. From 583 Delete Operation for Two Strings [Medium] to 403 Frog Jump [Hard]
> Similarity Distance: 0.5106

### >> Reminder: 583 Delete Operation for Two Strings [Medium]
Given two strings word1 and word2, return the minimum number of steps required to make word1 and word2 the same.
##### Optimal Python solution:
```python
def minDistance(word1: str, word2: str) -> int:
    m, n = len(word1), len(word2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if word1[i - 1] == word2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
            else:
                dp[i][j] = min(dp[i - 1][j], dp[i][j - 1]) + 1
    return dp[m][n]
```
The essence of this problem is finding the minimum number of steps required to make two strings the same.
    
### >> 403 Frog Jump [Hard]
A frog is crossing a river. The river is divided into some number of units, and at each unit, there may or may not exist a stone. The frog can jump on a stone, but it must not jump into the water.

Given a list of stones' positions (in units) in sorted ascending order, determine if the frog can cross the river by landing on the last stone. Initially, the frog is on the first stone and assumes the first jump must be 1 unit.

If the frog's last jump was k units, its next jump must be either k - 1, k, or k + 1 units. The frog can only jump in the forward direction.
##### Sample input:
[0,1,3,5,6,8,12,17]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the frog jump backwards?
- Can the frog jump more than one unit at a time?
- Can the frog jump to any stone or only to adjacent stones?

##### Optimal Python solution:
```python
def canCross(stones):
    n = len(stones)
    dp = [[False] * n for _ in range(n)]
    dp[0][0] = True
    for i in range(1, n):
        for j in range(i - 1, -1, -1):
            k = stones[i] - stones[j]
            if k <= j + 1:
                dp[i][k] = dp[j][k - 1] or dp[j][k] or dp[j][k + 1]
    return any(dp[-1])
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:

- Use dynamic programming to solve the problem
- Create a 2D array to store the states of each stone and its possible jumps
- Initialize the first stone with True
- Iterate through the stones and check if the frog can jump to the current stone from any previous stone

- Use memoization to avoid redundant calculations
- Start with a simple example and try to find the pattern

- Handling the edge cases when the frog is at the first or last stone

- Using recursion without memoization
    
### >> Comparison: 583 Delete Operation for Two Strings [Medium] *VS* 403 Frog Jump [Hard]
> Similarity distance: 0.5106
##### Similarities

- Both questions involve manipulating strings or sequences of characters.
- Both questions require finding the minimum number of operations to transform one string or sequence into another.
- Both questions involve dynamic programming techniques to solve the problem efficiently.
##### Differences

- The 'Delete Operation for Two Strings' question focuses on finding the minimum number of operations (deletions) required to make two strings equal.
- The 'Frog Jump' question focuses on determining if a frog can cross a river by jumping on stones, where each stone has a specific distance it can be jumped.
- The 'Delete Operation for Two Strings' question involves manipulating strings, while the 'Frog Jump' question involves manipulating sequences of numbers.
- The 'Delete Operation for Two Strings' question has a time complexity of O(m*n), where m and n are the lengths of the input strings, while the 'Frog Jump' question has a time complexity of O(n^2), where n is the number of stones in the river.
##### New Insights in 403 Frog Jump [Hard]

- The 'Delete Operation for Two Strings' question introduces the concept of finding the longest common subsequence between two strings.
- The 'Frog Jump' question introduces the concept of using dynamic programming to solve a problem involving sequences of numbers.


---
# 8. From 44 Wildcard Matching [Hard] to 471 Encode String with Shortest Length [Hard]
> Similarity Distance: 0.4079

### >> Reminder: 44 Wildcard Matching [Hard]
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*'.
##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        m, n = len(s), len(p)
        dp = [[False] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = True
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 1]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[m][n]
```
The essence of this problem is to implement wildcard pattern matching using dynamic programming and handle wildcard characters '?' and '*'.
    
### >> 471 Encode String with Shortest Length [Hard]
Given a non-empty string, encode the string such that its encoded length is the shortest.
##### Sample input:
"aaa"
##### Sample output:
"aaa"

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def encode(self, s: str) -> str:
        n = len(s)
        dp = [["" for _ in range(n)] for _ in range(n)]
        for l in range(1, n + 1):
            for i in range(n - l + 1):
                j = i + l - 1
                dp[i][j] = s[i:j + 1]
                if l > 4:
                    for k in range(i, j):
                        if len(dp[i][k]) + len(dp[k + 1][j]) < len(dp[i][j]):
                            dp[i][j] = dp[i][k] + dp[k + 1][j]
                for k in range(i, j):
                    t = s[i:j + 1]
                    p = (t + t).find(t, 1)
                    if p != -1 and p < len(t):
                        t = str(len(t) // p) + '[' + dp[i][i + p - 1] + ']'
                    if len(t) < len(dp[i][j]):
                        dp[i][j] = t
        return dp[0][n - 1]
```
##### Time complexity:
O(n^3)
##### Space complexity:
O(n^2)
##### Notes:
1. Use dynamic programming to find the shortest encoded string.
2. Iterate through all possible substrings and check if they can be encoded more efficiently.
3. Use a 2D array to store the encoded strings for each substring.
4. Return the shortest encoded string for the entire input string.
None
None
None
    
### >> Comparison: 44 Wildcard Matching [Hard] *VS* 471 Encode String with Shortest Length [Hard]
> Similarity distance: 0.4079
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve string manipulation and pattern matching.
- Both questions require finding a matching pattern in a given string.
##### Differences

- Question 44: Wildcard Matching involves matching a string with wildcard characters '?' and '*'.
- Question 471: Encode String with Shortest Length involves encoding a given string using a specific algorithm to minimize its length.
##### New Insights in 471 Encode String with Shortest Length [Hard]

- Question 44: Wildcard Matching requires understanding and implementing a backtracking algorithm to handle wildcard characters.
- Question 471: Encode String with Shortest Length requires understanding and implementing dynamic programming to find the optimal encoding.


---
# 9. From 44 Wildcard Matching [Hard] to 139 Word Break [Medium]
> Similarity Distance: 0.4163

### >> Reminder: 44 Wildcard Matching [Hard]
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*'.
##### Optimal Python solution:
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        m, n = len(s), len(p)
        dp = [[False] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = True
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[0][j] = dp[0][j - 1]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                elif p[j - 1] == '*':
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[m][n]
```
The essence of this problem is to implement wildcard pattern matching using dynamic programming and handle wildcard characters '?' and '*'.
    
### >> 139 Word Break [Medium]
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.
##### Sample input:
"leetcode", ["leet", "code"]
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the words in the dictionary be used multiple times? Can the words in the dictionary overlap?

##### Optimal Python solution:
```python
def wordBreak(s, wordDict):
    n = len(s)
    dp = [False] * (n + 1)
    dp[0] = True
    for i in range(1, n + 1):
        for j in range(i):
            if dp[j] and s[j:i] in wordDict:
                dp[i] = True
                break
    return dp[n]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Create a boolean array dp of size n+1, where dp[i] is True if the substring s[0:i] can be segmented into words from the dictionary.
3. Initialize dp[0] as True, since an empty string can be segmented into words from the dictionary.
4. Iterate through the string s and for each index i, iterate through all indices j less than i.
5. If dp[j] is True and the substring s[j:i] is in the dictionary, set dp[i] as True.
6. Return dp[n], where n is the length of the string s.
1. Use a bottom-up dynamic programming approach to solve the problem.
2. Initialize the dp array with the base case dp[0] = True.
3. Iterate through the string and for each index i, iterate through all indices j less than i.
4. If dp[j] is True and the substring s[j:i] is in the dictionary, set dp[i] as True.
5. Return dp[n], where n is the length of the string s.
1. Use a dynamic programming approach to solve the problem.
2. Initialize a boolean array dp of size n+1, where dp[i] is True if the substring s[0:i] can be segmented into words from the dictionary.
3. Iterate through the string s and for each index i, iterate through all indices j less than i.
4. If dp[j] is True and the substring s[j:i] is in the dictionary, set dp[i] as True.
5. Return dp[n], where n is the length of the string s.
1. Avoid using a brute force approach to check all possible combinations of words from the dictionary.
2. Avoid using recursion without memoization, as it can lead to exponential time complexity.
3. Avoid using a greedy approach, as it may not always give the correct solution.
    
### >> Comparison: 44 Wildcard Matching [Hard] *VS* 139 Word Break [Medium]
> Similarity distance: 0.4163
##### Similarities

- Both questions involve pattern matching or string matching.
- Both questions require determining if a given string matches a given pattern.
- Both questions have a dynamic programming solution approach.
##### Differences

- Wildcard Matching uses '?' to match any single character and '*' to match any sequence of characters, while Word Break checks if a string can be segmented into a space-separated sequence of dictionary words.
- Wildcard Matching has a more complex pattern matching mechanism compared to Word Break.
- Wildcard Matching has a time complexity of O(m*n), where m and n are the lengths of the pattern and the string, respectively. Word Break has a time complexity of O(n^2), where n is the length of the string.
##### New Insights in 139 Word Break [Medium]

- Wildcard Matching can be solved using a dynamic programming approach with a 2D matrix to store the intermediate results.
- Word Break can be solved using a dynamic programming approach with a 1D array to store the intermediate results.


---
# 10. From 140 Word Break II [Hard] to 464 Can I Win [Medium]
> Similarity Distance: 0.5128

### >> Reminder: 140 Word Break II [Hard]
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.
##### Optimal Python solution:
```python
def wordBreak(s, wordDict):
    memo = {}
    def backtrack(s):
        if s in memo:
            return memo[s]
        if not s:
            return []
        res = []
        for word in wordDict:
            if s.startswith(word):
                if len(word) == len(s):
                    res.append(word)
                else:
                    rest = backtrack(s[len(word):])
                    for item in rest:
                        res.append(word + ' ' + item)
        memo[s] = res
        return res
    return backtrack(s)
```
The essence of the word break II problem is to generate all possible sentences that can be formed from a string using words from a dictionary using dynamic programming and backtracking.
    
### >> 464 Can I Win [Medium]
In the "100 game" two players take turns adding, to a running total, any integer from 1 to 10. The player who first causes the running total to reach or exceed 100 wins. What if we change the game so that players cannot re-use integers? For example, two players might take turns drawing from a common pool of numbers from 1 to 15 without replacement until they reach a total >= 100. Given an integer maxChoosableInteger and another integer desiredTotal, determine if the first player to move can force a win, assuming both players play optimally. You can always assume that maxChoosableInteger will not be larger than 20 and desiredTotal will not be larger than 300.
##### Sample input:
maxChoosableInteger = 10, desiredTotal = 11
##### Sample output:
false

##### Questions to ask to clarify requirements:

- Can the players choose the same number in different turns?
- Is there a limit on the number of turns?
- Can the players choose any integer from 1 to maxChoosableInteger in each turn?

##### Optimal Python solution:
```python
def canIWin(maxChoosableInteger, desiredTotal):
    if desiredTotal <= maxChoosableInteger:
        return True
    if (maxChoosableInteger + 1) * maxChoosableInteger / 2 < desiredTotal:
        return False
    memo = {}
    return canWin(tuple(range(1, maxChoosableInteger + 1)), desiredTotal, memo)

def canWin(choices, desiredTotal, memo):
    if choices[-1] >= desiredTotal:
        return True
    if choices in memo:
        return memo[choices]
    for i in range(len(choices)):
        if not canWin(choices[:i] + choices[i+1:], desiredTotal - choices[i], memo):
            memo[choices] = True
            return True
    memo[choices] = False
    return False
```
##### Time complexity:
O(2^n)
##### Space complexity:
O(2^n)
##### Notes:

- Use dynamic programming to memoize the results of subproblems
- Simulate the game by recursively trying all possible moves

- Break down the problem into smaller subproblems
- Use memoization to avoid redundant calculations

- Handling large values of maxChoosableInteger and desiredTotal efficiently

- Using brute force to try all possible moves
    
### >> Comparison: 140 Word Break II [Hard] *VS* 464 Can I Win [Medium]
> Similarity distance: 0.5128
##### Similarities

- Both questions are dynamic programming problems.
- Both questions involve finding a solution based on a given set of constraints.
##### Differences

- Word Break II is a hard-level problem, while Can I Win is a medium-level problem.
- Word Break II involves breaking a given string into valid words, while Can I Win involves determining if the first player can win a game.
- Word Break II requires generating all possible valid word combinations, while Can I Win requires finding a winning strategy.
- Word Break II has a time complexity of O(n^3), while Can I Win has a time complexity of O(2^n).
##### New Insights in 464 Can I Win [Medium]

- Word Break II can be solved using backtracking and memoization.
- Can I Win can be solved using a minimax algorithm.

