
# Leetcode Intensive Tutorial Day 50 
> [Difficulty Score: 24]

> [Version: 20231226_040350]

> [Including this day, you had studied : 421 leetcode problems]


## Courses overview of the day

- 455 Assign Cookies [Easy]
  - 135 Candy [Hard]
    - 330 Patching Array [Hard]
      - 55 Jump Game [Medium]
        - 45 Jump Game II [Hard]
          - 334 Increasing Triplet Subsequence [Medium]
      - 321 Create Maximum Number [Hard]
      - 43 Multiply Strings [Medium]
    - 575 Distribute Candies [Easy]

#### Step by step

 - [1. From 455 Assign Cookies [Easy] to 135 Candy [Hard]](#1-from-455-assign-cookies-easy-to-135-candy-hard))

 - [2. From 135 Candy [Hard] to 330 Patching Array [Hard]](#2-from-135-candy-hard-to-330-patching-array-hard))

 - [3. From 330 Patching Array [Hard] to 55 Jump Game [Medium]](#3-from-330-patching-array-hard-to-55-jump-game-medium))

 - [4. From 55 Jump Game [Medium] to 45 Jump Game II [Hard]](#4-from-55-jump-game-medium-to-45-jump-game-ii-hard))

 - [5. From 45 Jump Game II [Hard] to 334 Increasing Triplet Subsequence [Medium]](#5-from-45-jump-game-ii-hard-to-334-increasing-triplet-subsequence-medium))

 - [6. From 330 Patching Array [Hard] to 321 Create Maximum Number [Hard]](#6-from-330-patching-array-hard-to-321-create-maximum-number-hard))

 - [7. From 330 Patching Array [Hard] to 43 Multiply Strings [Medium]](#7-from-330-patching-array-hard-to-43-multiply-strings-medium))

 - [8. From 135 Candy [Hard] to 575 Distribute Candies [Easy]](#8-from-135-candy-hard-to-575-distribute-candies-easy))

    

#### Summary


- 55 Jump Game : Determining if it is possible to reach the last index of an array using a greedy approach.
- 135 Candy : The essence of this problem is to assign candies to children based on their ratings, ensuring that each child has at least one candy and children with higher ratings get more candies than their neighbors.
- 330 Patching Array : The essence of the problem is to find the minimum number of patches required to form any number in a given range using elements from a sorted array.
- 321 Create Maximum Number : The essence of this problem is to find the maximum number that can be formed by selecting numbers from two arrays.
- 455 Assign Cookies : The essence of this problem is to find the maximum number of content children by assigning cookies to children based on their greed factor and the size of the available cookies.
- 43 Multiply Strings : The essence of this problem is to perform multiplication of two numbers represented as strings without using built-in multiplication or conversion functions.
- 45 Jump Game II : Find the minimum number of jumps required to reach the last index.
- 334 Increasing Triplet Subsequence : Check if there exists a triplet of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k].
- 575 Distribute Candies : Distribute candies equally to brother and sister and find the maximum number of kinds of candies the sister could gain.
> Similarity Diameter of these problems: 0.7389


---
# 1. From 455 Assign Cookies [Easy] to 135 Candy [Hard]
> Similarity Distance: 0.5855

### >> 455 Assign Cookies [Easy]
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.
##### Sample input:
[1,2,3], [1,1]
##### Sample output:
1

##### Questions to ask to clarify requirements:
What is the maximum number of content children that can be achieved?

##### Optimal Python solution:
```python
def findContentChildren(g, s):
    g.sort()
    s.sort()
    i = 0
    for j in range(len(s)):
        if i == len(g):
            break
        if s[j] >= g[i]:
            i += 1
    return i
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(1)
##### Notes:
1. Sort the greed factor and cookie size arrays
2. Iterate through the cookie size array and assign cookies to children if the size is greater than or equal to the greed factor
3. Return the number of children who received cookies
Use the sort() function to sort the arrays in ascending order.
None
None
    
### >> 135 Candy [Hard]
There are N children standing in a line. Each child is assigned a rating value. You are giving candies to these children subjected to the following requirements: Each child must have at least one candy. Children with a higher rating get more candies than their neighbors. What is the minimum candies you must give?
##### Sample input:
[1,0,2]
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can the ratings be negative?
- Can the ratings be floating point numbers?
- Can the ratings be zero?
- Can the length of ratings be zero?
- Can the length of ratings be one?

##### Optimal Python solution:
```python
def candy(ratings):
    n = len(ratings)
    candies = [1] * n
    for i in range(1, n):
        if ratings[i] > ratings[i-1]:
            candies[i] = candies[i-1] + 1
    for i in range(n-2, -1, -1):
        if ratings[i] > ratings[i+1] and candies[i] <= candies[i+1]:
            candies[i] = candies[i+1] + 1
    return sum(candies)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Each child must have at least one candy
- Children with a higher rating get more candies than their neighbors

- Use two passes through the ratings array to assign candies to the children.
- Start with assigning one candy to each child.
- In the first pass, assign more candies to children with higher ratings than their neighbors.
- In the second pass, assign more candies to children with higher ratings than their neighbors and fewer candies than their neighbors.
- Return the sum of all the candies as the minimum number of candies required.

- The solution uses two passes through the ratings array

- Using a sorting algorithm
    
### >> Comparison: 455 Assign Cookies [Easy] *VS* 135 Candy [Hard]
> Similarity distance: 0.5855
##### Similarities

- Both questions involve distributing cookies or candies to children.
- Both questions have a limited supply of cookies or candies.
- Both questions require maximizing the number of satisfied children.
##### Differences

- 455 Assign Cookies: In this question, each child can only be assigned one cookie, and each cookie has a size.
- 135 Candy: In this question, each child can be assigned multiple candies, and each candy has a rating.
##### New Insights in 135 Candy [Hard]

- 455 Assign Cookies: The size of the cookie matters in determining whether a child can be satisfied.
- 135 Candy: The rating of the candy matters in determining the satisfaction level of a child.


---
# 2. From 135 Candy [Hard] to 330 Patching Array [Hard]
> Similarity Distance: 0.4961

### >> Reminder: 135 Candy [Hard]
There are N children standing in a line. Each child is assigned a rating value. You are giving candies to these children subjected to the following requirements: Each child must have at least one candy. Children with a higher rating get more candies than their neighbors. What is the minimum candies you must give?
##### Optimal Python solution:
```python
def candy(ratings):
    n = len(ratings)
    candies = [1] * n
    for i in range(1, n):
        if ratings[i] > ratings[i-1]:
            candies[i] = candies[i-1] + 1
    for i in range(n-2, -1, -1):
        if ratings[i] > ratings[i+1] and candies[i] <= candies[i+1]:
            candies[i] = candies[i+1] + 1
    return sum(candies)
```
The essence of this problem is to assign candies to children based on their ratings, ensuring that each child has at least one candy and children with higher ratings get more candies than their neighbors.
    
### >> 330 Patching Array [Hard]
Given a sorted positive integer array nums and an integer n, add/patch elements to the array such that any number in the range [1, n] can be formed by the sum of some elements in the array. Return the minimum number of patches required.
##### Sample input:
[1,3], 6
##### Sample output:
1

##### Questions to ask to clarify requirements:

- Can the array contain negative numbers?
- Can the array contain duplicates?
- Can the array be empty?

##### Optimal Python solution:
```python
def minPatches(nums, n):
    patches = 0
    covered = 0
    i = 0
    while covered < n:
        if i < len(nums) and nums[i] <= covered + 1:
            covered += nums[i]
            i += 1
        else:
            covered += covered + 1
            patches += 1
    return patches
```
##### Time complexity:
O(m + log(n))
##### Space complexity:
O(1)
##### Notes:

- Use a greedy approach to add/patch elements to the array.
- Track the range of numbers that can be formed using the current elements in the array.
- Add the smallest missing number to the array to expand the range.

- Start with an empty range and add the smallest missing number to expand the range.
- Optimize the solution by avoiding unnecessary additions to the array.

- The array is sorted in ascending order.
- The array can contain duplicates.
- The array can be empty.

- Avoid using a brute force approach to check all possible combinations of elements.
- Avoid sorting the array multiple times.
    
### >> Comparison: 135 Candy [Hard] *VS* 330 Patching Array [Hard]
> Similarity distance: 0.4961
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve manipulating arrays.
- Both questions require finding the minimum number of operations to achieve a certain goal.
##### Differences

- Question 135 'Candy' involves distributing candies to children, while question 330 'Patching Array' involves patching an array.
- Question 135 'Candy' requires ensuring that children with a higher rating receive more candies, while question 330 'Patching Array' requires ensuring that a given array is patched to contain all numbers from 1 to a certain limit.
- Question 135 'Candy' can be solved using a greedy algorithm, while question 330 'Patching Array' can be solved using a greedy approach combined with dynamic programming.
##### New Insights in 330 Patching Array [Hard]

- Question 135 'Candy' teaches us how to use a greedy algorithm to solve a problem involving distributing resources.
- Question 330 'Patching Array' teaches us how to use a combination of greedy approach and dynamic programming to solve a problem involving patching an array.


---
# 3. From 330 Patching Array [Hard] to 55 Jump Game [Medium]
> Similarity Distance: 0.4008

### >> Reminder: 330 Patching Array [Hard]
Given a sorted positive integer array nums and an integer n, add/patch elements to the array such that any number in the range [1, n] can be formed by the sum of some elements in the array. Return the minimum number of patches required.
##### Optimal Python solution:
```python
def minPatches(nums, n):
    patches = 0
    covered = 0
    i = 0
    while covered < n:
        if i < len(nums) and nums[i] <= covered + 1:
            covered += nums[i]
            i += 1
        else:
            covered += covered + 1
            patches += 1
    return patches
```
The essence of the problem is to find the minimum number of patches required to form any number in a given range using elements from a sorted array.
    
### >> 55 Jump Game [Medium]
Given an array of non-negative integers, you are initially positioned at the first index of the array. Each element in the array represents your maximum jump length at that position. Determine if you are able to reach the last index.
##### Sample input:
[2,3,1,1,4]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can we assume that the input array is non-empty?
- Can we assume that the input array contains only non-negative integers?

##### Optimal Python solution:
```python
def canJump(nums):
    max_reach = 0
    for i in range(len(nums)):
        if i > max_reach:
            return False
        max_reach = max(max_reach, i + nums[i])
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use a variable to keep track of the maximum reach
- Iterate through the array and update the maximum reach at each position
- If the current position is greater than the maximum reach, return False
- If the last index is reachable, return True

- Use a variable to keep track of the maximum reach
- Iterate through the array and update the maximum reach at each position
- Check if the current position is greater than the maximum reach

- Determining the maximum reach at each position
- Checking if the current position is greater than the maximum reach

- Using recursion to solve the problem
    
### >> Comparison: 330 Patching Array [Hard] *VS* 55 Jump Game [Medium]
> Similarity distance: 0.4008
##### Similarities

- Both questions involve manipulating an array.
- Both questions require determining if a certain condition can be satisfied.
- Both questions have a greedy algorithm solution.
##### Differences

- Patching Array requires adding the minimum number of elements to the array to satisfy a condition, while Jump Game requires determining if it is possible to reach the last index of the array.
- Patching Array has a time complexity of O(n), while Jump Game has a time complexity of O(n^2).
- Patching Array is classified as a Hard level question, while Jump Game is classified as a Medium level question.
##### New Insights in 55 Jump Game [Medium]

- Patching Array teaches us how to use a greedy algorithm to solve a problem involving array manipulation.
- Jump Game teaches us how to use dynamic programming to solve a problem involving array traversal.


---
# 4. From 55 Jump Game [Medium] to 45 Jump Game II [Hard]
> Similarity Distance: 0.3708

### >> Reminder: 55 Jump Game [Medium]
Given an array of non-negative integers, you are initially positioned at the first index of the array. Each element in the array represents your maximum jump length at that position. Determine if you are able to reach the last index.
##### Optimal Python solution:
```python
def canJump(nums):
    max_reach = 0
    for i in range(len(nums)):
        if i > max_reach:
            return False
        max_reach = max(max_reach, i + nums[i])
    return True
```
Determining if it is possible to reach the last index of an array using a greedy approach.
    
### >> 45 Jump Game II [Hard]
Given an array of non-negative integers nums, you are initially positioned at the first index of the array. Each element in the array represents your maximum jump length at that position. Your goal is to reach the last index in the minimum number of jumps. Return the minimum number of jumps required to reach the last index.
##### Sample input:
[2,3,1,1,4]
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can the array be empty?
- Can the array contain negative integers?
- Can the array contain duplicates?

##### Optimal Python solution:
```python
def jump(nums):
    if len(nums) <= 1:
        return 0
    jumps = 0
    curr_end = 0
    curr_farthest = 0
    for i in range(len(nums) - 1):
        curr_farthest = max(curr_farthest, i + nums[i])
        if i == curr_end:
            jumps += 1
            curr_end = curr_farthest
    return jumps
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use greedy approach
- Track the current farthest index that can be reached
- Update the current end index when reaching it

- Use the max() function to update the current farthest index.
- Use a loop to iterate through the array.

- Finding the current farthest index
- Updating the current end index

- Using a recursive approach
    
### >> Comparison: 55 Jump Game [Medium] *VS* 45 Jump Game II [Hard]
> Similarity distance: 0.3708
##### Similarities

- Both questions are related to jumping or moving in a game.
- Both questions involve determining if it is possible to reach a certain position.
- Both questions require finding the minimum number of jumps needed to reach a target.
##### Differences

- Question 55 is a medium difficulty level, while question 45 is a hard difficulty level.
- Question 55 asks if it is possible to reach the last index, while question 45 asks for the minimum number of jumps to reach the last index.
- Question 55 can be solved using a greedy algorithm, while question 45 requires a dynamic programming approach.
##### New Insights in 45 Jump Game II [Hard]

- Question 55: The greedy algorithm works because we only need to check if we can reach each position, not the minimum number of jumps.
- Question 45: Dynamic programming can be used to efficiently find the minimum number of jumps by keeping track of the minimum jumps needed at each position.


---
# 5. From 45 Jump Game II [Hard] to 334 Increasing Triplet Subsequence [Medium]
> Similarity Distance: 0.4470

### >> Reminder: 45 Jump Game II [Hard]
Given an array of non-negative integers nums, you are initially positioned at the first index of the array. Each element in the array represents your maximum jump length at that position. Your goal is to reach the last index in the minimum number of jumps. Return the minimum number of jumps required to reach the last index.
##### Optimal Python solution:
```python
def jump(nums):
    if len(nums) <= 1:
        return 0
    jumps = 0
    curr_end = 0
    curr_farthest = 0
    for i in range(len(nums) - 1):
        curr_farthest = max(curr_farthest, i + nums[i])
        if i == curr_end:
            jumps += 1
            curr_end = curr_farthest
    return jumps
```
Find the minimum number of jumps required to reach the last index.
    
### >> 334 Increasing Triplet Subsequence [Medium]
Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.
##### Sample input:
[1,2,3,4,5]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the input array be empty?
- Can the input array have duplicate values?

##### Optimal Python solution:
```python
class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        first = second = float('inf')
        for num in nums:
            if num <= first:
                first = num
            elif num <= second:
                second = num
            else:
                return True
        return False
```
##### Time complexity:
O(N)
##### Space complexity:
O(1)
##### Notes:

- The problem can be solved using a greedy approach.
- We keep track of the smallest and second smallest numbers seen so far.
- If we find a number greater than the second smallest number, we have found an increasing triplet.
- If we reach the end of the array without finding an increasing triplet, we return false.

- Use a greedy approach to keep track of the smallest and second smallest numbers seen so far.
- Return true if we find a number greater than the second smallest number.
- Return false if we reach the end of the array without finding an increasing triplet.

- Handling the case where the input array has duplicate values.

- Using an inefficient approach that checks all possible triplets.
    
### >> Comparison: 45 Jump Game II [Hard] *VS* 334 Increasing Triplet Subsequence [Medium]
> Similarity distance: 0.4470
##### Similarities

- Both questions involve finding a sequence of numbers that satisfy certain conditions.
- Both questions require iterating through an array and making decisions based on the values encountered.
- Both questions have a time complexity of O(n).
##### Differences

- Jump Game II focuses on finding the minimum number of jumps needed to reach the end of the array, while Increasing Triplet Subsequence focuses on finding a subsequence of length 3 that is increasing.
- Jump Game II uses a greedy algorithm approach, while Increasing Triplet Subsequence uses a dynamic programming approach.
- Jump Game II requires keeping track of the maximum reachable index at each step, while Increasing Triplet Subsequence requires keeping track of the smallest and second smallest elements encountered so far.
##### New Insights in 334 Increasing Triplet Subsequence [Medium]

- Jump Game II teaches us how to efficiently navigate through an array by making optimal decisions at each step.
- Increasing Triplet Subsequence teaches us how to find a subsequence with a specific pattern in an array.
- Both questions provide insights into different problem-solving techniques and algorithms.


---
# 6. From 330 Patching Array [Hard] to 321 Create Maximum Number [Hard]
> Similarity Distance: 0.4121

### >> Reminder: 330 Patching Array [Hard]
Given a sorted positive integer array nums and an integer n, add/patch elements to the array such that any number in the range [1, n] can be formed by the sum of some elements in the array. Return the minimum number of patches required.
##### Optimal Python solution:
```python
def minPatches(nums, n):
    patches = 0
    covered = 0
    i = 0
    while covered < n:
        if i < len(nums) and nums[i] <= covered + 1:
            covered += nums[i]
            i += 1
        else:
            covered += covered + 1
            patches += 1
    return patches
```
The essence of the problem is to find the minimum number of patches required to form any number in a given range using elements from a sorted array.
    
### >> 321 Create Maximum Number [Hard]
Given two arrays of length m and n with digits 0-9 representing two numbers. Create the maximum number of length k <= m + n from digits of the two. The relative order of the digits from the same array must be preserved. Return an array of the k digits.
##### Sample input:
[[3,4,6,5],[9,1,2,5,8,3]]
5
##### Sample output:
[9,8,6,5,3]

##### Questions to ask to clarify requirements:

- Can the input arrays be empty?
- Can the input arrays contain negative numbers?
- Can the input arrays have duplicate numbers?

##### Optimal Python solution:
```python
def maxNumber(self, nums1: List[int], nums2: List[int], k: int) -> List[int]:
    def prep(nums, k):
        drop = len(nums) - k
        out = []
        for num in nums:
            while drop and out and out[-1] < num:
                out.pop()
                drop -= 1
            out.append(num)
        return out[:k]

    def merge(a, b):
        return [max(a, b).pop(0) for _ in a+b]

    return max(merge(prep(nums1, i), prep(nums2, k-i)) for i in range(k+1) if i <= len(nums1) and k-i <= len(nums2))
```
##### Time complexity:
O((m+n)^3)
##### Space complexity:
O(m+n)
##### Notes:

- Use a greedy approach to select the maximum number from each array.
- Merge the selected numbers to form the maximum number of length k.
- Try all possible combinations of selecting numbers from both arrays.

- Use a stack to keep track of the selected numbers.
- Use a loop to try all possible combinations of selecting numbers.
- Use the max function to select the maximum number from two arrays.

- The maximum number can be formed by selecting numbers from both arrays in different combinations.
- The relative order of the digits from the same array must be preserved.

- Avoid using sorting algorithms to find the maximum number.
- Avoid using brute force approach to try all possible combinations of selecting numbers.
    
### >> Comparison: 330 Patching Array [Hard] *VS* 321 Create Maximum Number [Hard]
> Similarity distance: 0.4121
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve manipulating arrays.
- Both questions require finding the maximum possible value.
- Both questions involve some form of optimization.
##### Differences

- Question 330 involves patching an array, while question 321 involves creating a maximum number.
- Question 330 allows patching any number of elements in the array, while question 321 has a fixed number of elements to create the maximum number.
- Question 330 has a time complexity requirement of O(n), while question 321 does not have a specific time complexity requirement.
- Question 330 has a greedy algorithm solution, while question 321 has a combination of greedy and dynamic programming solutions.
##### New Insights in 321 Create Maximum Number [Hard]

- Question 330 introduces the concept of patching an array by adding missing elements to make it a valid sequence.
- Question 321 introduces the concept of creating the maximum number by selecting elements from two arrays and maintaining the relative order.


---
# 7. From 330 Patching Array [Hard] to 43 Multiply Strings [Medium]
> Similarity Distance: 0.4770

### >> Reminder: 330 Patching Array [Hard]
Given a sorted positive integer array nums and an integer n, add/patch elements to the array such that any number in the range [1, n] can be formed by the sum of some elements in the array. Return the minimum number of patches required.
##### Optimal Python solution:
```python
def minPatches(nums, n):
    patches = 0
    covered = 0
    i = 0
    while covered < n:
        if i < len(nums) and nums[i] <= covered + 1:
            covered += nums[i]
            i += 1
        else:
            covered += covered + 1
            patches += 1
    return patches
```
The essence of the problem is to find the minimum number of patches required to form any number in a given range using elements from a sorted array.
    
### >> 43 Multiply Strings [Medium]
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.
##### Sample input:
"2"
"3"
##### Sample output:
"6"

##### Questions to ask to clarify requirements:
What is the maximum length of the input strings? Can the input strings be empty?

##### Optimal Python solution:
```python
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        n1 = len(num1)
        n2 = len(num2)
        pos = [0] * (n1 + n2)
        for i in range(n1 - 1, -1, -1):
            for j in range(n2 - 1, -1, -1):
                mul = (ord(num1[i]) - ord('0')) * (ord(num2[j]) - ord('0'))
                p1 = i + j
                p2 = i + j + 1
                sum = mul + pos[p2]
                pos[p1] += sum // 10
                pos[p2] = sum % 10
        result = ""
        for p in pos:
            if not (len(result) == 0 and p == 0):
                result += str(p)
        return "0" if len(result) == 0 else result
```
##### Time complexity:
O(n * m)
##### Space complexity:
O(n + m)
##### Notes:
1. Use an array to store the intermediate results
2. Iterate through the input strings from right to left
3. Perform multiplication and addition operations
4. Handle carry and overflow
5. Convert the array to a string
1. Use ord() to convert a character to its ASCII value
2. Use // and % operators for division and remainder
3. Use str() to convert an integer to a string
Handling carry and overflow
Using built-in multiplication or conversion functions
    
### >> Comparison: 330 Patching Array [Hard] *VS* 43 Multiply Strings [Medium]
> Similarity distance: 0.4770
##### Similarities

- Both questions are from LeetCode.
- Both questions require manipulating arrays.
- Both questions have multiple test cases.
##### Differences

- 330 Patching Array is classified as a Hard level question, while 43 Multiply Strings is classified as a Medium level question.
- 330 Patching Array involves patching an array to make it contain all numbers from 1 to n, while 43 Multiply Strings involves multiplying two strings representing non-negative integers.
- 330 Patching Array requires finding the minimum number of patches needed, while 43 Multiply Strings requires implementing the multiplication algorithm for strings.
- 330 Patching Array has a time complexity requirement of O(log n), while 43 Multiply Strings does not have a specific time complexity requirement.
##### New Insights in 43 Multiply Strings [Medium]

- From 330 Patching Array, we can learn how to efficiently patch an array to contain all numbers from 1 to n.
- From 43 Multiply Strings, we can learn how to implement the multiplication algorithm for strings representing non-negative integers.


---
# 8. From 135 Candy [Hard] to 575 Distribute Candies [Easy]
> Similarity Distance: 0.5447

### >> Reminder: 135 Candy [Hard]
There are N children standing in a line. Each child is assigned a rating value. You are giving candies to these children subjected to the following requirements: Each child must have at least one candy. Children with a higher rating get more candies than their neighbors. What is the minimum candies you must give?
##### Optimal Python solution:
```python
def candy(ratings):
    n = len(ratings)
    candies = [1] * n
    for i in range(1, n):
        if ratings[i] > ratings[i-1]:
            candies[i] = candies[i-1] + 1
    for i in range(n-2, -1, -1):
        if ratings[i] > ratings[i+1] and candies[i] <= candies[i+1]:
            candies[i] = candies[i+1] + 1
    return sum(candies)
```
The essence of this problem is to assign candies to children based on their ratings, ensuring that each child has at least one candy and children with higher ratings get more candies than their neighbors.
    
### >> 575 Distribute Candies [Easy]
Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain.
##### Sample input:
[1,1,2,2,3,3]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- What is the maximum number of candies that can be distributed?
- Can the candies be distributed unevenly?
- Can the candies be negative?
- Can the candies be floating point numbers?

##### Optimal Python solution:
```python
def distributeCandies(candies):
    return min(len(candies) // 2, len(set(candies)))
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The maximum number of kinds of candies the sister could gain is the minimum of half the length of the input array and the number of unique candies.
- Use a set to count the number of unique candies.

- Use the set data structure to count the number of unique candies.
- Use integer division to calculate half the length of the input array.

- None

- None
    
### >> Comparison: 135 Candy [Hard] *VS* 575 Distribute Candies [Easy]
> Similarity distance: 0.5447
##### Similarities

- Both questions involve distributing candies
- Both questions have a constraint on the number of candies each person can have
##### Differences

- 135 Candy is a hard question, while 575 Distribute Candies is an easy question
- 135 Candy requires optimizing the distribution to minimize the total number of candies, while 575 Distribute Candies requires maximizing the number of unique candies each person can have
- 135 Candy involves a greedy algorithm approach, while 575 Distribute Candies can be solved using a simple mathematical formula
##### New Insights in 575 Distribute Candies [Easy]

- In 135 Candy, we can use a greedy algorithm to distribute the candies in an optimal way
- In 575 Distribute Candies, we can use a mathematical formula to calculate the maximum number of unique candies each person can have

