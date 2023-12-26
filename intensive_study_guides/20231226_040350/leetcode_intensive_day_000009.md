
# Leetcode Intensive Tutorial Day 9 
> [Difficulty Score: 12]

> [Version: 20231226_040350]

> [Including this day, you had studied : 66 leetcode problems]


## Courses overview of the day

- 461 Hamming Distance [Easy]
  - 136 Single Number [Easy]
    - 137 Single Number II [Medium]
      - 260 Single Number III [Medium]
        - 389 Find the Difference [Easy]
          - 243 Shortest Word Distance [Easy]
            - 245 Shortest Word Distance III [Medium]
            - 244 Shortest Word Distance II [Medium]

#### Step by step

 - [1. From 461 Hamming Distance [Easy] to 136 Single Number [Easy]](#1-from-461-hamming-distance-easy-to-136-single-number-easy))

 - [2. From 136 Single Number [Easy] to 137 Single Number II [Medium]](#2-from-136-single-number-easy-to-137-single-number-ii-medium))

 - [3. From 137 Single Number II [Medium] to 260 Single Number III [Medium]](#3-from-137-single-number-ii-medium-to-260-single-number-iii-medium))

 - [4. From 260 Single Number III [Medium] to 389 Find the Difference [Easy]](#4-from-260-single-number-iii-medium-to-389-find-the-difference-easy))

 - [5. From 389 Find the Difference [Easy] to 243 Shortest Word Distance [Easy]](#5-from-389-find-the-difference-easy-to-243-shortest-word-distance-easy))

 - [6. From 243 Shortest Word Distance [Easy] to 245 Shortest Word Distance III [Medium]](#6-from-243-shortest-word-distance-easy-to-245-shortest-word-distance-iii-medium))

 - [7. From 243 Shortest Word Distance [Easy] to 244 Shortest Word Distance II [Medium]](#7-from-243-shortest-word-distance-easy-to-244-shortest-word-distance-ii-medium))

    

#### Summary


- 244 Shortest Word Distance II : Finding the shortest distance between two words in a list using a class with a constructor and a method.
- 461 Hamming Distance : The Hamming distance between two integers is the number of positions at which the corresponding bits are different.
- 260 Single Number III : Given an array with exactly two elements appearing only once, find those two elements.
- 137 Single Number II : Using bitwise operations to find the single element that appears only once.
- 243 Shortest Word Distance : Finding the shortest distance between two words in a list.
- 245 Shortest Word Distance III : Finding the shortest distance between two words in a list
- 389 Find the Difference : Use XOR to find the difference between two strings.
- 136 Single Number : The essence of this problem is to find the single number in an array where every element appears twice except for one.
> Similarity Diameter of these problems: 0.6834


---
# 1. From 461 Hamming Distance [Easy] to 136 Single Number [Easy]
> Similarity Distance: 0.4129

### >> 461 Hamming Distance [Easy]
The Hamming distance between two integers is the number of positions at which the corresponding bits are different. Given two integers x and y, calculate the Hamming distance.
##### Sample input:
1
4
##### Sample output:
2

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def hammingDistance(x: int, y: int) -> int:
    return bin(x ^ y).count('1')
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
Use XOR to find the different bits, then count the number of '1' bits.
None
None
None
    
### >> 136 Single Number [Easy]
Given a non-empty array of integers, every element appears twice except for one. Find that single one.
##### Sample input:
[2,2,1]
##### Sample output:
1

##### Questions to ask to clarify requirements:

- Can the array contain negative numbers?
- Can the array contain floating point numbers?
- Can the array contain zero?
- Can the length of the array be zero?
- Can the length of the array be one?

##### Optimal Python solution:
```python
def singleNumber(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Every element appears twice except for one

- Use bitwise XOR operation to find the single number.
- Initialize the result variable to 0.
- Iterate through the array and XOR each number with the result variable.
- Return the result variable as the single number.

- The solution uses bitwise XOR operation

- Using a sorting algorithm
    
### >> Comparison: 461 Hamming Distance [Easy] *VS* 136 Single Number [Easy]
> Similarity distance: 0.4129
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve bitwise operations.
- Both questions require finding the difference between two numbers.
##### Differences

- Hamming Distance involves finding the number of positions at which the corresponding bits are different in two given integers.
- Single Number involves finding the number that appears only once in an array of integers.
##### New Insights in 136 Single Number [Easy]

- Hamming Distance can be solved using XOR operation to find the number of differing bits.
- Single Number can be solved using XOR operation to find the number that appears only once.


---
# 2. From 136 Single Number [Easy] to 137 Single Number II [Medium]
> Similarity Distance: 0.3947

### >> Reminder: 136 Single Number [Easy]
Given a non-empty array of integers, every element appears twice except for one. Find that single one.
##### Optimal Python solution:
```python
def singleNumber(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```
The essence of this problem is to find the single number in an array where every element appears twice except for one.
    
### >> 137 Single Number II [Medium]
Given an integer array nums where every element appears three times except for one, which appears exactly once. Find the single element and return it.
##### Sample input:
[2,2,3,2]
##### Sample output:
3

##### Questions to ask to clarify requirements:
Are there any constraints on the input array size? Can the input array be empty?

##### Optimal Python solution:
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        ones = 0
        twos = 0
        for num in nums:
            ones = (ones ^ num) & ~twos
            twos = (twos ^ num) & ~ones
        return ones
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use bitwise XOR to find the elements that appear only once
- Use bitwise AND to clear the bits that appear three times
- Use bitwise NOT to invert the bits

- Understand the bitwise XOR and AND operations.
- Be familiar with bitwise manipulation techniques.

- Understanding the bitwise operations used in the solution

- Using extra space
- Sorting the array
    
### >> Comparison: 136 Single Number [Easy] *VS* 137 Single Number II [Medium]
> Similarity distance: 0.3947
##### Similarities

- Both questions are related to finding a single number in an array.
- Both questions have a time complexity requirement of O(n) and a space complexity requirement of O(1).
##### Differences

- Question 136 is classified as an Easy level question, while Question 137 is classified as a Medium level question.
- Question 136 requires finding the single number that appears only once in the array, while Question 137 requires finding the single number that appears exactly three times in the array.
- Question 136 can be solved using bitwise XOR operation, while Question 137 requires a different approach using bitwise operations and counting bits.
##### New Insights in 137 Single Number II [Medium]

- Question 136 introduces the concept of using bitwise XOR operation to find the single number that appears only once in an array.
- Question 137 introduces the concept of using bitwise operations and counting bits to find the single number that appears exactly three times in an array.


---
# 3. From 137 Single Number II [Medium] to 260 Single Number III [Medium]
> Similarity Distance: 0.4499

### >> Reminder: 137 Single Number II [Medium]
Given an integer array nums where every element appears three times except for one, which appears exactly once. Find the single element and return it.
##### Optimal Python solution:
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        ones = 0
        twos = 0
        for num in nums:
            ones = (ones ^ num) & ~twos
            twos = (twos ^ num) & ~ones
        return ones
```
Using bitwise operations to find the single element that appears only once.
    
### >> 260 Single Number III [Medium]
Given an integer array nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.
##### Sample input:
nums = [1,2,1,3,2,5]
##### Sample output:
[3,5]

##### Questions to ask to clarify requirements:
Can the array contain negative numbers? Can the two elements that appear only once be the same?

##### Optimal Python solution:
```python
def singleNumber(nums):
    xor = 0
    for num in nums:
        xor ^= num
    mask = xor & (-xor)
    num1 = 0
    num2 = 0
    for num in nums:
        if num & mask:
            num1 ^= num
        else:
            num2 ^= num
    return [num1, num2]
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use XOR to find the XOR of the two elements that appear only once
- Use the XOR result to find a mask that separates the two elements
- Use XOR again to find the two elements

- Handle negative numbers in the array

- Finding the mask to separate the two elements

- Using a brute force approach with nested loops
    
### >> Comparison: 137 Single Number II [Medium] *VS* 260 Single Number III [Medium]
> Similarity distance: 0.4499
##### Similarities

- Both questions are related to finding single numbers in an array.
- Both questions have a time complexity requirement of O(n) and a space complexity requirement of O(1).
##### Differences

- In question 137, the array contains elements that appear three times except for one element that appears only once.
- In question 260, the array contains elements that appear twice except for two elements that appear only once.
- Question 137 requires finding the single number that appears only once, while question 260 requires finding the two single numbers that appear only once.
- Question 137 can be solved using bitwise operations, while question 260 requires a different approach using bit manipulation.
##### New Insights in 260 Single Number III [Medium]

- Question 137 introduces the concept of using bitwise operations to solve problems efficiently.
- Question 260 introduces the concept of using bit manipulation to solve problems with multiple single numbers.


---
# 4. From 260 Single Number III [Medium] to 389 Find the Difference [Easy]
> Similarity Distance: 0.4434

### >> Reminder: 260 Single Number III [Medium]
Given an integer array nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.
##### Optimal Python solution:
```python
def singleNumber(nums):
    xor = 0
    for num in nums:
        xor ^= num
    mask = xor & (-xor)
    num1 = 0
    num2 = 0
    for num in nums:
        if num & mask:
            num1 ^= num
        else:
            num2 ^= num
    return [num1, num2]
```
Given an array with exactly two elements appearing only once, find those two elements.
    
### >> 389 Find the Difference [Easy]
Given two strings s and t which consist of only lowercase letters, find the difference between the two strings.
##### Sample input:
"abcd"
"abcde"
##### Sample output:
"e"

##### Questions to ask to clarify requirements:
What should be the output if the strings are empty?

##### Optimal Python solution:
```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        diff = 0
        for char in s:
            diff ^= ord(char)
        for char in t:
            diff ^= ord(char)
        return chr(diff)
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use XOR to find the difference between two strings.
None
None
None
    
### >> Comparison: 260 Single Number III [Medium] *VS* 389 Find the Difference [Easy]
> Similarity distance: 0.4434
##### Similarities
Both questions involve finding a difference between two sets of numbers.
##### Differences
Question 260 requires finding two unique numbers in an array, while question 389 requires finding a single character that is added to one string.
##### New Insights in 389 Find the Difference [Easy]
Question 260 introduces the concept of using bitwise XOR to find the difference between two numbers, while question 389 highlights the use of character manipulation to find the added character.


---
# 5. From 389 Find the Difference [Easy] to 243 Shortest Word Distance [Easy]
> Similarity Distance: 0.5685

### >> Reminder: 389 Find the Difference [Easy]
Given two strings s and t which consist of only lowercase letters, find the difference between the two strings.
##### Optimal Python solution:
```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        diff = 0
        for char in s:
            diff ^= ord(char)
        for char in t:
            diff ^= ord(char)
        return chr(diff)
```
Use XOR to find the difference between two strings.
    
### >> 243 Shortest Word Distance [Easy]
Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.
##### Sample input:
words = ["practice", "makes", "perfect", "coding", "makes"]
word1 = "coding"
word2 = "practice"
##### Sample output:
Output: 3

##### Questions to ask to clarify requirements:

- Can the list of words be empty?
- Can word1 and word2 be the same word?

##### Optimal Python solution:
```python
def shortestDistance(words, word1, word2):
    index1 = -1
    index2 = -1
    min_distance = float('inf')
    for i in range(len(words)):
        if words[i] == word1:
            index1 = i
        elif words[i] == word2:
            index2 = i
        if index1 != -1 and index2 != -1:
            min_distance = min(min_distance, abs(index1 - index2))
    return min_distance
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to keep track of the indices of word1 and word2
- Update the minimum distance whenever both pointers are valid

- Use meaningful variable names to improve code readability.
- Consider edge cases such as empty list of words or same word for word1 and word2.

- Handling the case when word1 and word2 are the same word

- Using a nested loop to compare all pairs of words
    
### >> Comparison: 389 Find the Difference [Easy] *VS* 243 Shortest Word Distance [Easy]
> Similarity distance: 0.5685
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve string manipulation.
- Both questions require finding a difference or distance between elements.
##### Differences

- Question 389 involves finding the difference between two strings, while question 243 involves finding the shortest distance between two words in an array of words.
- Question 389 requires finding a single character difference, while question 243 requires finding the minimum distance between two words.
- Question 389 has a time complexity of O(n), while question 243 has a time complexity of O(n^2).
##### New Insights in 243 Shortest Word Distance [Easy]

- Question 389 teaches us how to compare two strings and find the differing character.
- Question 243 teaches us how to find the shortest distance between two words in an array of words.
- Both questions provide practice in string manipulation and problem-solving skills.


---
# 6. From 243 Shortest Word Distance [Easy] to 245 Shortest Word Distance III [Medium]
> Similarity Distance: 0.1559

### >> Reminder: 243 Shortest Word Distance [Easy]
Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.
##### Optimal Python solution:
```python
def shortestDistance(words, word1, word2):
    index1 = -1
    index2 = -1
    min_distance = float('inf')
    for i in range(len(words)):
        if words[i] == word1:
            index1 = i
        elif words[i] == word2:
            index2 = i
        if index1 != -1 and index2 != -1:
            min_distance = min(min_distance, abs(index1 - index2))
    return min_distance
```
Finding the shortest distance between two words in a list.
    
### >> 245 Shortest Word Distance III [Medium]
Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list. word1 and word2 may be the same and they represent two individual words in the list.
##### Sample input:
words = ["practice", "makes", "perfect", "coding", "makes"]
word1 = "makes"
word2 = "coding"
##### Sample output:
Output: 1

##### Questions to ask to clarify requirements:

- Can word1 and word2 be the same word?
- Can word1 and word2 appear multiple times in the list?

##### Optimal Python solution:
```python
def shortestWordDistance(words, word1, word2):
    min_distance = float('inf')
    index1 = -1
    index2 = -1
    for i in range(len(words)):
        if words[i] == word1:
            index1 = i
        if words[i] == word2:
            if word1 == word2:
                index1 = index2
            index2 = i
        if index1 != -1 and index2 != -1:
            min_distance = min(min_distance, abs(index1 - index2))
    return min_distance
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to keep track of the indices of word1 and word2
- Update the minimum distance whenever both pointers are valid

- Use meaningful variable names to improve code readability
- Handle special cases separately to avoid unnecessary checks

- Handling the case when word1 and word2 are the same word

- Using a nested loop to compare all pairs of words
    
### >> Comparison: 243 Shortest Word Distance [Easy] *VS* 245 Shortest Word Distance III [Medium]
> Similarity distance: 0.1559
##### Similarities

- Both questions involve finding the shortest distance between two words in an array of strings.
- Both questions have a time complexity of O(n).
##### Differences

- Question 243 only considers the distance between two different words, while question 245 considers the distance between two words, even if they are the same.
- Question 243 assumes that the two words are always present in the array, while question 245 handles the case when one or both words are not present.
- Question 243 returns the shortest distance as an integer, while question 245 returns -1 if the words are the same and the shortest distance if they are different.
##### New Insights in 245 Shortest Word Distance III [Medium]

- Question 245 introduces the concept of handling the case when the two words are the same.
- Question 245 demonstrates how to handle the case when one or both words are not present in the array.


---
# 7. From 243 Shortest Word Distance [Easy] to 244 Shortest Word Distance II [Medium]
> Similarity Distance: 0.2404

### >> Reminder: 243 Shortest Word Distance [Easy]
Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.
##### Optimal Python solution:
```python
def shortestDistance(words, word1, word2):
    index1 = -1
    index2 = -1
    min_distance = float('inf')
    for i in range(len(words)):
        if words[i] == word1:
            index1 = i
        elif words[i] == word2:
            index2 = i
        if index1 != -1 and index2 != -1:
            min_distance = min(min_distance, abs(index1 - index2))
    return min_distance
```
Finding the shortest distance between two words in a list.
    
### >> 244 Shortest Word Distance II [Medium]
Design a class which receives a list of words in the constructor, and implements a method that takes two words word1 and word2 and return the shortest distance between these two words in the list.
##### Sample input:
words = ["practice", "makes", "perfect", "coding", "makes"]
word1 = "coding"
word2 = "practice"
##### Sample output:
Output: 3

##### Questions to ask to clarify requirements:

- Can the list of words be empty?
- Can word1 and word2 be the same word?

##### Optimal Python solution:
```python
class WordDistance:
    def __init__(self, words):
        self.word_indices = {}
        for i, word in enumerate(words):
            if word in self.word_indices:
                self.word_indices[word].append(i)
            else:
                self.word_indices[word] = [i]

    def shortestDistance(self, word1, word2):
        indices1 = self.word_indices[word1]
        indices2 = self.word_indices[word2]
        min_distance = float('inf')
        i = 0
        j = 0
        while i < len(indices1) and j < len(indices2):
            min_distance = min(min_distance, abs(indices1[i] - indices2[j]))
            if indices1[i] < indices2[j]:
                i += 1
            else:
                j += 1
        return min_distance
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a dictionary to store the indices of each word
- Use two pointers to iterate through the indices of word1 and word2
- Update the minimum distance whenever both pointers are valid

- Use meaningful variable names to improve code readability.
- Consider edge cases such as empty list of words or same word for word1 and word2.
- Use a dictionary to optimize the solution by reducing the time complexity of searching for word indices.

- Handling the case when word1 and word2 are the same word

- Using a nested loop to compare all pairs of words
    
### >> Comparison: 243 Shortest Word Distance [Easy] *VS* 244 Shortest Word Distance II [Medium]
> Similarity distance: 0.2404
##### Similarities

- Both questions involve finding the shortest distance between two words in an array of strings.
##### Differences

- 243 Shortest Word Distance [Easy] only considers the distance between two different words, while 244 Shortest Word Distance II [Medium] allows for multiple occurrences of the same word.
- 244 Shortest Word Distance II [Medium] requires the shortest distance to be calculated multiple times, as the words can appear multiple times in the array.
##### New Insights in 244 Shortest Word Distance II [Medium]

- In both questions, a linear scan of the array is required to find the shortest distance.
- In 244 Shortest Word Distance II [Medium], we can optimize the solution by pre-processing the array and storing the indices of each word in a hashmap.

