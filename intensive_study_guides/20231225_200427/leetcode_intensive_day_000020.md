
# Leetcode Intensive Tutorial Day 20 
> [Difficulty Score: 16]

> [Version: 20231225_200427]

## Courses overview of the day

- 376 Wiggle Subsequence [Medium]
  - 562 Longest Line of Consecutive One in Matrix [Medium]
    - 487 Max Consecutive Ones II [Medium]
    - 368 Largest Divisible Subset [Medium]
      - 474 Ones and Zeroes [Medium]
      - 279 Perfect Squares [Medium]
        - 416 Partition Equal Subset Sum [Medium]
          - 494 Target Sum [Medium]

#### Steps by steps

 - [1. From 376 Wiggle Subsequence [Medium] to 562 Longest Line of Consecutive One in Matrix [Medium]](#1-from-376-wiggle-subsequence-medium-to-562-longest-line-of-consecutive-one-in-matrix-medium)

 - [2. From 562 Longest Line of Consecutive One in Matrix [Medium] to 487 Max Consecutive Ones II [Medium]](#2-from-562-longest-line-of-consecutive-one-in-matrix-medium-to-487-max-consecutive-ones-ii-medium)

 - [3. From 562 Longest Line of Consecutive One in Matrix [Medium] to 368 Largest Divisible Subset [Medium]](#3-from-562-longest-line-of-consecutive-one-in-matrix-medium-to-368-largest-divisible-subset-medium)

 - [4. From 368 Largest Divisible Subset [Medium] to 474 Ones and Zeroes [Medium]](#4-from-368-largest-divisible-subset-medium-to-474-ones-and-zeroes-medium)

 - [5. From 368 Largest Divisible Subset [Medium] to 279 Perfect Squares [Medium]](#5-from-368-largest-divisible-subset-medium-to-279-perfect-squares-medium)

 - [6. From 279 Perfect Squares [Medium] to 416 Partition Equal Subset Sum [Medium]](#6-from-279-perfect-squares-medium-to-416-partition-equal-subset-sum-medium)

 - [7. From 416 Partition Equal Subset Sum [Medium] to 494 Target Sum [Medium]](#7-from-416-partition-equal-subset-sum-medium-to-494-target-sum-medium)

#### Summary


- 376 Wiggle Subsequence : The essence of the problem is to find the length of the longest wiggle subsequence.
- 368 Largest Divisible Subset : Dynamic programming is used to find the largest divisible subset.
- 416 Partition Equal Subset Sum : Use dynamic programming to solve the subset sum problem.
- 487 Max Consecutive Ones II : Find the maximum number of consecutive 1s in a binary array by flipping at most one zero.
- 562 Longest Line of Consecutive One in Matrix : The essence of this problem is to find the longest line of consecutive ones in a matrix by using dynamic programming.
- 474 Ones and Zeroes : The essence of this problem is to find the maximum subset size of binary strings with at most m 0's and n 1's.
- 279 Perfect Squares : The essence of this problem is to find the least number of perfect square numbers that sum to a given number.
- 494 Target Sum : Using dynamic programming to count the number of ways to reach the target sum in an array
> Similarity Diameter of these problems: 0.6316


---
# 1. From 376 Wiggle Subsequence [Medium] to 562 Longest Line of Consecutive One in Matrix [Medium]
> Similarity Distance: 0.4723

### >> 376 Wiggle Subsequence [Medium]
A sequence of numbers is called a wiggle sequence if the differences between successive numbers strictly alternate between positive and negative. The first difference (if one exists) may be either positive or negative. A sequence with fewer than two elements is trivially a wiggle sequence.

For example, [1,7,4,9,2,5] is a wiggle sequence because the differences (6,-3,5,-7,3) are alternately positive and negative.

Given a sequence of integers, return the length of the longest subsequence that is a wiggle sequence. A subsequence is obtained by deleting some number of elements (eventually, also zero) from the original sequence, leaving the remaining elements in their original order.
##### Sample input:
[1,7,4,9,2,5]

Output: 6

Explanation: 

The entire sequence is a wiggle sequence.

[1,7,4,9,2,5] -> [1,4,2,5] -> [1,2,5] -> [1,5] -> [1].

Therefore, the length of the longest subsequence is 6.
##### Sample output:
6

##### Questions to ask to clarify requirements:
Can the sequence contain duplicate numbers?

##### Optimal Python solution:
```python
class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        if len(nums) < 2:
            return len(nums)
        up = down = 1
        for i in range(1, len(nums)):
            if nums[i] > nums[i - 1]:
                up = down + 1
            elif nums[i] < nums[i - 1]:
                down = up + 1
        return max(up, down)
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Maintain two variables to track the length of the longest wiggle subsequence ending in an up or down position.
3. Update the variables based on the current number and the previous number.
4. Return the maximum of the two variables.
Try to find the optimal strategy for the problem.
The length of the longest wiggle subsequence ending in an up or down position can be updated based on the current number and the previous number.
Avoid brute force approach.
    
### >> 562 Longest Line of Consecutive One in Matrix [Medium]
Given a 01 matrix M, find the longest line of consecutive one in the matrix. The line could be horizontal, vertical, diagonal or anti-diagonal.
##### Sample input:
[[0,1,1,0],[0,1,1,0],[0,0,0,1]]
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the maximum size of the matrix? Can the matrix be empty?

##### Optimal Python solution:
```python
def longestLine(M):
    if not M:
        return 0
    m, n = len(M), len(M[0])
    dp = [[[0, 0, 0, 0] for _ in range(n)] for _ in range(m)]
    max_len = 0
    for i in range(m):
        for j in range(n):
            if M[i][j] == 1:
                dp[i][j][0] = dp[i][j-1][0] + 1 if j > 0 else 1
                dp[i][j][1] = dp[i-1][j][1] + 1 if i > 0 else 1
                dp[i][j][2] = dp[i-1][j-1][2] + 1 if i > 0 and j > 0 else 1
                dp[i][j][3] = dp[i-1][j+1][3] + 1 if i > 0 and j < n-1 else 1
                max_len = max(max_len, max(dp[i][j]))
    return max_len
```
##### Time complexity:
O(m*n)
##### Space complexity:
O(m*n)
##### Notes:
Use dynamic programming to keep track of the longest line of consecutive ones in each direction.
Break down the problem into subproblems and use dynamic programming to solve them.
None
None
    
### >> Comparison: 376 Wiggle Subsequence [Medium] *VS* 562 Longest Line of Consecutive One in Matrix [Medium]
> Similarity distance: 0.4723
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding a subsequence or a line of consecutive ones.
- Both questions require iterating through a matrix or an array.
- Both questions involve making decisions based on certain conditions.
##### Differences

- 376 Wiggle Subsequence focuses on finding a subsequence that alternates between increasing and decreasing elements.
- 562 Longest Line of Consecutive One in Matrix focuses on finding the longest line of consecutive ones in a matrix.
- 376 Wiggle Subsequence requires finding the length of the subsequence.
- 562 Longest Line of Consecutive One in Matrix requires finding the number of consecutive ones in the longest line.
- 376 Wiggle Subsequence can have elements with the same value in the subsequence.
- 562 Longest Line of Consecutive One in Matrix only considers horizontal, vertical, diagonal, and anti-diagonal lines.
##### New Insights in 562 Longest Line of Consecutive One in Matrix [Medium]

- In 376 Wiggle Subsequence, we can use dynamic programming to solve the problem efficiently.
- In 562 Longest Line of Consecutive One in Matrix, we can use a combination of depth-first search and dynamic programming to find the longest line.


---
# 2. From 562 Longest Line of Consecutive One in Matrix [Medium] to 487 Max Consecutive Ones II [Medium]
> Similarity Distance: 0.4068

### >> Reminder: 562 Longest Line of Consecutive One in Matrix [Medium]
Given a 01 matrix M, find the longest line of consecutive one in the matrix. The line could be horizontal, vertical, diagonal or anti-diagonal.
##### Optimal Python solution:
```python
def longestLine(M):
    if not M:
        return 0
    m, n = len(M), len(M[0])
    dp = [[[0, 0, 0, 0] for _ in range(n)] for _ in range(m)]
    max_len = 0
    for i in range(m):
        for j in range(n):
            if M[i][j] == 1:
                dp[i][j][0] = dp[i][j-1][0] + 1 if j > 0 else 1
                dp[i][j][1] = dp[i-1][j][1] + 1 if i > 0 else 1
                dp[i][j][2] = dp[i-1][j-1][2] + 1 if i > 0 and j > 0 else 1
                dp[i][j][3] = dp[i-1][j+1][3] + 1 if i > 0 and j < n-1 else 1
                max_len = max(max_len, max(dp[i][j]))
    return max_len
```
The essence of this problem is to find the longest line of consecutive ones in a matrix by using dynamic programming.
    
### >> 487 Max Consecutive Ones II [Medium]
Given a binary array, find the maximum number of consecutive 1s in this array if you can flip at most one 0.
##### Sample input:
[1,0,1,1,0]
##### Sample output:
4

##### Questions to ask to clarify requirements:
Can we assume the input array will always contain at least one 0?

##### Optimal Python solution:
```python
def findMaxConsecutiveOnes(nums):
    max_count = 0
    count = 0
    prev_count = 0
    for num in nums:
        if num == 1:
            count += 1
            prev_count += 1
        else:
            prev_count = count + 1
            count = 0
        max_count = max(max_count, count, prev_count)
    return max_count
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use two counters to keep track of the current count and the previous count.
2. Update the previous count when encountering a zero.
3. Update the maximum count with the current count, previous count, and the count after flipping a zero.
4. Return the maximum count.
Keep track of the current count and the previous count to handle the case when the input array contains only 1s.
Handling the case when the input array contains only 1s.
Using extra space.
    
### >> Comparison: 562 Longest Line of Consecutive One in Matrix [Medium] *VS* 487 Max Consecutive Ones II [Medium]
> Similarity distance: 0.4068
##### Similarities

- Both questions involve finding the longest line of consecutive ones in a matrix.
- Both questions have a medium difficulty level.
##### Differences

- 562 Longest Line of Consecutive One in Matrix only considers horizontal, vertical, and diagonal lines, while 487 Max Consecutive Ones II considers flipping at most one 0 to 1.
- 562 Longest Line of Consecutive One in Matrix returns the length of the longest line, while 487 Max Consecutive Ones II returns the number of ones in the longest line.
##### New Insights in 487 Max Consecutive Ones II [Medium]

- 562 Longest Line of Consecutive One in Matrix can be solved using dynamic programming to keep track of the longest line length at each cell.
- 487 Max Consecutive Ones II can be solved using a sliding window approach to find the longest line length.


---
# 3. From 562 Longest Line of Consecutive One in Matrix [Medium] to 368 Largest Divisible Subset [Medium]
> Similarity Distance: 0.4735

### >> Reminder: 562 Longest Line of Consecutive One in Matrix [Medium]
Given a 01 matrix M, find the longest line of consecutive one in the matrix. The line could be horizontal, vertical, diagonal or anti-diagonal.
##### Optimal Python solution:
```python
def longestLine(M):
    if not M:
        return 0
    m, n = len(M), len(M[0])
    dp = [[[0, 0, 0, 0] for _ in range(n)] for _ in range(m)]
    max_len = 0
    for i in range(m):
        for j in range(n):
            if M[i][j] == 1:
                dp[i][j][0] = dp[i][j-1][0] + 1 if j > 0 else 1
                dp[i][j][1] = dp[i-1][j][1] + 1 if i > 0 else 1
                dp[i][j][2] = dp[i-1][j-1][2] + 1 if i > 0 and j > 0 else 1
                dp[i][j][3] = dp[i-1][j+1][3] + 1 if i > 0 and j < n-1 else 1
                max_len = max(max_len, max(dp[i][j]))
    return max_len
```
The essence of this problem is to find the longest line of consecutive ones in a matrix by using dynamic programming.
    
### >> 368 Largest Divisible Subset [Medium]
Given a set of distinct positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies: Si % Sj = 0 or Sj % Si = 0.
##### Sample input:
[1,2,3]
[1,2,4,8]
##### Sample output:
[1,2]
[1,2,4,8]

##### Questions to ask to clarify requirements:
What is the maximum size of the input set? Can the input set be empty?

##### Optimal Python solution:
```python
class Solution:
    def largestDivisibleSubset(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
        nums.sort()
        dp = [1] * len(nums)
        prev = [-1] * len(nums)
        max_len = 1
        max_idx = 0
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] % nums[j] == 0 and dp[j] + 1 > dp[i]:
                    dp[i] = dp[j] + 1
                    prev[i] = j
                    if dp[i] > max_len:
                        max_len = dp[i]
                        max_idx = i
        subset = []
        while max_idx != -1:
            subset.append(nums[max_idx])
            max_idx = prev[max_idx]
        return subset[::-1]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Sort the input set in ascending order.
2. Use dynamic programming to find the largest divisible subset.
3. Initialize a dp array to store the length of the largest divisible subset ending at each index.
4. Initialize a prev array to store the previous index in the largest divisible subset.
5. Iterate through the input set and update the dp and prev arrays.
6. Find the index of the maximum length in the dp array.
7. Use the prev array to construct the largest divisible subset.
1. Sort the input set to simplify the dynamic programming process.
2. Use the prev array to construct the largest divisible subset in reverse order.
None
None
    
### >> Comparison: 562 Longest Line of Consecutive One in Matrix [Medium] *VS* 368 Largest Divisible Subset [Medium]
> Similarity distance: 0.4735
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating a matrix.
- Both questions require finding a consecutive sequence of numbers.
- Both questions involve dynamic programming.
##### Differences

- 562 Longest Line of Consecutive One in Matrix focuses on finding the longest line of consecutive ones in a matrix, while 368 Largest Divisible Subset focuses on finding the largest divisible subset of a given set of numbers.
- 562 Longest Line of Consecutive One in Matrix uses a 2D matrix as input, while 368 Largest Divisible Subset uses a 1D array as input.
- 562 Longest Line of Consecutive One in Matrix has a time complexity of O(m * n), where m and n are the dimensions of the matrix, while 368 Largest Divisible Subset has a time complexity of O(n^2), where n is the size of the input array.
- 562 Longest Line of Consecutive One in Matrix requires counting the number of consecutive ones in each direction (horizontal, vertical, diagonal), while 368 Largest Divisible Subset requires finding the largest divisible subset using dynamic programming.
##### New Insights in 368 Largest Divisible Subset [Medium]

- From 562 Longest Line of Consecutive One in Matrix, we can learn how to efficiently count the number of consecutive ones in a matrix by using dynamic programming.
- From 368 Largest Divisible Subset, we can learn how to find the largest divisible subset of a given set of numbers using dynamic programming.


---
# 4. From 368 Largest Divisible Subset [Medium] to 474 Ones and Zeroes [Medium]
> Similarity Distance: 0.4361

### >> Reminder: 368 Largest Divisible Subset [Medium]
Given a set of distinct positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies: Si % Sj = 0 or Sj % Si = 0.
##### Optimal Python solution:
```python
class Solution:
    def largestDivisibleSubset(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
        nums.sort()
        dp = [1] * len(nums)
        prev = [-1] * len(nums)
        max_len = 1
        max_idx = 0
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] % nums[j] == 0 and dp[j] + 1 > dp[i]:
                    dp[i] = dp[j] + 1
                    prev[i] = j
                    if dp[i] > max_len:
                        max_len = dp[i]
                        max_idx = i
        subset = []
        while max_idx != -1:
            subset.append(nums[max_idx])
            max_idx = prev[max_idx]
        return subset[::-1]
```
Dynamic programming is used to find the largest divisible subset.
    
### >> 474 Ones and Zeroes [Medium]
You are given an array of binary strings strs and two integers m and n. Return the size of the largest subset of strs such that there are at most m 0's and n 1's in the subset. A binary string s is a subset of strs if s can be formed by concatenating some number of strs (possibly none) in strs.
##### Sample input:
["10","0001","111001","1","0"]
5
3
##### Sample output:
4

##### Questions to ask to clarify requirements:

- Can the binary strings be used partially?
- What is the maximum number of binary strings?

##### Optimal Python solution:
```python
def findMaxForm(strs, m, n):
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for s in strs:
        zeros = s.count('0')
        ones = s.count('1')
        for i in range(m, zeros - 1, -1):
            for j in range(n, ones - 1, -1):
                dp[i][j] = max(dp[i][j], dp[i - zeros][j - ones] + 1)
    return dp[m][n]
```
##### Time complexity:
O(LMN)
##### Space complexity:
O(MN)
##### Notes:

- Use dynamic programming to solve the problem
- Create a 2D array to store the maximum subset size for each combination of m and n

- Count the number of 0's and 1's in each binary string
- Use a 2D array to store the maximum subset size for each combination of m and n

- The binary strings can be used partially

- Using depth-first search
    
### >> Comparison: 368 Largest Divisible Subset [Medium] *VS* 474 Ones and Zeroes [Medium]
> Similarity distance: 0.4361
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating arrays.
- Both questions require finding subsets of elements that meet certain conditions.
##### Differences

- Question 368 involves finding the largest divisible subset of a given array.
- Question 474 involves finding the maximum number of strings that can be formed using a given number of 0s and 1s, with a constraint on the total number of 0s and 1s used.
##### New Insights in 474 Ones and Zeroes [Medium]

- Question 368 introduces the concept of finding the largest divisible subset, which can be solved using dynamic programming.
- Question 474 introduces the concept of maximizing the number of strings that can be formed using a limited number of 0s and 1s, which can also be solved using dynamic programming.


---
# 5. From 368 Largest Divisible Subset [Medium] to 279 Perfect Squares [Medium]
> Similarity Distance: 0.4454

### >> Reminder: 368 Largest Divisible Subset [Medium]
Given a set of distinct positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies: Si % Sj = 0 or Sj % Si = 0.
##### Optimal Python solution:
```python
class Solution:
    def largestDivisibleSubset(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
        nums.sort()
        dp = [1] * len(nums)
        prev = [-1] * len(nums)
        max_len = 1
        max_idx = 0
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] % nums[j] == 0 and dp[j] + 1 > dp[i]:
                    dp[i] = dp[j] + 1
                    prev[i] = j
                    if dp[i] > max_len:
                        max_len = dp[i]
                        max_idx = i
        subset = []
        while max_idx != -1:
            subset.append(nums[max_idx])
            max_idx = prev[max_idx]
        return subset[::-1]
```
Dynamic programming is used to find the largest divisible subset.
    
### >> 279 Perfect Squares [Medium]
Given an integer n, return the least number of perfect square numbers that sum to n.
##### Sample input:
12
13
##### Sample output:
3
2

##### Questions to ask to clarify requirements:
What is the range of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def numSquares(self, n: int) -> int:
        dp = [float('inf')] * (n + 1)
        dp[0] = 0
        for i in range(1, n + 1):
            j = 1
            while j * j <= i:
                dp[i] = min(dp[i], dp[i - j * j] + 1)
                j += 1
        return dp[n]
```
##### Time complexity:
O(n * sqrt(n))
##### Space complexity:
O(n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Initialize a dp array with infinity values.
3. Iterate from 1 to n and update the dp array.
4. Use a nested loop to check all possible perfect square numbers.
5. Return the value at dp[n].
1. Use a nested loop to check all possible perfect square numbers.
2. Initialize the dp array with infinity values.
None
None
    
### >> Comparison: 368 Largest Divisible Subset [Medium] *VS* 279 Perfect Squares [Medium]
> Similarity distance: 0.4454
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding subsets of numbers that satisfy certain conditions.
- Both questions require dynamic programming to solve efficiently.
##### Differences

- Question 368 involves finding the largest divisible subset of numbers.
- Question 279 involves finding the minimum number of perfect squares that sum up to a given number.
##### New Insights in 279 Perfect Squares [Medium]

- Question 368 teaches us how to find the largest divisible subset using dynamic programming.
- Question 279 teaches us how to find the minimum number of perfect squares using dynamic programming.


---
# 6. From 279 Perfect Squares [Medium] to 416 Partition Equal Subset Sum [Medium]
> Similarity Distance: 0.4359

### >> Reminder: 279 Perfect Squares [Medium]
Given an integer n, return the least number of perfect square numbers that sum to n.
##### Optimal Python solution:
```python
class Solution:
    def numSquares(self, n: int) -> int:
        dp = [float('inf')] * (n + 1)
        dp[0] = 0
        for i in range(1, n + 1):
            j = 1
            while j * j <= i:
                dp[i] = min(dp[i], dp[i - j * j] + 1)
                j += 1
        return dp[n]
```
The essence of this problem is to find the least number of perfect square numbers that sum to a given number.
    
### >> 416 Partition Equal Subset Sum [Medium]
Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.
##### Sample input:
[1,5,11,5]
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the array contain negative integers? Can the array contain duplicates?

##### Optimal Python solution:
```python
def canPartition(nums: List[int]) -> bool:
    total_sum = sum(nums)
    if total_sum % 2 != 0:
        return False
    target_sum = total_sum // 2
    dp = [False] * (target_sum + 1)
    dp[0] = True
    for num in nums:
        for i in range(target_sum, num - 1, -1):
            dp[i] = dp[i] or dp[i - num]
    return dp[target_sum]
```
##### Time complexity:
O(n * target_sum)
##### Space complexity:
O(target_sum)
##### Notes:
1. Check if the total sum of the array is even. If not, return False.
2. Divide the total sum by 2 to get the target sum.
3. Use dynamic programming to check if there is a subset that sums up to the target sum.
Use a boolean array to represent the subset sum.
Using dynamic programming to solve the subset sum problem.
Brute force approach with exponential time complexity.
    
### >> Comparison: 279 Perfect Squares [Medium] *VS* 416 Partition Equal Subset Sum [Medium]
> Similarity distance: 0.4359
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding a specific sum or subset of numbers.
- Both questions require dynamic programming techniques.
- Both questions have multiple possible solutions.
##### Differences

- Question 279 involves finding the minimum number of perfect square numbers that sum up to a given number.
- Question 416 involves partitioning an array into two subsets with equal sums.
- Question 279 has a mathematical approach using Lagrange's four-square theorem.
- Question 416 has a dynamic programming approach using a 2D array.
##### New Insights in 416 Partition Equal Subset Sum [Medium]

- Question 279 teaches us about the properties of perfect square numbers and how they can be used to solve the problem efficiently.
- Question 416 teaches us about the concept of partitioning a set into two equal subsets and how it can be solved using dynamic programming.


---
# 7. From 416 Partition Equal Subset Sum [Medium] to 494 Target Sum [Medium]
> Similarity Distance: 0.4511

### >> Reminder: 416 Partition Equal Subset Sum [Medium]
Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.
##### Optimal Python solution:
```python
def canPartition(nums: List[int]) -> bool:
    total_sum = sum(nums)
    if total_sum % 2 != 0:
        return False
    target_sum = total_sum // 2
    dp = [False] * (target_sum + 1)
    dp[0] = True
    for num in nums:
        for i in range(target_sum, num - 1, -1):
            dp[i] = dp[i] or dp[i - num]
    return dp[target_sum]
```
Use dynamic programming to solve the subset sum problem.
    
### >> 494 Target Sum [Medium]
You are given a list of non-negative integers, a1, a2, ..., an, and a target, S. Now you have 2 symbols + and -. For each integer, you should choose one from + and - as its new symbol. Find out how many ways to assign symbols to make sum of integers equal to target S.
##### Sample input:
[1, 1, 1, 1, 1]
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can the input array contain negative numbers?
- What is the maximum length of the input array?
- Can the input array be empty?

##### Optimal Python solution:
```python
def findTargetSumWays(nums, S):
    total_sum = sum(nums)
    if total_sum < S or (total_sum + S) % 2 != 0:
        return 0
    target = (total_sum + S) // 2
    dp = [0] * (target + 1)
    dp[0] = 1
    for num in nums:
        for i in range(target, num - 1, -1):
            dp[i] += dp[i - num]
    return dp[target]
```
##### Time complexity:
O(n * target)
##### Space complexity:
O(target)
##### Notes:

- Convert the problem to a subset sum problem
- Use dynamic programming to count the number of ways to reach the target sum

- Understand the subset sum problem and its dynamic programming solution
- Pay attention to the conversion of the problem to a subset sum problem

- Converting the problem to a subset sum problem
- Using dynamic programming to count the number of ways

- Using brute force approach to generate all possible combinations
    
### >> Comparison: 416 Partition Equal Subset Sum [Medium] *VS* 494 Target Sum [Medium]
> Similarity distance: 0.4511
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding a subset of numbers that satisfy a certain condition.
- Both questions require dynamic programming to solve efficiently.
##### Differences

- 416 Partition Equal Subset Sum: The goal is to partition the given array into two subsets with equal sum.
- 494 Target Sum: The goal is to find the number of ways to achieve a target sum by assigning a positive or negative sign to each element in the given array.
##### New Insights in 494 Target Sum [Medium]

- 416 Partition Equal Subset Sum: The problem can be reduced to finding a subset with a target sum equal to half of the total sum of the array.
- 494 Target Sum: The problem can be solved using a variation of the 0/1 Knapsack problem.

