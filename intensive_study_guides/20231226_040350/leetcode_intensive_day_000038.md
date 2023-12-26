
# Leetcode Intensive Tutorial Day 38 
> [Difficulty Score: 20]

> [Version: 20231226_040350]

> [Including this day, you had studied : 316 leetcode problems]


## Courses overview of the day

- 459 Repeated Substring Pattern [Easy]
  - 161 One Edit Distance [Medium]
    - 392 Is Subsequence [Easy]
      - 567 Permutation in String [Medium]
        - 87 Scramble String [Hard]
        - 306 Additive Number [Medium]
          - 293 Flip Game [Easy]
            - 294 Flip Game II [Medium]
  - 394 Decode String [Medium]
    - 385 Mini Parser [Medium]
      - 401 Binary Watch [Easy]

#### Step by step

 - [1. From 459 Repeated Substring Pattern [Easy] to 161 One Edit Distance [Medium]](#1-from-459-repeated-substring-pattern-easy-to-161-one-edit-distance-medium))

 - [2. From 161 One Edit Distance [Medium] to 392 Is Subsequence [Easy]](#2-from-161-one-edit-distance-medium-to-392-is-subsequence-easy))

 - [3. From 392 Is Subsequence [Easy] to 567 Permutation in String [Medium]](#3-from-392-is-subsequence-easy-to-567-permutation-in-string-medium))

 - [4. From 567 Permutation in String [Medium] to 87 Scramble String [Hard]](#4-from-567-permutation-in-string-medium-to-87-scramble-string-hard))

 - [5. From 567 Permutation in String [Medium] to 306 Additive Number [Medium]](#5-from-567-permutation-in-string-medium-to-306-additive-number-medium))

 - [6. From 306 Additive Number [Medium] to 293 Flip Game [Easy]](#6-from-306-additive-number-medium-to-293-flip-game-easy))

 - [7. From 293 Flip Game [Easy] to 294 Flip Game II [Medium]](#7-from-293-flip-game-easy-to-294-flip-game-ii-medium))

 - [8. From 459 Repeated Substring Pattern [Easy] to 394 Decode String [Medium]](#8-from-459-repeated-substring-pattern-easy-to-394-decode-string-medium))

 - [9. From 394 Decode String [Medium] to 385 Mini Parser [Medium]](#9-from-394-decode-string-medium-to-385-mini-parser-medium))

 - [10. From 385 Mini Parser [Medium] to 401 Binary Watch [Easy]](#10-from-385-mini-parser-medium-to-401-binary-watch-easy))

    

#### Summary


- 87 Scramble String : The essence of this problem is to use recursion and memoization to check if s2 is a scrambled string of s1.
- 459 Repeated Substring Pattern : Check if the given string is a repeated substring pattern.
- 293 Flip Game : The essence of the solution is to iterate through the input string and find consecutive '+' signs. For each pair of consecutive '+' signs, create a new string by replacing them with '--'. Add the new string to the result list and return it.
- 385 Mini Parser : The essence of this problem is to parse a nested list of integers represented as a string.
- 306 Additive Number : The essence of this problem is to generate all possible additive numbers by splitting the input string and checking if each substring forms an additive sequence.
- 392 Is Subsequence : Check if a string is a subsequence of another string.
- 567 Permutation in String : The essence of this problem is to efficiently check if s2 contains a permutation of s1 using a sliding window approach.
- 394 Decode String : Decoding an encoded string using a stack.
- 161 One Edit Distance : Comparing characters of two strings using two pointers.
- 294 Flip Game II : The essence of the solution is to iterate through the input string and find consecutive '+' signs. For each pair of consecutive '+' signs, create a new string by replacing them with '--'. Recursively call the function with the new string. If the recursive call returns False, return True. If no valid move is found, return False.
- 401 Binary Watch : The essence of this problem is to generate all possible combinations of hours and minutes and check if the number of '1' digits in the binary representation is equal to the given number.
> Similarity Diameter of these problems: 0.8017


---
# 1. From 459 Repeated Substring Pattern [Easy] to 161 One Edit Distance [Medium]
> Similarity Distance: 0.5639

### >> 459 Repeated Substring Pattern [Easy]
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.
##### Sample input:
"abab"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the substring be empty? Can the substring be the entire string?

##### Optimal Python solution:
```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        return s in (s + s)[1:-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. The repeated substring must be at least half the length of the original string.
2. The repeated substring must be a divisor of the original string.
3. The repeated substring must occur at least twice in the original string.
1. Use the slicing technique to check if a string is a substring of another string.
2. Use the property of divisors to optimize solutions.
1. Using the slicing technique to check if the given string is a repeated substring pattern.
2. Using the property of divisors to optimize the solution.
1. Using brute force to check all possible substrings.
2. Using regular expressions to solve the problem.
    
### >> 161 One Edit Distance [Medium]
Given two strings s and t, return true if they are both one edit distance apart, otherwise return false.
##### Sample input:
"ab", "acb"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the definition of one edit distance? Can the strings be empty?

##### Optimal Python solution:
```python
class Solution:
    def isOneEditDistance(self, s: str, t: str) -> bool:
        m, n = len(s), len(t)
        if abs(m - n) > 1:
            return False
        if m > n:
            return self.isOneEditDistance(t, s)
        for i in range(m):
            if s[i] != t[i]:
                if m == n:
                    return s[i + 1:] == t[i + 1:]
                else:
                    return s[i:] == t[i + 1:]
        return m + 1 == n
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use two pointers to compare the characters of the two strings. If a difference is found, check if the remaining substrings are equal.
Handle the case when the strings have different lengths by adjusting the indices accordingly.
Handling the case when the strings have different lengths.
Using built-in functions like editdistance.
    
### >> Comparison: 459 Repeated Substring Pattern [Easy] *VS* 161 One Edit Distance [Medium]
> Similarity distance: 0.5639
##### Similarities

- Both questions involve string manipulation.
- Both questions have a specific pattern or condition to check.
##### Differences

- 459 Repeated Substring Pattern checks if a string can be formed by repeating a substring, while 161 One Edit Distance checks if two strings are one edit distance apart.
- 459 Repeated Substring Pattern has a time complexity of O(n^2), while 161 One Edit Distance has a time complexity of O(n).
- 459 Repeated Substring Pattern is classified as an Easy level question, while 161 One Edit Distance is classified as a Medium level question.
##### New Insights in 161 One Edit Distance [Medium]

- From 459 Repeated Substring Pattern, we can learn how to check if a string can be formed by repeating a substring.
- From 161 One Edit Distance, we can learn how to check if two strings are one edit distance apart.


---
# 2. From 161 One Edit Distance [Medium] to 392 Is Subsequence [Easy]
> Similarity Distance: 0.4641

### >> Reminder: 161 One Edit Distance [Medium]
Given two strings s and t, return true if they are both one edit distance apart, otherwise return false.
##### Optimal Python solution:
```python
class Solution:
    def isOneEditDistance(self, s: str, t: str) -> bool:
        m, n = len(s), len(t)
        if abs(m - n) > 1:
            return False
        if m > n:
            return self.isOneEditDistance(t, s)
        for i in range(m):
            if s[i] != t[i]:
                if m == n:
                    return s[i + 1:] == t[i + 1:]
                else:
                    return s[i:] == t[i + 1:]
        return m + 1 == n
```
Comparing characters of two strings using two pointers.
    
### >> 392 Is Subsequence [Easy]
Given a string s and a string t, check if s is a subsequence of t.
##### Sample input:

- "abc"
- "ahbgdc"
##### Sample output:

- true

##### Questions to ask to clarify requirements:

- Can the characters in s be in any order?
- Can s be an empty string?
- Can t be an empty string?

##### Optimal Python solution:
```python

- class Solution:
-     def isSubsequence(self, s: str, t: str) -> bool:
-         i = 0
-         for char in t:
-             if i < len(s) and char == s[i]:
-                 i += 1
-         return i == len(s)
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- The characters in s must appear in the same order in t
- The characters in s do not have to be consecutive in t

- Use two pointers to efficiently check for matching characters.
- Handle edge cases such as empty strings.

- Handling the case where the characters in s can be in any order
- Handling the case where s is an empty string
- Handling the case where t is an empty string

- Using brute force to check all possible subsequences
    
### >> Comparison: 161 One Edit Distance [Medium] *VS* 392 Is Subsequence [Easy]
> Similarity distance: 0.4641
##### Similarities

- Both questions involve comparing two strings.
- Both questions require determining if there is a specific relationship between the strings.
##### Differences

- One Edit Distance: Determines if two strings are exactly one edit distance apart.
- Is Subsequence: Determines if one string is a subsequence of another string.
##### New Insights in 392 Is Subsequence [Easy]

- One Edit Distance: The specific relationship is that the two strings can be transformed into each other by performing exactly one edit operation (insertion, deletion, or substitution).
- Is Subsequence: The specific relationship is that one string can be formed by deleting some characters from another string while maintaining the relative order of the remaining characters.


---
# 3. From 392 Is Subsequence [Easy] to 567 Permutation in String [Medium]
> Similarity Distance: 0.5549

### >> Reminder: 392 Is Subsequence [Easy]
Given a string s and a string t, check if s is a subsequence of t.
##### Optimal Python solution:
```python

- class Solution:
-     def isSubsequence(self, s: str, t: str) -> bool:
-         i = 0
-         for char in t:
-             if i < len(s) and char == s[i]:
-                 i += 1
-         return i == len(s)
```
Check if a string is a subsequence of another string.
    
### >> 567 Permutation in String [Medium]
Given two strings s1 and s2, return true if s2 contains the permutation of s1.
##### Sample input:
"ab"
"eidbaooo"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the input strings contain uppercase letters? Can the input strings contain spaces or special characters?

##### Optimal Python solution:
```python
def checkInclusion(s1: str, s2: str) -> bool:
    if len(s1) > len(s2):
        return False
    s1_count = [0] * 26
    s2_count = [0] * 26
    for i in range(len(s1)):
        s1_count[ord(s1[i]) - ord('a')] += 1
        s2_count[ord(s2[i]) - ord('a')] += 1
    if s1_count == s2_count:
        return True
    for i in range(len(s1), len(s2)):
        s2_count[ord(s2[i]) - ord('a')] += 1
        s2_count[ord(s2[i - len(s1)]) - ord('a')] -= 1
        if s1_count == s2_count:
            return True
    return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use a sliding window approach to check if s2 contains a permutation of s1. Maintain a count of characters in s1 and s2 using arrays. Compare the counts to determine if they are equal.
Use arrays to efficiently maintain the count of characters. Start with a window of size equal to the length of s1 and slide it through s2.
The trickiest part of this problem is to efficiently maintain the count of characters in s1 and s2.
Avoid using a brute force approach to check all possible permutations of s1 in s2.
    
### >> Comparison: 392 Is Subsequence [Easy] *VS* 567 Permutation in String [Medium]
> Similarity distance: 0.5549
##### Similarities

- Both questions involve string manipulation.
- Both questions require checking if one string is a subsequence of another string.
##### Differences

- Question 392 is an easy level question, while question 567 is a medium level question.
- Question 392 only requires checking if one string is a subsequence, while question 567 requires checking if one string is a permutation of another string.
- Question 392 can be solved using a two-pointer approach, while question 567 requires a sliding window approach.
- Question 392 has a linear time complexity solution, while question 567 has a solution with a time complexity of O(n^2).
##### New Insights in 567 Permutation in String [Medium]

- Question 567 introduces the concept of permutations and requires understanding how to check if one string is a permutation of another string.
- Question 567 requires a sliding window approach, which is a useful technique for solving string manipulation problems.


---
# 4. From 567 Permutation in String [Medium] to 87 Scramble String [Hard]
> Similarity Distance: 0.5619

### >> Reminder: 567 Permutation in String [Medium]
Given two strings s1 and s2, return true if s2 contains the permutation of s1.
##### Optimal Python solution:
```python
def checkInclusion(s1: str, s2: str) -> bool:
    if len(s1) > len(s2):
        return False
    s1_count = [0] * 26
    s2_count = [0] * 26
    for i in range(len(s1)):
        s1_count[ord(s1[i]) - ord('a')] += 1
        s2_count[ord(s2[i]) - ord('a')] += 1
    if s1_count == s2_count:
        return True
    for i in range(len(s1), len(s2)):
        s2_count[ord(s2[i]) - ord('a')] += 1
        s2_count[ord(s2[i - len(s1)]) - ord('a')] -= 1
        if s1_count == s2_count:
            return True
    return False
```
The essence of this problem is to efficiently check if s2 contains a permutation of s1 using a sliding window approach.
    
### >> 87 Scramble String [Hard]
Given two strings s1 and s2 of the same length, determine if s2 is a scrambled string of s1.
##### Sample input:
"great"
"rgeat"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the input strings contain any characters? Can the input strings be empty?

##### Optimal Python solution:
```python
def isScramble(s1: str, s2: str) -> bool:
    if s1 == s2:
        return True
    if sorted(s1) != sorted(s2):
        return False
    for i in range(1, len(s1)):
        if isScramble(s1[:i], s2[:i]) and isScramble(s1[i:], s2[i:]):
            return True
        if isScramble(s1[:i], s2[-i:]) and isScramble(s1[i:], s2[:-i]):
            return True
    return False
```
##### Time complexity:
O(n^4)
##### Space complexity:
O(n^3)
##### Notes:
1. Use recursion to check if s2 is a scrambled string of s1.
2. Sort the characters in s1 and s2 to check if they are anagrams.
3. Divide s1 and s2 into two parts and recursively check if the parts are scrambled strings.
4. Time complexity is O(n^4) and space complexity is O(n^3), where n is the length of the strings.
Use memoization to optimize the recursive solution.
The recursive solution has exponential time complexity. Use memoization to optimize the solution.
Avoid using brute force approach to check all possible combinations of substrings.
    
### >> Comparison: 567 Permutation in String [Medium] *VS* 87 Scramble String [Hard]
> Similarity distance: 0.5619
##### Similarities

- Both questions involve manipulating strings to check for certain patterns or permutations.
- Both questions require checking if one string can be formed by rearranging the characters of another string.
##### Differences

- The 'Permutation in String' question requires finding if any permutation of one string is a substring of another string.
- The 'Scramble String' question requires finding if one string can be scrambled to form another string.
##### New Insights in 87 Scramble String [Hard]

- The 'Permutation in String' question can be solved using a sliding window approach to efficiently check for permutations.
- The 'Scramble String' question can be solved using dynamic programming to check for all possible scrambles of the string.


---
# 5. From 567 Permutation in String [Medium] to 306 Additive Number [Medium]
> Similarity Distance: 0.6026

### >> Reminder: 567 Permutation in String [Medium]
Given two strings s1 and s2, return true if s2 contains the permutation of s1.
##### Optimal Python solution:
```python
def checkInclusion(s1: str, s2: str) -> bool:
    if len(s1) > len(s2):
        return False
    s1_count = [0] * 26
    s2_count = [0] * 26
    for i in range(len(s1)):
        s1_count[ord(s1[i]) - ord('a')] += 1
        s2_count[ord(s2[i]) - ord('a')] += 1
    if s1_count == s2_count:
        return True
    for i in range(len(s1), len(s2)):
        s2_count[ord(s2[i]) - ord('a')] += 1
        s2_count[ord(s2[i - len(s1)]) - ord('a')] -= 1
        if s1_count == s2_count:
            return True
    return False
```
The essence of this problem is to efficiently check if s2 contains a permutation of s1 using a sliding window approach.
    
### >> 306 Additive Number [Medium]
A string is called additive if every substring of length greater than or equal to 3 forms an additive sequence. Given a string containing only digits, return all possible additive numbers you can create by splitting the string.
##### Sample input:

- "112358"
##### Sample output:

- "1,1,2,3,5,8"
- "1,12,13,25,38"
- "11,2,3,5,8"
- "11,23,5,8"

##### Questions to ask to clarify requirements:

- Can the input string contain leading zeros?
- Can the input string be empty?
- What is the maximum length of the input string?

##### Optimal Python solution:
```python

- class Solution:
-     def isAdditiveNumber(self, num: str) -> bool:
-         def backtrack(start: int, num1: int, num2: int) -> bool:
-             if start == len(num):
-                 return True
-             for i in range(start, len(num)):
-                 if num[start] == '0' and i > start:
-                     break
-                 curr = int(num[start:i+1])
-                 if num1 is None or num2 is None or num1 + num2 == curr:
-                     if backtrack(i+1, num2, curr):
-                         return True
-             return False
-         for i in range(len(num)-2):
-             if num[0] == '0' and i > 0:
-                 break
-             num1 = int(num[:i+1])
-             for j in range(i+1, len(num)-1):
-                 if num[i+1] == '0' and j > i+1:
-                     break
-                 num2 = int(num[i+1:j+1])
-                 if backtrack(j+1, num1, num2):
-                     return True
-         return False
```
##### Time complexity:
O(n^3)
##### Space complexity:
O(n)
##### Notes:

- Use backtracking to generate all possible additive numbers
- Check if each substring forms an additive sequence

- Understand the backtracking algorithm and its implementation.
- Optimize the solution by avoiding unnecessary computations.
- Handle edge cases for leading zeros.

- Generating all possible additive numbers using backtracking
- Checking if each substring forms an additive sequence

- Brute force approach of checking all possible substrings
    
### >> Comparison: 567 Permutation in String [Medium] *VS* 306 Additive Number [Medium]
> Similarity distance: 0.6026
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve string manipulation.
- Both questions require checking for a specific pattern in the string.
##### Differences

- 567 Permutation in String requires finding if one string is a permutation of another, while 306 Additive Number requires finding if a string represents an additive sequence.
- 567 Permutation in String requires considering all possible permutations of a string, while 306 Additive Number requires considering all possible additive sequences.
- 567 Permutation in String requires a sliding window approach, while 306 Additive Number requires a recursive approach.
- 567 Permutation in String has a time complexity of O(n), while 306 Additive Number has a time complexity of O(n^2).
##### New Insights in 306 Additive Number [Medium]

- 567 Permutation in String: The sliding window approach can be used to efficiently check if one string is a permutation of another.
- 306 Additive Number: The recursive approach can be used to efficiently check if a string represents an additive sequence.


---
# 6. From 306 Additive Number [Medium] to 293 Flip Game [Easy]
> Similarity Distance: 0.6200

### >> Reminder: 306 Additive Number [Medium]
A string is called additive if every substring of length greater than or equal to 3 forms an additive sequence. Given a string containing only digits, return all possible additive numbers you can create by splitting the string.
##### Optimal Python solution:
```python

- class Solution:
-     def isAdditiveNumber(self, num: str) -> bool:
-         def backtrack(start: int, num1: int, num2: int) -> bool:
-             if start == len(num):
-                 return True
-             for i in range(start, len(num)):
-                 if num[start] == '0' and i > start:
-                     break
-                 curr = int(num[start:i+1])
-                 if num1 is None or num2 is None or num1 + num2 == curr:
-                     if backtrack(i+1, num2, curr):
-                         return True
-             return False
-         for i in range(len(num)-2):
-             if num[0] == '0' and i > 0:
-                 break
-             num1 = int(num[:i+1])
-             for j in range(i+1, len(num)-1):
-                 if num[i+1] == '0' and j > i+1:
-                     break
-                 num2 = int(num[i+1:j+1])
-                 if backtrack(j+1, num1, num2):
-                     return True
-         return False
```
The essence of this problem is to generate all possible additive numbers by splitting the input string and checking if each substring forms an additive sequence.
    
### >> 293 Flip Game [Easy]
You are playing a Flip Game with your friend. You are given a string currentState that contains only '+' and '-'. You and your friend take turns to flip two consecutive '++' into '--'. The game ends when a person can no longer make a move, and therefore the other person will be the winner. Return all possible states of the string after one valid move.
##### Sample input:
"++++"
##### Sample output:
["--++", "+--+", "++--"]

##### Questions to ask to clarify requirements:
1. Can the input string be empty?
2. Can there be more than two consecutive '+' signs?
3. Can there be other characters in the input string?
4. Can the input string contain spaces?
5. Can the input string be very long?

##### Optimal Python solution:
```python
def generatePossibleNextMoves(currentState):
    result = []
    for i in range(len(currentState) - 1):
        if currentState[i] == '+' and currentState[i + 1] == '+':
            result.append(currentState[:i] + '--' + currentState[i + 2:])
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Iterate through the input string and check for consecutive '+' signs.
2. If found, create a new string by replacing the consecutive '+' signs with '--'.
3. Add the new string to the result list.
4. Return the result list.
None
None
None
    
### >> Comparison: 306 Additive Number [Medium] *VS* 293 Flip Game [Easy]
> Similarity distance: 0.6200
##### Similarities
Both questions involve manipulating strings.
##### Differences

- 306 Additive Number requires checking if a string can be split into additive numbers, while 293 Flip Game requires finding all possible states after flipping a substring.
- 306 Additive Number is a medium-level question, while 293 Flip Game is an easy-level question.
- 306 Additive Number involves mathematical calculations, while 293 Flip Game involves simple string manipulation.
- 306 Additive Number requires a recursive approach, while 293 Flip Game can be solved using a simple loop.
##### New Insights in 293 Flip Game [Easy]

- From 306 Additive Number, we can learn how to check if a string can be split into additive numbers.
- From 293 Flip Game, we can learn how to generate all possible states by flipping a substring.


---
# 7. From 293 Flip Game [Easy] to 294 Flip Game II [Medium]
> Similarity Distance: 0.4061

### >> Reminder: 293 Flip Game [Easy]
You are playing a Flip Game with your friend. You are given a string currentState that contains only '+' and '-'. You and your friend take turns to flip two consecutive '++' into '--'. The game ends when a person can no longer make a move, and therefore the other person will be the winner. Return all possible states of the string after one valid move.
##### Optimal Python solution:
```python
def generatePossibleNextMoves(currentState):
    result = []
    for i in range(len(currentState) - 1):
        if currentState[i] == '+' and currentState[i + 1] == '+':
            result.append(currentState[:i] + '--' + currentState[i + 2:])
    return result
```
The essence of the solution is to iterate through the input string and find consecutive '+' signs. For each pair of consecutive '+' signs, create a new string by replacing them with '--'. Add the new string to the result list and return it.
    
### >> 294 Flip Game II [Medium]
You are playing a Flip Game with your friend. You are given a string currentState that contains only '+' and '-'. You and your friend take turns to flip two consecutive '++' into '--'. The game ends when a person can no longer make a move, and therefore the other person will be the winner. Write a function to determine if the starting player can guarantee a win.
##### Sample input:
"++++"
##### Sample output:
true

##### Questions to ask to clarify requirements:
1. Can the input string be empty?
2. Can there be more than two consecutive '+' signs?
3. Can there be other characters in the input string?
4. Can the input string contain spaces?
5. Can the input string be very long?

##### Optimal Python solution:
```python
def canWin(s):
    if len(s) < 2:
        return False
    for i in range(len(s) - 1):
        if s[i] == '+' and s[i + 1] == '+':
            if not canWin(s[:i] + '--' + s[i + 2:]):
                return True
    return False
```
##### Time complexity:
O(n!)
##### Space complexity:
O(n)
##### Notes:
1. Iterate through the input string and check for consecutive '+' signs.
2. If found, create a new string by replacing the consecutive '+' signs with '--'.
3. Recursively call the function with the new string.
4. If the recursive call returns False, return True.
5. If no valid move is found, return False.
None
None
None
    
### >> Comparison: 293 Flip Game [Easy] *VS* 294 Flip Game II [Medium]
> Similarity distance: 0.4061
##### Similarities

- Both questions involve flipping a sequence of characters.
- Both questions have a similar goal of finding the final state of the sequence after flipping.
##### Differences

- 293 Flip Game [Easy] requires finding all possible states of the sequence after flipping a pair of adjacent characters.
- 294 Flip Game II [Medium] requires determining if the first player can guarantee a win by flipping characters in the sequence.
##### New Insights in 294 Flip Game II [Medium]

- 293 Flip Game [Easy] can be solved by iterating through the sequence and checking for adjacent characters that are the same.
- 294 Flip Game II [Medium] can be solved using the Sprague-Grundy theorem to determine the game's outcome.


---
# 8. From 459 Repeated Substring Pattern [Easy] to 394 Decode String [Medium]
> Similarity Distance: 0.6421

### >> Reminder: 459 Repeated Substring Pattern [Easy]
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.
##### Optimal Python solution:
```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        return s in (s + s)[1:-1]
```
Check if the given string is a repeated substring pattern.
    
### >> 394 Decode String [Medium]
Given an encoded string, return its decoded string.
##### Sample input:
"3[a]2[bc]"
##### Sample output:
"aaabcbc"

##### Questions to ask to clarify requirements:

- What is the maximum length of the input string?
- Can the input string be empty?

##### Optimal Python solution:
```python
def decodeString(s):
    stack = []
    curr_num = 0
    curr_str = ''
    for char in s:
        if char.isdigit():
            curr_num = curr_num * 10 + int(char)
        elif char == '[':
            stack.append(curr_str)
            stack.append(curr_num)
            curr_str = ''
            curr_num = 0
        elif char == ']':
            num = stack.pop()
            prev_str = stack.pop()
            curr_str = prev_str + curr_str * num
        else:
            curr_str += char
    return curr_str
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a stack to keep track of the current number and string.
- Handle nested encoded strings by pushing and popping from the stack.
- Build the decoded string by repeating the current string based on the current number.

- Understand the encoding and decoding rules.
- Use a stack to handle nested structures.

- Handling nested encoded strings.
- Building the decoded string based on the current number.

- Using regular expressions or built-in string manipulation functions.
    
### >> Comparison: 459 Repeated Substring Pattern [Easy] *VS* 394 Decode String [Medium]
> Similarity distance: 0.6421
##### Similarities

- Both questions involve string manipulation.
- Both questions require understanding of patterns in strings.
##### Differences

- 459 Repeated Substring Pattern is an easy level question, while 394 Decode String is a medium level question.
- 459 Repeated Substring Pattern focuses on finding repeated substrings, while 394 Decode String focuses on decoding a given string.
- 459 Repeated Substring Pattern requires identifying if a string can be formed by repeating a substring, while 394 Decode String requires decoding a string based on a given pattern.
##### New Insights in 394 Decode String [Medium]

- From 459 Repeated Substring Pattern, we can learn how to check if a string can be formed by repeating a substring.
- From 394 Decode String, we can learn how to decode a given string based on a given pattern.


---
# 9. From 394 Decode String [Medium] to 385 Mini Parser [Medium]
> Similarity Distance: 0.5326

### >> Reminder: 394 Decode String [Medium]
Given an encoded string, return its decoded string.
##### Optimal Python solution:
```python
def decodeString(s):
    stack = []
    curr_num = 0
    curr_str = ''
    for char in s:
        if char.isdigit():
            curr_num = curr_num * 10 + int(char)
        elif char == '[':
            stack.append(curr_str)
            stack.append(curr_num)
            curr_str = ''
            curr_num = 0
        elif char == ']':
            num = stack.pop()
            prev_str = stack.pop()
            curr_str = prev_str + curr_str * num
        else:
            curr_str += char
    return curr_str
```
Decoding an encoded string using a stack.
    
### >> 385 Mini Parser [Medium]
Given a nested list of integers represented as a string, implement a parser to deserialize it.
##### Sample input:
[[1,1],2,[1,1]]
##### Sample output:
[[1,1],2,[1,1]]

##### Questions to ask to clarify requirements:
What is the maximum depth of the input string? Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def deserialize(self, s: str) -> NestedInteger:
        stack = []
        num = ''
        for c in s:
            if c == '[':
                stack.append(NestedInteger())
            elif c == ']':
                if num:
                    stack[-1].add(NestedInteger(int(num)))
                    num = ''
                ni = stack.pop()
                if stack:
                    stack[-1].add(ni)
                else:
                    return ni
            elif c == ',':
                if num:
                    stack[-1].add(NestedInteger(int(num)))
                    num = ''
            else:
                num += c
        return NestedInteger(int(s))
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to keep track of nested lists
2. Use a variable to store the current number
3. Handle different characters in the input string
Use a stack to keep track of nested lists. Handle different characters in the input string.
Handling the different characters in the input string
Using recursion
    
### >> Comparison: 394 Decode String [Medium] *VS* 385 Mini Parser [Medium]
> Similarity distance: 0.5326
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve parsing and manipulating strings.
- Both questions require understanding and implementing a specific grammar.
- Both questions involve recursive parsing and processing of nested structures.
##### Differences

- 394 Decode String focuses on decoding a string based on a specific grammar.
- 385 Mini Parser focuses on parsing and evaluating a nested data structure.
- 394 Decode String uses a stack to keep track of the nested structures.
- 385 Mini Parser uses recursion to parse and evaluate the nested structures.
- 394 Decode String has a specific grammar that defines how the string should be decoded.
- 385 Mini Parser can handle different types of nested structures, including integers, lists, and nested lists.
##### New Insights in 385 Mini Parser [Medium]

- From 394 Decode String, we can learn how to use a stack to handle nested structures.
- From 385 Mini Parser, we can learn how to recursively parse and evaluate nested data structures.
- Both questions provide insights into handling and manipulating strings in a specific grammar.


---
# 10. From 385 Mini Parser [Medium] to 401 Binary Watch [Easy]
> Similarity Distance: 0.6660

### >> Reminder: 385 Mini Parser [Medium]
Given a nested list of integers represented as a string, implement a parser to deserialize it.
##### Optimal Python solution:
```python
class Solution:
    def deserialize(self, s: str) -> NestedInteger:
        stack = []
        num = ''
        for c in s:
            if c == '[':
                stack.append(NestedInteger())
            elif c == ']':
                if num:
                    stack[-1].add(NestedInteger(int(num)))
                    num = ''
                ni = stack.pop()
                if stack:
                    stack[-1].add(ni)
                else:
                    return ni
            elif c == ',':
                if num:
                    stack[-1].add(NestedInteger(int(num)))
                    num = ''
            else:
                num += c
        return NestedInteger(int(s))
```
The essence of this problem is to parse a nested list of integers represented as a string.
    
### >> 401 Binary Watch [Easy]
Given a non-negative integer n which represents the number of LEDs that are currently on, return all possible times the watch could represent.
##### Sample input:
1

##### Sample output:
["0:01","0:02","0:04","0:08","0:16","0:32","1:00","2:00","4:00","8:00"]


##### Questions to ask to clarify requirements:
What is the maximum number of LEDs that can be on? Can the time be in 24-hour format?

##### Optimal Python solution:
```python
class Solution:
    def readBinaryWatch(self, num: int) -> List[str]:
        res = []
        for h in range(12):
            for m in range(60):
                if (bin(h) + bin(m)).count('1') == num:
                    res.append('%d:%02d' % (h, m))
        return res

```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. Use nested loops to iterate through all possible hours and minutes.
2. Use the bin() function to convert integers to binary strings.
3. Use the count() method to count the number of '1' digits in the binary representation.
4. Format the hours and minutes as strings using the %d and %02d format specifiers.
5. Append the formatted time to the result list.
1. Use the bin() function to convert integers to binary strings.
2. Use the count() method to count the number of '1' digits in a string.
3. Format strings using the %d and %02d format specifiers.
None
None
    
### >> Comparison: 385 Mini Parser [Medium] *VS* 401 Binary Watch [Easy]
> Similarity distance: 0.6660
##### Similarities

- Both questions involve parsing and manipulating data structures.
- Both questions require understanding of number representation and manipulation.
- Both questions involve iterating through a given input.
##### Differences

- 385 Mini Parser involves parsing a nested list structure, while 401 Binary Watch involves manipulating binary representations of time.
- 385 Mini Parser requires handling multiple data types (integers and nested lists), while 401 Binary Watch only deals with integers.
- 385 Mini Parser requires building a nested data structure, while 401 Binary Watch involves counting the number of possible time combinations.
- 385 Mini Parser has a more complex input format, while 401 Binary Watch has a simpler input format.
##### New Insights in 401 Binary Watch [Easy]

- 385 Mini Parser teaches how to parse and manipulate nested data structures, which is a common task in many programming scenarios.
- 401 Binary Watch teaches how to manipulate binary representations of numbers, which can be useful in various applications.
- Both questions provide practice in iterating through a given input and performing operations based on specific conditions.

