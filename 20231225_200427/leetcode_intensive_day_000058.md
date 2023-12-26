
# Leetcode Intensive Tutorial Day 58 
> [Difficulty Score: 26]

> [Version: 20231225_200427]

## Courses overview of the day

- 516 Longest Palindromic Subsequence [Medium]
  - 5 Longest Palindromic Substring [Medium]
    - 214 Shortest Palindrome [Hard]
      - 564 Find the Closest Palindrome [Hard]
        - 479 Largest Palindrome Product [Hard]
          - 267 Palindrome Permutation II [Medium]
    - 340 Longest Substring with At Most K Distinct Characters [Medium]
      - 159 Longest Substring with At Most Two Distinct Characters [Medium]
        - 3 Longest Substring Without Repeating Characters [Medium]
      - 424 Longest Repeating Character Replacement [Medium]

#### Steps by steps

 - [1. From 516 Longest Palindromic Subsequence [Medium] to 5 Longest Palindromic Substring [Medium]](#1-from-516-longest-palindromic-subsequence-medium-to-5-longest-palindromic-substring-medium)

 - [2. From 5 Longest Palindromic Substring [Medium] to 214 Shortest Palindrome [Hard]](#2-from-5-longest-palindromic-substring-medium-to-214-shortest-palindrome-hard)

 - [3. From 214 Shortest Palindrome [Hard] to 564 Find the Closest Palindrome [Hard]](#3-from-214-shortest-palindrome-hard-to-564-find-the-closest-palindrome-hard)

 - [4. From 564 Find the Closest Palindrome [Hard] to 479 Largest Palindrome Product [Hard]](#4-from-564-find-the-closest-palindrome-hard-to-479-largest-palindrome-product-hard)

 - [5. From 479 Largest Palindrome Product [Hard] to 267 Palindrome Permutation II [Medium]](#5-from-479-largest-palindrome-product-hard-to-267-palindrome-permutation-ii-medium)

 - [6. From 5 Longest Palindromic Substring [Medium] to 340 Longest Substring with At Most K Distinct Characters [Medium]](#6-from-5-longest-palindromic-substring-medium-to-340-longest-substring-with-at-most-k-distinct-characters-medium)

 - [7. From 340 Longest Substring with At Most K Distinct Characters [Medium] to 159 Longest Substring with At Most Two Distinct Characters [Medium]](#7-from-340-longest-substring-with-at-most-k-distinct-characters-medium-to-159-longest-substring-with-at-most-two-distinct-characters-medium)

 - [8. From 159 Longest Substring with At Most Two Distinct Characters [Medium] to 3 Longest Substring Without Repeating Characters [Medium]](#8-from-159-longest-substring-with-at-most-two-distinct-characters-medium-to-3-longest-substring-without-repeating-characters-medium)

 - [9. From 340 Longest Substring with At Most K Distinct Characters [Medium] to 424 Longest Repeating Character Replacement [Medium]](#9-from-340-longest-substring-with-at-most-k-distinct-characters-medium-to-424-longest-repeating-character-replacement-medium)

#### Summary


- 564 Find the Closest Palindrome : Find the closest palindrome to a given string by finding the smaller and larger palindromes.
- 516 Longest Palindromic Subsequence : Use dynamic programming to find the length of the longest palindromic subsequence in a string.
- 5 Longest Palindromic Substring : The essence of the problem is to find the longest palindromic substring in a given string.
- 479 Largest Palindrome Product : The essence of this problem is to find the largest palindrome made from the product of two n-digit numbers.
- 159 Longest Substring with At Most Two Distinct Characters : The essence of this problem is to find the longest substring with at most two distinct characters using a sliding window approach.
- 340 Longest Substring with At Most K Distinct Characters : The essence of this problem is to find the longest substring with at most k distinct characters using a sliding window approach.
- 267 Palindrome Permutation II : The essence of this problem is to generate all palindromic permutations of a given string.
- 214 Shortest Palindrome : The essence of this problem is to find the shortest palindrome by adding characters in front of the given string.
- 424 Longest Repeating Character Replacement : The essence of this problem is using a sliding window to find the longest sub-string containing all repeating letters and adjusting the window based on the maximum count and the value of k.
- 3 Longest Substring Without Repeating Characters : The essence of this problem is to find the longest substring without repeating characters using a sliding window approach.
> Similarity Diameter of these problems: 0.7218


---
# 1. From 516 Longest Palindromic Subsequence [Medium] to 5 Longest Palindromic Substring [Medium]
> Similarity Distance: 0.2770

### >> 516 Longest Palindromic Subsequence [Medium]
Given a string s, find the longest palindromic subsequence's length in s.
##### Sample input:
"bbbab"
##### Sample output:
4

##### Questions to ask to clarify requirements:

- Can the string be empty?
- Can the string have spaces or special characters?
- Is the input case-sensitive?

##### Optimal Python solution:
```python
def longestPalindromeSubseq(self, s: str) -> int:
    n = len(s)
    dp = [[0] * n for _ in range(n)]
    for i in range(n-1, -1, -1):
        dp[i][i] = 1
        for j in range(i+1, n):
            if s[i] == s[j]:
                dp[i][j] = dp[i+1][j-1] + 2
            else:
                dp[i][j] = max(dp[i+1][j], dp[i][j-1])
    return dp[0][n-1]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:

- Use dynamic programming to solve the problem
- Create a 2D array to store the lengths of palindromic subsequences
- Fill the array diagonally from bottom right to top left

- Create a 2D array to store the lengths of palindromic subsequences
- Fill the array diagonally from bottom right to top left

- Filling the 2D array diagonally
- Handling the base cases

- Using recursion for solving the problem
    
### >> 5 Longest Palindromic Substring [Medium]
Given a string s, return the longest palindromic substring in s.
##### Sample input:
"babad"
##### Sample output:
"bab"

##### Questions to ask to clarify requirements:
What should be returned if there are multiple longest palindromic substrings?

##### Optimal Python solution:
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def expandAroundCenter(left, right):
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left+1:right]
        if len(s) < 2:
            return s
        res = ""
        for i in range(len(s)):
            odd = expandAroundCenter(i, i)
            even = expandAroundCenter(i, i+1)
            res = max(res, odd, even, key=len)
        return res
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(1)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Expand around center to find palindromic substrings.
3. Return the longest palindromic substring.
1. Break down the problem into smaller subproblems.
2. Use helper functions to simplify the code.
1. Handle the case when the length of the string is less than 2.
2. Handle the case when the length of the string is even.
1. Avoid using brute force approach.
2. Avoid unnecessary calculations.
    
### >> Comparison: 516 Longest Palindromic Subsequence [Medium] *VS* 5 Longest Palindromic Substring [Medium]
> Similarity distance: 0.2770
##### Similarities

- Both questions are related to finding the longest palindromic subsequence or substring.
- Both questions have a medium difficulty level.
##### Differences

- Question 516 focuses on finding the longest palindromic subsequence, while question 5 focuses on finding the longest palindromic substring.
- Question 516 requires finding the length of the longest palindromic subsequence, while question 5 requires finding the actual substring.
- Question 516 allows characters to be skipped in order to form a palindromic subsequence, while question 5 requires consecutive characters in the substring.
##### New Insights in 5 Longest Palindromic Substring [Medium]

- Both questions require dynamic programming to solve efficiently.
- Both questions can be solved using a similar approach based on subproblems and memoization.
- Both questions can be solved using a bottom-up dynamic programming approach.


---
# 2. From 5 Longest Palindromic Substring [Medium] to 214 Shortest Palindrome [Hard]
> Similarity Distance: 0.4207

### >> Reminder: 5 Longest Palindromic Substring [Medium]
Given a string s, return the longest palindromic substring in s.
##### Optimal Python solution:
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def expandAroundCenter(left, right):
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left+1:right]
        if len(s) < 2:
            return s
        res = ""
        for i in range(len(s)):
            odd = expandAroundCenter(i, i)
            even = expandAroundCenter(i, i+1)
            res = max(res, odd, even, key=len)
        return res
```
The essence of the problem is to find the longest palindromic substring in a given string.
    
### >> 214 Shortest Palindrome [Hard]
You are given a string s. You can convert s to a palindrome by adding characters in front of it. Return the shortest palindrome you can find by performing this transformation.
##### Sample input:
"aacecaaa"
##### Sample output:
"aaacecaaa"

##### Questions to ask to clarify requirements:
Can I assume that the input string will always have at least one character? Can I assume that the input string will always have at most 5000 characters? Can I assume that the input string will only contain lowercase letters?

##### Optimal Python solution:
```python
def shortestPalindrome(s):
    n = len(s)
    rev = s[::-1]
    for i in range(n):
        if s[:n-i] == rev[i:]:
            return rev[:i] + s
    return ""
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
The problem can be solved by finding the longest palindrome substring starting from the beginning of the string. Reverse the remaining part of the string and append it to the beginning of the original string.
Use string manipulation techniques to solve the problem. Break down the problem into smaller subproblems. Use variables to store intermediate results.
Finding the longest palindrome substring starting from the beginning of the string. Reversing the remaining part of the string.
Using brute force to try all possible substrings. Using recursion to solve the problem.
    
### >> Comparison: 5 Longest Palindromic Substring [Medium] *VS* 214 Shortest Palindrome [Hard]
> Similarity distance: 0.4207
##### Similarities

- Both questions involve finding palindromic substrings in a given string.
- Both questions require finding the longest or shortest palindromic substring.
- Both questions have a complexity requirement of O(n^2) or better.
##### Differences

- The 'Longest Palindromic Substring' question asks for the longest palindromic substring in the given string.
- The 'Shortest Palindrome' question asks for the shortest palindrome that can be formed by adding characters to the beginning of the given string.
##### New Insights in 214 Shortest Palindrome [Hard]

- The 'Longest Palindromic Substring' question can be solved using dynamic programming or expanding around the center approach.
- The 'Shortest Palindrome' question can be solved using the KMP algorithm or the Manacher's algorithm.


---
# 3. From 214 Shortest Palindrome [Hard] to 564 Find the Closest Palindrome [Hard]
> Similarity Distance: 0.4353

### >> Reminder: 214 Shortest Palindrome [Hard]
You are given a string s. You can convert s to a palindrome by adding characters in front of it. Return the shortest palindrome you can find by performing this transformation.
##### Optimal Python solution:
```python
def shortestPalindrome(s):
    n = len(s)
    rev = s[::-1]
    for i in range(n):
        if s[:n-i] == rev[i:]:
            return rev[:i] + s
    return ""
```
The essence of this problem is to find the shortest palindrome by adding characters in front of the given string.
    
### >> 564 Find the Closest Palindrome [Hard]
Given a string n representing an integer, return the closest integer (not including itself), which is a palindrome.
If there is a tie, return the smaller one as the answer.
A palindrome is a string that reads the same backward as forward.
##### Sample input:
123
##### Sample output:
121

##### Questions to ask to clarify requirements:

- What should be the output if the input string is already a palindrome?
- What should be the output if there is no smaller or larger palindrome?

##### Optimal Python solution:
```python
class Solution:
    def nearestPalindromic(self, n: str) -> str:
        def is_palindrome(s):
            return s == s[::-1]
        num = int(n)
        smaller = larger = num
        while True:
            smaller -= 1
            larger += 1
            if is_palindrome(str(smaller)):
                return str(smaller)
            if is_palindrome(str(larger)):
                return str(larger)
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- A palindrome is a string that reads the same backward as forward.
- The closest palindrome is the smaller or larger palindrome that is closest to the input string.
- If there is a tie, return the smaller one as the answer.

- Use a helper function to check if a number is a palindrome.
- Start with the input number and decrement it to find the smaller palindrome.
- Increment the input number to find the larger palindrome.

- Handling tie cases

- Brute force solution
    
### >> Comparison: 214 Shortest Palindrome [Hard] *VS* 564 Find the Closest Palindrome [Hard]
> Similarity distance: 0.4353
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve finding palindromes.
- Both questions require string manipulation.
##### Differences

- Question 214 involves finding the shortest palindrome by adding characters to the beginning of the given string.
- Question 564 involves finding the closest palindrome by modifying the given string.
- Question 214 has a linear time complexity solution, while question 564 has a quadratic time complexity solution.
##### New Insights in 564 Find the Closest Palindrome [Hard]

- Question 214 teaches us how to efficiently find the shortest palindrome by utilizing the concept of the longest proper suffix that is also a prefix.
- Question 564 introduces the concept of finding the closest palindrome by considering different cases and making modifications to the given string.


---
# 4. From 564 Find the Closest Palindrome [Hard] to 479 Largest Palindrome Product [Hard]
> Similarity Distance: 0.4807

### >> Reminder: 564 Find the Closest Palindrome [Hard]
Given a string n representing an integer, return the closest integer (not including itself), which is a palindrome.
If there is a tie, return the smaller one as the answer.
A palindrome is a string that reads the same backward as forward.
##### Optimal Python solution:
```python
class Solution:
    def nearestPalindromic(self, n: str) -> str:
        def is_palindrome(s):
            return s == s[::-1]
        num = int(n)
        smaller = larger = num
        while True:
            smaller -= 1
            larger += 1
            if is_palindrome(str(smaller)):
                return str(smaller)
            if is_palindrome(str(larger)):
                return str(larger)
```
Find the closest palindrome to a given string by finding the smaller and larger palindromes.
    
### >> 479 Largest Palindrome Product [Hard]
Find the largest palindrome made from the product of two n-digit numbers.
##### Sample input:
2

Output:
987

Explanation:
The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 × 99.
##### Sample output:
9009

##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be 0?

##### Optimal Python solution:
```python
class Solution:
    def largestPalindrome(self, n: int) -> int:
        if n == 1:
            return 9
        upper = 10 ** n - 1
        lower = upper // 10
        max_product = upper * upper
        first_half = max_product // (10 ** n)
        while True:
            palindrome = int(str(first_half) + str(first_half)[::-1])
            for i in range(upper, lower - 1, -1):
                if palindrome // i > upper:
                    break
                if palindrome % i == 0:
                    return palindrome % 1337
            first_half -= 1

```
##### Time complexity:
O(10^n)
##### Space complexity:
O(1)
##### Notes:
1. The largest palindrome product of two n-digit numbers can be found by iterating through all possible first halves of the palindrome and checking if it can be formed by multiplying two n-digit numbers.
2. Start with the largest possible first half of the palindrome and decrement it until a valid palindrome is found.
3. Check if the palindrome can be formed by multiplying two n-digit numbers by iterating through all possible second halves of the palindrome and checking if it is divisible by any n-digit number.
4. Return the largest palindrome modulo 1337.
1. Use integer division and modulo operators to extract digits from a number.
2. Use string concatenation and reversal to generate palindromes.
3. Use a loop to iterate through all possible values of a variable.
4. Use the break statement to exit a loop early.
1. Generating the first half of the palindrome by decrementing it from the largest possible value.
2. Checking if the palindrome can be formed by multiplying two n-digit numbers by iterating through all possible second halves of the palindrome.
3. Finding the largest palindrome modulo 1337.
1. Generating all possible palindromes and checking if they can be formed by multiplying two n-digit numbers.
2. Checking if a number is a palindrome by converting it to a string and comparing it with its reverse.
3. Checking if a number is divisible by another number by using the modulo operator.
    
### >> Comparison: 564 Find the Closest Palindrome [Hard] *VS* 479 Largest Palindrome Product [Hard]
> Similarity distance: 0.4807
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve finding palindromes.
- Both questions require manipulating numbers to find the desired palindrome.
##### Differences

- 564 Find the Closest Palindrome: The goal is to find the closest palindrome to a given number.
- 479 Largest Palindrome Product: The goal is to find the largest palindrome that is a product of two n-digit numbers.
##### New Insights in 479 Largest Palindrome Product [Hard]

- 564 Find the Closest Palindrome: The insight is to consider different cases and compare the differences to find the closest palindrome.
- 479 Largest Palindrome Product: The insight is to use mathematical properties to optimize the search for the largest palindrome product.


---
# 5. From 479 Largest Palindrome Product [Hard] to 267 Palindrome Permutation II [Medium]
> Similarity Distance: 0.5009

### >> Reminder: 479 Largest Palindrome Product [Hard]
Find the largest palindrome made from the product of two n-digit numbers.
##### Optimal Python solution:
```python
class Solution:
    def largestPalindrome(self, n: int) -> int:
        if n == 1:
            return 9
        upper = 10 ** n - 1
        lower = upper // 10
        max_product = upper * upper
        first_half = max_product // (10 ** n)
        while True:
            palindrome = int(str(first_half) + str(first_half)[::-1])
            for i in range(upper, lower - 1, -1):
                if palindrome // i > upper:
                    break
                if palindrome % i == 0:
                    return palindrome % 1337
            first_half -= 1

```
The essence of this problem is to find the largest palindrome made from the product of two n-digit numbers.
    
### >> 267 Palindrome Permutation II [Medium]
Given a string s, return all the palindromic permutations (without duplicates) of it. Return an empty list if no palindromic permutation could be form.
##### Sample input:
"aabb"
##### Sample output:
["abba", "baab"]

##### Questions to ask to clarify requirements:
Can the input string contain spaces? Can the input string contain special characters? Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def generatePalindromes(self, s: str) -> List[str]:
        counter = collections.Counter(s)
        odd = [char for char, count in counter.items() if count % 2]
        if len(odd) > 1:
            return []
        mid = ''
        if odd:
            mid = odd[0]
            counter[mid] -= 1
        half = ''.join([char * (count // 2) for char, count in counter.items()])
        permutations = set(itertools.permutations(half))
        return [''.join(p) + mid + ''.join(p[::-1]) for p in permutations]
```
##### Time complexity:
O(n!)
##### Space complexity:
O(n)
##### Notes:
1. Use Counter to count the frequency of each character
2. Check if there is more than one character with an odd frequency
3. If there is, return an empty list
4. If there is only one character with an odd frequency, use it as the middle character
5. Generate all possible permutations of the half string
6. Combine each permutation with the middle character and its reverse
7. Return the list of palindromic permutations
1. Use the Counter class to count the frequency of characters
2. Use the itertools.permutations function to generate all possible permutations
1. Handling the case when there are more than one character with an odd frequency
2. Generating all possible permutations of the half string
1. Using a brute force approach to generate all possible permutations
2. Using a nested loop to check if a permutation is a palindrome
    
### >> Comparison: 479 Largest Palindrome Product [Hard] *VS* 267 Palindrome Permutation II [Medium]
> Similarity distance: 0.5009
##### Similarities

- Both questions involve palindromes
- Both questions require finding the largest palindrome
##### Differences

- 479 involves finding the largest palindrome product of two n-digit numbers
- 267 involves generating all possible palindromic permutations of a given string
##### New Insights in 267 Palindrome Permutation II [Medium]

- 479 teaches us how to efficiently find the largest palindrome product using mathematical properties
- 267 teaches us how to generate palindromic permutations using backtracking


---
# 6. From 5 Longest Palindromic Substring [Medium] to 340 Longest Substring with At Most K Distinct Characters [Medium]
> Similarity Distance: 0.4618

### >> Reminder: 5 Longest Palindromic Substring [Medium]
Given a string s, return the longest palindromic substring in s.
##### Optimal Python solution:
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def expandAroundCenter(left, right):
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left+1:right]
        if len(s) < 2:
            return s
        res = ""
        for i in range(len(s)):
            odd = expandAroundCenter(i, i)
            even = expandAroundCenter(i, i+1)
            res = max(res, odd, even, key=len)
        return res
```
The essence of the problem is to find the longest palindromic substring in a given string.
    
### >> 340 Longest Substring with At Most K Distinct Characters [Medium]
Given a string s and an integer k, return the length of the longest substring of s that contains at most k distinct characters.
##### Sample input:
"eceba", 2
##### Sample output:
3

##### Questions to ask to clarify requirements:
What should be the output if the string is empty? Can the string contain special characters or spaces?

##### Optimal Python solution:
```python
def lengthOfLongestSubstringKDistinct(s, k):
    if k == 0:
        return 0
    left = 0
    right = 0
    counter = {}
    max_length = 0
    while right < len(s):
        counter[s[right]] = counter.get(s[right], 0) + 1
        while len(counter) > k:
            counter[s[left]] -= 1
            if counter[s[left]] == 0:
                del counter[s[left]]
            left += 1
        max_length = max(max_length, right - left + 1)
        right += 1
    return max_length
```
##### Time complexity:
O(N)
##### Space complexity:
O(K)
##### Notes:
1. Use a sliding window approach with two pointers to find the longest substring.
2. Use a counter to keep track of the number of distinct characters in the current substring.
3. Update the counter and the pointers as you move through the string.
Make sure to handle the case when the string is empty. Use a counter to keep track of the number of distinct characters.
Handling the counter and updating the pointers can be tricky. Make sure to handle the case when k is 0.
Avoid using a brute-force approach to check all possible substrings as it would be inefficient.
    
### >> Comparison: 5 Longest Palindromic Substring [Medium] *VS* 340 Longest Substring with At Most K Distinct Characters [Medium]
> Similarity distance: 0.4618
##### Similarities

- Both questions involve finding the longest substring with certain constraints.
- Both questions have a medium difficulty level.
##### Differences

- The first question focuses on finding the longest palindromic substring.
- The second question focuses on finding the longest substring with at most k distinct characters.
##### New Insights in 340 Longest Substring with At Most K Distinct Characters [Medium]

- The first question requires identifying palindromic substrings, which can be done using dynamic programming or expanding around the center approach.
- The second question requires maintaining a sliding window and a hashmap to track the distinct characters.


---
# 7. From 340 Longest Substring with At Most K Distinct Characters [Medium] to 159 Longest Substring with At Most Two Distinct Characters [Medium]
> Similarity Distance: 0.2880

### >> Reminder: 340 Longest Substring with At Most K Distinct Characters [Medium]
Given a string s and an integer k, return the length of the longest substring of s that contains at most k distinct characters.
##### Optimal Python solution:
```python
def lengthOfLongestSubstringKDistinct(s, k):
    if k == 0:
        return 0
    left = 0
    right = 0
    counter = {}
    max_length = 0
    while right < len(s):
        counter[s[right]] = counter.get(s[right], 0) + 1
        while len(counter) > k:
            counter[s[left]] -= 1
            if counter[s[left]] == 0:
                del counter[s[left]]
            left += 1
        max_length = max(max_length, right - left + 1)
        right += 1
    return max_length
```
The essence of this problem is to find the longest substring with at most k distinct characters using a sliding window approach.
    
### >> 159 Longest Substring with At Most Two Distinct Characters [Medium]
Given a string s, find the length of the longest substring that contains at most two distinct characters.
##### Sample input:
"eceba"
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the maximum length of the input string? Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def lengthOfLongestSubstringTwoDistinct(self, s: str) -> int:
        if len(s) < 3:
            return len(s)
        left, right = 0, 0
        max_len = 2
        char_count = {s[0]: 1}
        while right < len(s) - 1:
            right += 1
            char_count[s[right]] = char_count.get(s[right], 0) + 1
            if len(char_count) > 2:
                char_count[s[left]] -= 1
                if char_count[s[left]] == 0:
                    del char_count[s[left]]
                left += 1
            max_len = max(max_len, right - left + 1)
        return max_len
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use a sliding window approach to find the longest substring with at most two distinct characters. Use a hashmap to keep track of the count of each character in the current window.
Start with a simple example and walk through the algorithm step by step to understand how it works.
Handling the case when the input string has less than three characters.
Using a brute force approach to check all possible substrings.
    
### >> Comparison: 340 Longest Substring with At Most K Distinct Characters [Medium] *VS* 159 Longest Substring with At Most Two Distinct Characters [Medium]
> Similarity distance: 0.2880
##### Similarities

- Both questions are about finding the longest substring with a limited number of distinct characters.
- Both questions have a constraint on the maximum number of distinct characters allowed in the substring.
##### Differences

- Question 340 allows at most K distinct characters, while question 159 allows at most two distinct characters.
- Question 340 has a larger maximum number of distinct characters compared to question 159.
- Question 340 is more general than question 159.
##### New Insights in 159 Longest Substring with At Most Two Distinct Characters [Medium]

- By solving question 340, we can gain insights into solving question 159.
- Solving question 159 can help us understand a specific case of question 340.


---
# 8. From 159 Longest Substring with At Most Two Distinct Characters [Medium] to 3 Longest Substring Without Repeating Characters [Medium]
> Similarity Distance: 0.2742

### >> Reminder: 159 Longest Substring with At Most Two Distinct Characters [Medium]
Given a string s, find the length of the longest substring that contains at most two distinct characters.
##### Optimal Python solution:
```python
class Solution:
    def lengthOfLongestSubstringTwoDistinct(self, s: str) -> int:
        if len(s) < 3:
            return len(s)
        left, right = 0, 0
        max_len = 2
        char_count = {s[0]: 1}
        while right < len(s) - 1:
            right += 1
            char_count[s[right]] = char_count.get(s[right], 0) + 1
            if len(char_count) > 2:
                char_count[s[left]] -= 1
                if char_count[s[left]] == 0:
                    del char_count[s[left]]
                left += 1
            max_len = max(max_len, right - left + 1)
        return max_len
```
The essence of this problem is to find the longest substring with at most two distinct characters using a sliding window approach.
    
### >> 3 Longest Substring Without Repeating Characters [Medium]
Given a string s, find the length of the longest substring without repeating characters.
##### Sample input:
"abcabcbb"
##### Sample output:
3

##### Questions to ask to clarify requirements:
What should be the output if the input string is empty?

##### Optimal Python solution:
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        start = 0
        max_len = 0
        char_map = {}
        for end in range(len(s)):
            if s[end] in char_map:
                start = max(start, char_map[s[end]] + 1)
            char_map[s[end]] = end
            max_len = max(max_len, end - start + 1)
        return max_len
```
##### Time complexity:
O(n)
##### Space complexity:
O(min(n, m))
##### Notes:
Use a sliding window approach with two pointers to track the longest substring without repeating characters. Use a hashmap to store the last occurrence of each character.
Use a hashmap to store the last occurrence of each character. Update the start pointer to the maximum of its current value and the index of the last occurrence of the current character plus one.
Handling the case when the input string is empty.
Using brute force approach to check all possible substrings.
    
### >> Comparison: 159 Longest Substring with At Most Two Distinct Characters [Medium] *VS* 3 Longest Substring Without Repeating Characters [Medium]
> Similarity distance: 0.2742
##### Similarities

- Both questions involve finding the longest substring without repeating characters.
- Both questions have a sliding window approach as a possible solution.
- Both questions have a time complexity of O(n).
##### Differences

- Question 159 allows at most two distinct characters in the substring, while question 3 allows any number of distinct characters.
- Question 159 requires finding the length of the longest substring, while question 3 requires returning the actual substring.
- Question 159 is considered a more advanced problem compared to question 3.
##### New Insights in 3 Longest Substring Without Repeating Characters [Medium]

- Question 159 introduces the concept of handling substrings with at most two distinct characters, which can be useful in other scenarios.
- Question 3 provides a foundation for understanding and solving more complex substring problems.
- Both questions improve problem-solving skills and understanding of string manipulation.


---
# 9. From 340 Longest Substring with At Most K Distinct Characters [Medium] to 424 Longest Repeating Character Replacement [Medium]
> Similarity Distance: 0.3720

### >> Reminder: 340 Longest Substring with At Most K Distinct Characters [Medium]
Given a string s and an integer k, return the length of the longest substring of s that contains at most k distinct characters.
##### Optimal Python solution:
```python
def lengthOfLongestSubstringKDistinct(s, k):
    if k == 0:
        return 0
    left = 0
    right = 0
    counter = {}
    max_length = 0
    while right < len(s):
        counter[s[right]] = counter.get(s[right], 0) + 1
        while len(counter) > k:
            counter[s[left]] -= 1
            if counter[s[left]] == 0:
                del counter[s[left]]
            left += 1
        max_length = max(max_length, right - left + 1)
        right += 1
    return max_length
```
The essence of this problem is to find the longest substring with at most k distinct characters using a sliding window approach.
    
### >> 424 Longest Repeating Character Replacement [Medium]
Given a string s that consists of only uppercase English letters, you can perform at most k operations on that string. In one operation, you can choose any character of the string and change it to any other uppercase English character. Find the length of the longest sub-string containing all repeating letters you can get after performing the above operations.
##### Sample input:
"ABAB",
2
##### Sample output:
4

##### Questions to ask to clarify requirements:
What is the range of k? Can k be greater than the length of the string?

##### Optimal Python solution:
```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        max_length = 0
        max_count = 0
        counts = [0] * 26
        start = 0
        for end in range(len(s)):
            counts[ord(s[end]) - ord('A')] += 1
            max_count = max(max_count, counts[ord(s[end]) - ord('A')])
            if end - start + 1 - max_count > k:
                counts[ord(s[start]) - ord('A')] -= 1
                start += 1
            max_length = max(max_length, end - start + 1)
        return max_length
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a sliding window to find the longest sub-string containing all repeating letters.
2. Keep track of the maximum count of any letter in the current window.
3. Adjust the window based on the maximum count and the value of k.
1. Use a sliding window to find the longest sub-string containing all repeating letters.
2. Keep track of the maximum count of any letter in the current window.
3. Adjust the window based on the maximum count and the value of k.
The trickiest part of this problem is determining when to adjust the window.
Avoid using a brute force approach to check all possible sub-strings.
    
### >> Comparison: 340 Longest Substring with At Most K Distinct Characters [Medium] *VS* 424 Longest Repeating Character Replacement [Medium]
> Similarity distance: 0.3720
##### Similarities

- Both questions are related to finding the longest substring with specific conditions.
- Both questions have a sliding window approach as the optimal solution.
- Both questions have a time complexity of O(n).
##### Differences

- 340: Longest Substring with At Most K Distinct Characters focuses on finding the longest substring with at most K distinct characters.
- 424: Longest Repeating Character Replacement focuses on finding the longest substring by replacing characters with any other character to maximize the length.
##### New Insights in 424 Longest Repeating Character Replacement [Medium]

- 340: Longest Substring with At Most K Distinct Characters teaches us how to use a sliding window approach to solve substring problems with a specific constraint.
- 424: Longest Repeating Character Replacement teaches us how to use a sliding window approach to solve substring problems by maximizing the length through character replacements.

