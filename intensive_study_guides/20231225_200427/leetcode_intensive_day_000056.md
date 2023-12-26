
# Leetcode Intensive Tutorial Day 56 
> [Difficulty Score: 25]

> [Version: 20231225_200427]

## Courses overview of the day

- 14 Longest Common Prefix [Easy]
  - 6 ZigZag Conversion [Medium]
    - 72 Edit Distance [Hard]
      - 300 Longest Increasing Subsequence [Medium]
        - 91 Decode Ways [Medium]
        - 307 Range Sum Query - Mutable [Medium]
          - 308 Range Sum Query 2D - Mutable [Hard]
    - 189 Rotate Array [Medium]
      - 153 Find Minimum in Rotated Sorted Array [Medium]
        - 154 Find Minimum in Rotated Sorted Array II [Hard]

#### Steps by steps

 - [1. From 14 Longest Common Prefix [Easy] to 6 ZigZag Conversion [Medium]](#1-from-14-longest-common-prefix-easy-to-6-zigzag-conversion-medium)

 - [2. From 6 ZigZag Conversion [Medium] to 72 Edit Distance [Hard]](#2-from-6-zigzag-conversion-medium-to-72-edit-distance-hard)

 - [3. From 72 Edit Distance [Hard] to 300 Longest Increasing Subsequence [Medium]](#3-from-72-edit-distance-hard-to-300-longest-increasing-subsequence-medium)

 - [4. From 300 Longest Increasing Subsequence [Medium] to 91 Decode Ways [Medium]](#4-from-300-longest-increasing-subsequence-medium-to-91-decode-ways-medium)

 - [5. From 300 Longest Increasing Subsequence [Medium] to 307 Range Sum Query - Mutable [Medium]](#5-from-300-longest-increasing-subsequence-medium-to-307-range-sum-query---mutable-medium)

 - [6. From 307 Range Sum Query - Mutable [Medium] to 308 Range Sum Query 2D - Mutable [Hard]](#6-from-307-range-sum-query---mutable-medium-to-308-range-sum-query-2d---mutable-hard)

 - [7. From 6 ZigZag Conversion [Medium] to 189 Rotate Array [Medium]](#7-from-6-zigzag-conversion-medium-to-189-rotate-array-medium)

 - [8. From 189 Rotate Array [Medium] to 153 Find Minimum in Rotated Sorted Array [Medium]](#8-from-189-rotate-array-medium-to-153-find-minimum-in-rotated-sorted-array-medium)

 - [9. From 153 Find Minimum in Rotated Sorted Array [Medium] to 154 Find Minimum in Rotated Sorted Array II [Hard]](#9-from-153-find-minimum-in-rotated-sorted-array-medium-to-154-find-minimum-in-rotated-sorted-array-ii-hard)

#### Summary


- 189 Rotate Array : Rotate an array to the right by k steps.
- 91 Decode Ways : The essence of this problem is to count the number of ways to decode a given string using a mapping from letters to numbers.
- 154 Find Minimum in Rotated Sorted Array II : The minimum element is the only element in the array that is smaller than its previous element. The array may contain duplicates.
- 72 Edit Distance : Given two strings, find the minimum number of operations required to convert one string to another.
- 153 Find Minimum in Rotated Sorted Array : The minimum element is the only element in the array that is smaller than its previous element.
- 307 Range Sum Query - Mutable : The essence of this problem is to efficiently calculate the sum of subarrays using a segment tree.
- 300 Longest Increasing Subsequence : Find the length of the longest increasing subsequence in an array.
- 6 ZigZag Conversion : The essence of the problem is to convert a string into a zigzag pattern with a given number of rows.
- 14 Longest Common Prefix : The essence of this problem is to find the longest common prefix string among an array of strings by iteratively updating the prefix and checking if it is a prefix of each string.
- 308 Range Sum Query 2D - Mutable : The essence of this problem is to efficiently calculate the sum of submatrices using a segment tree.
> Similarity Diameter of these problems: 0.8990


---
# 1. From 14 Longest Common Prefix [Easy] to 6 ZigZag Conversion [Medium]
> Similarity Distance: 0.6577

### >> 14 Longest Common Prefix [Easy]
Write a function to find the longest common prefix string amongst an array of strings.
##### Sample input:
["flower","flow","flight"]
##### Sample output:
"fl"

##### Questions to ask to clarify requirements:
What should be returned if the array is empty? Can the array contain empty strings?

##### Optimal Python solution:
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""
        prefix = strs[0]
        for i in range(1, len(strs)):
            while strs[i].find(prefix) != 0:
                prefix = prefix[:-1]
                if not prefix:
                    return ""
        return prefix
```
##### Time complexity:
O(n*m)
##### Space complexity:
O(1)
##### Notes:
1. Initialize the prefix as the first string in the array.
2. Iterate through the remaining strings and update the prefix by removing characters from the end until it is a prefix of the current string.
3. If the prefix becomes empty, return an empty string.
4. Return the final prefix.
1. Start with the first string as the prefix.
2. Use a while loop to update the prefix by removing characters from the end.
3. Test the solution with different inputs to ensure correctness.
1. Handling the case where the array is empty or contains empty strings.
2. Updating the prefix by removing characters from the end until it is a prefix of the current string.
1. Comparing each character of the strings one by one.
2. Using nested loops to find the common prefix.
    
### >> 6 ZigZag Conversion [Medium]
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows.
##### Sample input:
"PAYPALISHIRING",
3
##### Sample output:
"PAHNAPLSIIGYIR"

##### Questions to ask to clarify requirements:
What should be returned if the input string is empty?

##### Optimal Python solution:
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1 or numRows >= len(s):
            return s
        res = [''] * numRows
        index, step = 0, 1
        for char in s:
            res[index] += char
            if index == 0:
                step = 1
            elif index == numRows - 1:
                step = -1
            index += step
        return ''.join(res)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use an array of strings to store the characters in each row.
2. Iterate through the input string and assign each character to the corresponding row.
3. Handle the zigzag pattern by changing the direction of iteration.
1. Use an array to store intermediate results.
2. Handle special cases separately.
1. Handle the case when the number of rows is 1 or greater than the length of the string.
2. Handle the zigzag pattern by changing the direction of iteration.
1. Avoid using a 2D array to store the characters in each row.
2. Avoid unnecessary calculations.
    
### >> Comparison: 14 Longest Common Prefix [Easy] *VS* 6 ZigZag Conversion [Medium]
> Similarity distance: 0.6577
##### Similarities

- Both questions involve manipulating strings.
- Both questions require finding patterns in the input strings.
##### Differences

- Longest Common Prefix is an Easy level question, while ZigZag Conversion is a Medium level question.
- Longest Common Prefix requires finding the longest common prefix among a set of strings, while ZigZag Conversion involves converting a string into a zigzag pattern.
- Longest Common Prefix has a linear time complexity solution, while ZigZag Conversion has a time complexity of O(n).
##### New Insights in 6 ZigZag Conversion [Medium]

- From Longest Common Prefix, we can learn how to efficiently compare characters in multiple strings.
- From ZigZag Conversion, we can learn how to manipulate strings to create a specific pattern.


---
# 2. From 6 ZigZag Conversion [Medium] to 72 Edit Distance [Hard]
> Similarity Distance: 0.6026

### >> Reminder: 6 ZigZag Conversion [Medium]
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows.
##### Optimal Python solution:
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1 or numRows >= len(s):
            return s
        res = [''] * numRows
        index, step = 0, 1
        for char in s:
            res[index] += char
            if index == 0:
                step = 1
            elif index == numRows - 1:
                step = -1
            index += step
        return ''.join(res)
```
The essence of the problem is to convert a string into a zigzag pattern with a given number of rows.
    
### >> 72 Edit Distance [Hard]
Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.
##### Sample input:
word1 = "horse", word2 = "ros"
##### Sample output:
3

##### Questions to ask to clarify requirements:
What are the possible operations allowed to convert one word to another? Can the operations be performed in any order?

##### Optimal Python solution:
```python
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
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
                    dp[i][j] = min(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1
        return dp[m][n]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Create a 2D array dp of size (m+1) x (n+1), where m and n are the lengths of word1 and word2.
3. Initialize the first row and column of dp with the respective indices.
4. Iterate over the remaining cells of dp and update them based on the characters of word1 and word2.
5. The value in the bottom-right cell of dp will be the minimum number of operations required to convert word1 to word2.
1. Use dynamic programming to solve the problem.
2. Initialize the first row and column of the dp array.
3. Iterate over the remaining cells and update them based on the characters of the words.
4. Return the value in the bottom-right cell of the dp array.
None
Using recursion without memoization.
    
### >> Comparison: 6 ZigZag Conversion [Medium] *VS* 72 Edit Distance [Hard]
> Similarity distance: 0.6026
##### Similarities

- Both questions involve manipulating strings.
- Both questions require finding a pattern or sequence in the input.
- Both questions have a dynamic programming solution approach.
##### Differences

- ZigZag Conversion involves converting a string into a zigzag pattern, while Edit Distance involves finding the minimum number of operations to transform one string into another.
- ZigZag Conversion has a medium difficulty level, while Edit Distance has a hard difficulty level.
- ZigZag Conversion has a linear time complexity, while Edit Distance has a quadratic time complexity.
##### New Insights in 72 Edit Distance [Hard]

- ZigZag Conversion: The zigzag pattern can be formed by iterating through the input string and placing each character in the appropriate row of the zigzag pattern.
- Edit Distance: The minimum number of operations required to transform one string into another can be calculated using a dynamic programming approach.


---
# 3. From 72 Edit Distance [Hard] to 300 Longest Increasing Subsequence [Medium]
> Similarity Distance: 0.6115

### >> Reminder: 72 Edit Distance [Hard]
Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.
##### Optimal Python solution:
```python
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
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
                    dp[i][j] = min(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1
        return dp[m][n]
```
Given two strings, find the minimum number of operations required to convert one string to another.
    
### >> 300 Longest Increasing Subsequence [Medium]
Given an integer array nums, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].
##### Sample input:
[10,9,2,5,3,7,101,18]
##### Sample output:
4

##### Questions to ask to clarify requirements:
Can the array contain negative numbers? Can the array be empty?

##### Optimal Python solution:
```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1] * len(nums)
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j] + 1)
        return max(dp)
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
Use dynamic programming to solve the problem.
Initialize a dp array with all elements set to 1.
Iterate through the array and update the dp array based on the previous elements.
The maximum value in the dp array is the length of the longest increasing subsequence.
Use dynamic programming to solve the problem.
Initialize a dp array with all elements set to 1.
Iterate through the array and update the dp array based on the previous elements.
Handle the case when the array is empty or contains negative numbers.
None
None
    
### >> Comparison: 72 Edit Distance [Hard] *VS* 300 Longest Increasing Subsequence [Medium]
> Similarity distance: 0.6115
##### Similarities

- Both questions involve finding the minimum number of operations to transform one string into another.
- Both questions require dynamic programming to solve efficiently.
##### Differences

- 72 Edit Distance focuses on transforming one string into another by performing insertions, deletions, and substitutions.
- 300 Longest Increasing Subsequence focuses on finding the length of the longest subsequence in an array that is in increasing order.
##### New Insights in 300 Longest Increasing Subsequence [Medium]

- From 72 Edit Distance, we can learn how to use dynamic programming to solve string transformation problems efficiently.
- From 300 Longest Increasing Subsequence, we can learn how to find the longest increasing subsequence in an array using dynamic programming.


---
# 4. From 300 Longest Increasing Subsequence [Medium] to 91 Decode Ways [Medium]
> Similarity Distance: 0.6160

### >> Reminder: 300 Longest Increasing Subsequence [Medium]
Given an integer array nums, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].
##### Optimal Python solution:
```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1] * len(nums)
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j] + 1)
        return max(dp)
```
Find the length of the longest increasing subsequence in an array.
    
### >> 91 Decode Ways [Medium]
A message containing letters from A-Z is being encoded to numbers using the following mapping: 'A' -> 1, 'B' -> 2, ..., 'Z' -> 26. Given a non-empty string containing only digits, determine the total number of ways to decode it.
##### Sample input:
12
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the maximum length of the input string? Can the input string contain leading zeros?

##### Optimal Python solution:
```python
def numDecodings(s):
    if not s or s[0] == '0':
        return 0
    dp = [0] * (len(s) + 1)
    dp[0] = 1
    dp[1] = 1
    for i in range(2, len(s) + 1):
        if 1 <= int(s[i-1:i]) <= 9:
            dp[i] += dp[i-1]
        if 10 <= int(s[i-2:i]) <= 26:
            dp[i] += dp[i-2]
    return dp[-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Initialize a dp array to store the number of ways to decode the string up to the current index.
3. Iterate through the string and update the dp array based on the current and previous characters.
4. Return the last element of the dp array as the result.
1. Handle edge cases such as an empty string or a string that cannot be decoded.
2. Use a bottom-up approach to solve the problem using dynamic programming.
3. Optimize the space complexity of the solution by using only two variables instead of an array.
1. Handling leading zeros in the input string.
2. Handling invalid characters in the input string.
1. Using recursion to solve the problem.
2. Using a brute force approach to check all possible combinations.
    
### >> Comparison: 300 Longest Increasing Subsequence [Medium] *VS* 91 Decode Ways [Medium]
> Similarity distance: 0.6160
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve string manipulation.
- Both questions require dynamic programming to solve.
- Both questions have multiple possible solutions.
##### Differences

- 300 Longest Increasing Subsequence deals with finding the length of the longest increasing subsequence in an array.
- 91 Decode Ways deals with decoding a string of numbers into possible letter combinations.
- 300 Longest Increasing Subsequence has a time complexity of O(n^2) for the dynamic programming solution.
- 91 Decode Ways has a time complexity of O(n) for the dynamic programming solution.
##### New Insights in 91 Decode Ways [Medium]

- From 300 Longest Increasing Subsequence, we can learn how to use dynamic programming to solve problems related to finding subsequences.
- From 91 Decode Ways, we can learn how to use dynamic programming to solve problems related to decoding strings.


---
# 5. From 300 Longest Increasing Subsequence [Medium] to 307 Range Sum Query - Mutable [Medium]
> Similarity Distance: 0.7468

### >> Reminder: 300 Longest Increasing Subsequence [Medium]
Given an integer array nums, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].
##### Optimal Python solution:
```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1] * len(nums)
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j] + 1)
        return max(dp)
```
Find the length of the longest increasing subsequence in an array.
    
### >> 307 Range Sum Query - Mutable [Medium]
Implement the NumArray class:

- NumArray(int[] nums) Initializes the object with the integer array nums.
- void update(int index, int val) Updates the value of nums[index] to be val.
- int sumRange(int left, int right) Returns the sum of the subarray nums[left, right] (i.e., nums[left] + nums[left + 1], ..., nums[right]).
##### Sample input:
["NumArray", "sumRange", "update", "sumRange"]
[[[1, 3, 5]], [0, 2], [1, 2], [0, 2]]
##### Sample output:
[null, 9, null, 8]

##### Questions to ask to clarify requirements:
What is the maximum size of the input array? Can the array contain negative numbers? Can the update operation modify the array size?

##### Optimal Python solution:
```python
class NumArray:

    def __init__(self, nums: List[int]):
        self.n = len(nums)
        self.tree = [0] * (2 * self.n)
        self.buildTree(nums)

    def buildTree(self, nums):
        for i in range(self.n, 2 * self.n):
            self.tree[i] = nums[i - self.n]
        for i in range(self.n - 1, 0, -1):
            self.tree[i] = self.tree[i * 2] + self.tree[i * 2 + 1]

    def update(self, index: int, val: int) -> None:
        index += self.n
        self.tree[index] = val
        while index > 0:
            left = right = index
            if index % 2 == 0:
                right = index + 1
            else:
                left = index - 1
            self.tree[index // 2] = self.tree[left] + self.tree[right]
            index //= 2

    def sumRange(self, left: int, right: int) -> int:
        left += self.n
        right += self.n
        res = 0
        while left <= right:
            if left % 2 == 1:
                res += self.tree[left]
                left += 1
            if right % 2 == 0:
                res += self.tree[right]
                right -= 1
            left //= 2
            right //= 2
        return res
```
##### Time complexity:
O(log n) for update and sumRange operations
##### Space complexity:
O(n) for the segment tree
##### Notes:
1. Use a segment tree to store the sum of subarrays.
2. Build the segment tree in the constructor.
3. Update the tree when an element is modified.
4. Calculate the sum of a range using the segment tree.
Understand the concept of segment trees and how they can be used to efficiently perform range queries on an array.
Understanding the indexing of the segment tree can be tricky.
Avoid using a brute force approach to calculate the sum of a range.
    
### >> Comparison: 300 Longest Increasing Subsequence [Medium] *VS* 307 Range Sum Query - Mutable [Medium]
> Similarity distance: 0.7468
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating arrays.
- Both questions require finding a specific subsequence or range of elements.
- Both questions involve dynamic programming techniques.
##### Differences

- 300 Longest Increasing Subsequence focuses on finding the length of the longest increasing subsequence in an array.
- 307 Range Sum Query - Mutable focuses on performing range sum queries and updating values in an array.
- 300 Longest Increasing Subsequence uses a dynamic programming approach with a time complexity of O(n^2).
- 307 Range Sum Query - Mutable uses a segment tree data structure with a time complexity of O(log n) for both query and update operations.
##### New Insights in 307 Range Sum Query - Mutable [Medium]

- From 300 Longest Increasing Subsequence, we can learn how to use dynamic programming to solve problems related to finding subsequences.
- From 307 Range Sum Query - Mutable, we can learn how to use a segment tree data structure to efficiently perform range sum queries and updates.


---
# 6. From 307 Range Sum Query - Mutable [Medium] to 308 Range Sum Query 2D - Mutable [Hard]
> Similarity Distance: 0.4838

### >> Reminder: 307 Range Sum Query - Mutable [Medium]
Implement the NumArray class:

- NumArray(int[] nums) Initializes the object with the integer array nums.
- void update(int index, int val) Updates the value of nums[index] to be val.
- int sumRange(int left, int right) Returns the sum of the subarray nums[left, right] (i.e., nums[left] + nums[left + 1], ..., nums[right]).
##### Optimal Python solution:
```python
class NumArray:

    def __init__(self, nums: List[int]):
        self.n = len(nums)
        self.tree = [0] * (2 * self.n)
        self.buildTree(nums)

    def buildTree(self, nums):
        for i in range(self.n, 2 * self.n):
            self.tree[i] = nums[i - self.n]
        for i in range(self.n - 1, 0, -1):
            self.tree[i] = self.tree[i * 2] + self.tree[i * 2 + 1]

    def update(self, index: int, val: int) -> None:
        index += self.n
        self.tree[index] = val
        while index > 0:
            left = right = index
            if index % 2 == 0:
                right = index + 1
            else:
                left = index - 1
            self.tree[index // 2] = self.tree[left] + self.tree[right]
            index //= 2

    def sumRange(self, left: int, right: int) -> int:
        left += self.n
        right += self.n
        res = 0
        while left <= right:
            if left % 2 == 1:
                res += self.tree[left]
                left += 1
            if right % 2 == 0:
                res += self.tree[right]
                right -= 1
            left //= 2
            right //= 2
        return res
```
The essence of this problem is to efficiently calculate the sum of subarrays using a segment tree.
    
### >> 308 Range Sum Query 2D - Mutable [Hard]
Implement the NumMatrix class:

- NumMatrix(int[][] matrix) Initializes the object with the integer matrix matrix.
- void update(int row, int col, int val) Updates the value of matrix[row][col] to be val.
- int sumRegion(int row1, int col1, int row2, int col2) Returns the sum of the submatrix matrix[row1, col1, row2, col2] (i.e., matrix[row1][col1] + matrix[row1][col1 + 1] + ... + matrix[row2][col2]).
##### Sample input:
["NumMatrix", "sumRegion", "update", "sumRegion"]
[[[[3, 0, 1, 4, 2],
   [5, 6, 3, 2, 1],
   [1, 2, 0, 1, 5],
   [4, 1, 0, 1, 7],
   [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [3, 2, 2], [2, 1, 4, 3]]
##### Sample output:
[null, 8, null, 11]

##### Questions to ask to clarify requirements:
What is the maximum size of the input matrix? Can the matrix contain negative numbers? Can the update operation modify the matrix size?

##### Optimal Python solution:
```python
class NumMatrix:

    def __init__(self, matrix: List[List[int]]):
        if not matrix or not matrix[0]:
            return
        self.m, self.n = len(matrix), len(matrix[0])
        self.tree = [[0] * (self.n + 1) for _ in range(self.m + 1)]
        self.nums = [[0] * self.n for _ in range(self.m)]
        for i in range(self.m):
            for j in range(self.n):
                self.update(i, j, matrix[i][j])

    def update(self, row: int, col: int, val: int) -> None:
        delta = val - self.nums[row][col]
        self.nums[row][col] = val
        i = row + 1
        while i <= self.m:
            j = col + 1
            while j <= self.n:
                self.tree[i][j] += delta
                j += j & -j
            i += i & -i

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        return self.sum(row2 + 1, col2 + 1) - self.sum(row2 + 1, col1) - self.sum(row1, col2 + 1) + self.sum(row1, col1)

    def sum(self, row: int, col: int) -> int:
        res = 0
        i = row
        while i > 0:
            j = col
            while j > 0:
                res += self.tree[i][j]
                j -= j & -j
            i -= i & -i
        return res
```
##### Time complexity:
O(log m * log n) for update and sumRegion operations
##### Space complexity:
O(m * n) for the segment tree
##### Notes:
1. Use a segment tree to store the sum of submatrices.
2. Build the segment tree in the constructor.
3. Update the tree when an element is modified.
4. Calculate the sum of a submatrix using the segment tree.
Understand the concept of segment trees and how they can be used to efficiently perform range queries on a 2D array.
Understanding the indexing of the segment tree can be tricky.
Avoid using a brute force approach to calculate the sum of a submatrix.
    
### >> Comparison: 307 Range Sum Query - Mutable [Medium] *VS* 308 Range Sum Query 2D - Mutable [Hard]
> Similarity distance: 0.4838
##### Similarities

- Both questions involve performing range sum queries on a mutable array or matrix.
- Both questions require implementing a data structure to efficiently update and query the range sums.
##### Differences

- 307 Range Sum Query - Mutable is a 1-dimensional problem, while 308 Range Sum Query 2D - Mutable is a 2-dimensional problem.
- 307 Range Sum Query - Mutable uses an array as the underlying data structure, while 308 Range Sum Query 2D - Mutable uses a matrix.
- 307 Range Sum Query - Mutable supports updating individual elements, while 308 Range Sum Query 2D - Mutable supports updating individual cells in the matrix.
- 307 Range Sum Query - Mutable uses a binary indexed tree (BIT) as the data structure, while 308 Range Sum Query 2D - Mutable uses a 2-dimensional binary indexed tree (2D BIT).
##### New Insights in 308 Range Sum Query 2D - Mutable [Hard]

- 307 Range Sum Query - Mutable introduces the concept of a binary indexed tree (BIT) for efficient range sum queries in a 1-dimensional array.
- 308 Range Sum Query 2D - Mutable extends the concept of a binary indexed tree (BIT) to efficiently handle range sum queries in a 2-dimensional matrix.


---
# 7. From 6 ZigZag Conversion [Medium] to 189 Rotate Array [Medium]
> Similarity Distance: 0.6838

### >> Reminder: 6 ZigZag Conversion [Medium]
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows.
##### Optimal Python solution:
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1 or numRows >= len(s):
            return s
        res = [''] * numRows
        index, step = 0, 1
        for char in s:
            res[index] += char
            if index == 0:
                step = 1
            elif index == numRows - 1:
                step = -1
            index += step
        return ''.join(res)
```
The essence of the problem is to convert a string into a zigzag pattern with a given number of rows.
    
### >> 189 Rotate Array [Medium]
Given an array, rotate the array to the right by k steps, where k is non-negative.
##### Sample input:
[1,2,3,4,5,6,7], 3
##### Sample output:
[5,6,7,1,2,3,4]

##### Questions to ask to clarify requirements:
What should be the behavior if k is greater than the length of the array?

##### Optimal Python solution:
```python
def rotate(nums, k):
    k = k % len(nums)
    nums[:] = nums[-k:] + nums[:-k]
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use modulo operator to handle cases where k is greater than the length of the array.
Use the modulo operator to handle cases where k is greater than the length of the array.
Handling cases where k is greater than the length of the array.
Using extra space.
    
### >> Comparison: 6 ZigZag Conversion [Medium] *VS* 189 Rotate Array [Medium]
> Similarity distance: 0.6838
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating arrays or strings.
- Both questions require some form of pattern manipulation.
##### Differences

- ZigZag Conversion involves converting a string into a zigzag pattern, while Rotate Array involves rotating the elements of an array.
- ZigZag Conversion requires rearranging the characters of a string based on a specific pattern, while Rotate Array requires shifting the elements of an array by a given number of positions.
- ZigZag Conversion has a time complexity of O(n), while Rotate Array has a time complexity of O(k), where n is the length of the string and k is the number of positions to rotate.
##### New Insights in 189 Rotate Array [Medium]

- ZigZag Conversion teaches us how to manipulate strings to create a specific pattern.
- Rotate Array teaches us how to efficiently rotate the elements of an array without using extra space.


---
# 8. From 189 Rotate Array [Medium] to 153 Find Minimum in Rotated Sorted Array [Medium]
> Similarity Distance: 0.4958

### >> Reminder: 189 Rotate Array [Medium]
Given an array, rotate the array to the right by k steps, where k is non-negative.
##### Optimal Python solution:
```python
def rotate(nums, k):
    k = k % len(nums)
    nums[:] = nums[-k:] + nums[:-k]
```
Rotate an array to the right by k steps.
    
### >> 153 Find Minimum in Rotated Sorted Array [Medium]
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. Find the minimum element in the array.
##### Sample input:
[4,5,6,7,0,1,2]
##### Sample output:
0

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def findMin(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
The minimum element is the only element in the array that is smaller than its previous element.
None
None
None
    
### >> Comparison: 189 Rotate Array [Medium] *VS* 153 Find Minimum in Rotated Sorted Array [Medium]
> Similarity distance: 0.4958
##### Similarities

- Both questions involve rotating an array
- Both questions have a time complexity of O(n)
##### Differences

- 189 Rotate Array rotates the entire array by a given number of steps
- 153 Find Minimum in Rotated Sorted Array finds the minimum element in a rotated sorted array
##### New Insights in 153 Find Minimum in Rotated Sorted Array [Medium]

- 189 Rotate Array can be solved using reverse technique
- 153 Find Minimum in Rotated Sorted Array can be solved using binary search


---
# 9. From 153 Find Minimum in Rotated Sorted Array [Medium] to 154 Find Minimum in Rotated Sorted Array II [Hard]
> Similarity Distance: 0.2266

### >> Reminder: 153 Find Minimum in Rotated Sorted Array [Medium]
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. Find the minimum element in the array.
##### Optimal Python solution:
```python
def findMin(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]
```
The minimum element is the only element in the array that is smaller than its previous element.
    
### >> 154 Find Minimum in Rotated Sorted Array II [Hard]
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. Find the minimum element in the array. The array may contain duplicates.
##### Sample input:
[2,2,2,0,1]
##### Sample output:
0

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def findMin(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        elif nums[mid] < nums[right]:
            right = mid
        else:
            right -= 1
    return nums[left]
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
The minimum element is the only element in the array that is smaller than its previous element. The array may contain duplicates.
None
None
None
    
### >> Comparison: 153 Find Minimum in Rotated Sorted Array [Medium] *VS* 154 Find Minimum in Rotated Sorted Array II [Hard]
> Similarity distance: 0.2266
##### Similarities

- Both questions are about finding the minimum element in a rotated sorted array.
- Both questions have a time complexity requirement of O(log n).
##### Differences

- Question 153 assumes that there are no duplicate elements in the array, while question 154 allows for duplicate elements.
- Question 153 guarantees that the minimum element exists in the array, while question 154 does not have this guarantee.
- Question 153 can be solved using a modified binary search algorithm, while question 154 requires a more complex approach.
- Question 153 has a space complexity of O(1), while question 154 has a space complexity of O(n).
##### New Insights in 154 Find Minimum in Rotated Sorted Array II [Hard]

- Question 154 introduces the concept of duplicate elements in a rotated sorted array and requires handling this scenario.
- Question 154 demonstrates the importance of carefully considering edge cases and handling them appropriately.

