
# Leetcode Intensive Tutorial Day 15 
> [Difficulty Score: 14]

> [Version: 20231225_200427]

## Courses overview of the day

- 1 Two Sum [Easy]
  - 220 Contains Duplicate III [Medium]
    - 219 Contains Duplicate II [Easy]
      - 599 Minimum Index Sum of Two Lists [Easy]
        - 454 4Sum II [Medium]
  - 387 First Unique Character in a String [Easy]
    - 187 Repeated DNA Sequences [Medium]
      - 347 Top K Frequent Elements [Medium]
    - 49 Group Anagrams [Medium]

#### Steps by steps

 - [1. From 1 Two Sum [Easy] to 220 Contains Duplicate III [Medium]](#1-from-1-two-sum-easy-to-220-contains-duplicate-iii-medium)

 - [2. From 220 Contains Duplicate III [Medium] to 219 Contains Duplicate II [Easy]](#2-from-220-contains-duplicate-iii-medium-to-219-contains-duplicate-ii-easy)

 - [3. From 219 Contains Duplicate II [Easy] to 599 Minimum Index Sum of Two Lists [Easy]](#3-from-219-contains-duplicate-ii-easy-to-599-minimum-index-sum-of-two-lists-easy)

 - [4. From 599 Minimum Index Sum of Two Lists [Easy] to 454 4Sum II [Medium]](#4-from-599-minimum-index-sum-of-two-lists-easy-to-454-4sum-ii-medium)

 - [5. From 1 Two Sum [Easy] to 387 First Unique Character in a String [Easy]](#5-from-1-two-sum-easy-to-387-first-unique-character-in-a-string-easy)

 - [6. From 387 First Unique Character in a String [Easy] to 187 Repeated DNA Sequences [Medium]](#6-from-387-first-unique-character-in-a-string-easy-to-187-repeated-dna-sequences-medium)

 - [7. From 187 Repeated DNA Sequences [Medium] to 347 Top K Frequent Elements [Medium]](#7-from-187-repeated-dna-sequences-medium-to-347-top-k-frequent-elements-medium)

 - [8. From 387 First Unique Character in a String [Easy] to 49 Group Anagrams [Medium]](#8-from-387-first-unique-character-in-a-string-easy-to-49-group-anagrams-medium)

#### Summary


- 1 Two Sum : Using a hash table to efficiently find the complement of each number.
- 454 4Sum II : The essence of this problem is to find the number of tuples such that the sum of elements from lists A, B, C, and D is zero.
- 219 Contains Duplicate II : Check if there are two distinct indices with the same number and a difference of at most k.
- 49 Group Anagrams : Group anagrams together by sorting each string and using a hash table.
- 599 Minimum Index Sum of Two Lists : Find the minimum index sum of a common element between two lists.
- 387 First Unique Character in a String : The essence of this problem is to efficiently find the first non-repeating character in a string.
- 187 Repeated DNA Sequences : The essence of this problem is to find repeated 10-letter sequences in a DNA molecule.
- 220 Contains Duplicate III : Check if there are two distinct indices with the absolute difference between their numbers at most t and the absolute difference between the indices at most k.
- 347 Top K Frequent Elements : Count the frequency of elements and find the k most frequent elements using a heap.
> Similarity Diameter of these problems: 0.7233


---
# 1. From 1 Two Sum [Easy] to 220 Contains Duplicate III [Medium]
> Similarity Distance: 0.4922

### >> 1 Two Sum [Easy]
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
##### Sample input:
[2,7,11,15]
9
##### Sample output:
[0,1]

##### Questions to ask to clarify requirements:
Are there always exactly one solution? Can the same element be used twice?

##### Optimal Python solution:
```python
def twoSum(nums, target):
    num_dict = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_dict:
            return [num_dict[complement], i]
        num_dict[num] = i
    return []
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a hash table to store the complement of each number
- Iterate through the array and check if the complement exists in the hash table
Use a dictionary to implement the hash table.
Handling the case when the same element is used twice
Brute force approach with nested loops
    
### >> 220 Contains Duplicate III [Medium]
Given an array of integers, find out whether there are two distinct indices i and j in the array such that the absolute difference between nums[i] and nums[j] is at most t and the absolute difference between i and j is at most k.
##### Sample input:
[1,2,3,1], 3, 0
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the maximum length of the array? Can the array contain negative numbers? What is the maximum absolute difference between two numbers?

##### Optimal Python solution:
```python
def containsNearbyAlmostDuplicate(nums, k, t):
    if t < 0:
        return False
    num_dict = {}
    bucket_size = t + 1
    for i, num in enumerate(nums):
        bucket = num // bucket_size
        if bucket in num_dict:
            return True
        if bucket - 1 in num_dict and abs(num - num_dict[bucket - 1]) <= t:
            return True
        if bucket + 1 in num_dict and abs(num - num_dict[bucket + 1]) <= t:
            return True
        num_dict[bucket] = num
        if i >= k:
            del num_dict[nums[i - k] // bucket_size]
    return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(min(n, k))
##### Notes:
Use a hash table to store the buckets of numbers. Iterate through the array and check if the current number falls into a bucket that already has a number. If it does, return True. If not, check the neighboring buckets to see if there is a number that satisfies the absolute difference condition. If no such pair is found, update the hash table with the current number. If the size of the hash table exceeds k, remove the oldest number from the hash table.
Use bucket sort to efficiently group numbers with similar values.
None
None
    
### >> Comparison: 1 Two Sum [Easy] *VS* 220 Contains Duplicate III [Medium]
> Similarity distance: 0.4922
##### Similarities

- Both Two Sum and Contains Duplicate III are LeetCode questions.
- Both questions involve manipulating arrays or lists.
- Both questions require finding certain patterns or relationships within the given data.
##### Differences

- Two Sum is classified as an Easy level question, while Contains Duplicate III is classified as a Medium level question.
- Two Sum requires finding two numbers that add up to a target value, while Contains Duplicate III requires finding if there are any two distinct indices i and j in the array such that the absolute difference between nums[i] and nums[j] is at most t and the absolute difference between i and j is at most k.
- Two Sum has a time complexity of O(n), while Contains Duplicate III has a time complexity of O(n log n).
##### New Insights in 220 Contains Duplicate III [Medium]

- From Two Sum, we can learn how to efficiently find two numbers that add up to a target value using a hash map.
- From Contains Duplicate III, we can learn how to efficiently find if there are any two distinct indices with specific absolute difference conditions using a balanced search tree.


---
# 2. From 220 Contains Duplicate III [Medium] to 219 Contains Duplicate II [Easy]
> Similarity Distance: 0.4156

### >> Reminder: 220 Contains Duplicate III [Medium]
Given an array of integers, find out whether there are two distinct indices i and j in the array such that the absolute difference between nums[i] and nums[j] is at most t and the absolute difference between i and j is at most k.
##### Optimal Python solution:
```python
def containsNearbyAlmostDuplicate(nums, k, t):
    if t < 0:
        return False
    num_dict = {}
    bucket_size = t + 1
    for i, num in enumerate(nums):
        bucket = num // bucket_size
        if bucket in num_dict:
            return True
        if bucket - 1 in num_dict and abs(num - num_dict[bucket - 1]) <= t:
            return True
        if bucket + 1 in num_dict and abs(num - num_dict[bucket + 1]) <= t:
            return True
        num_dict[bucket] = num
        if i >= k:
            del num_dict[nums[i - k] // bucket_size]
    return False
```
Check if there are two distinct indices with the absolute difference between their numbers at most t and the absolute difference between the indices at most k.
    
### >> 219 Contains Duplicate II [Easy]
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.
##### Sample input:
[1,2,3,1], 3
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the maximum length of the array? Can the array contain negative numbers?

##### Optimal Python solution:
```python
def containsNearbyDuplicate(nums, k):
    num_dict = {}
    for i, num in enumerate(nums):
        if num in num_dict and i - num_dict[num] <= k:
            return True
        num_dict[num] = i
    return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use a hash table to store the indices of each number. Iterate through the array and check if the current number is already in the hash table. If it is, check if the difference between the current index and the stored index is less than or equal to k. If it is, return True. If not, update the stored index with the current index. If no such pair is found, return False.
Use a hash table to efficiently store and retrieve the indices of each number.
None
None
    
### >> Comparison: 220 Contains Duplicate III [Medium] *VS* 219 Contains Duplicate II [Easy]
> Similarity distance: 0.4156
##### Similarities

- Both questions are related to finding duplicates in an array.
- Both questions have a constraint on the indices of the duplicates.
##### Differences

- Question 220 allows a maximum difference of k between the indices of the duplicates.
- Question 219 allows a maximum difference of 1 between the indices of the duplicates.
##### New Insights in 219 Contains Duplicate II [Easy]

- Question 220 introduces a new constraint on the difference between the values of the duplicates.
- Question 220 requires the absolute difference between the values to be less than or equal to t.


---
# 3. From 219 Contains Duplicate II [Easy] to 599 Minimum Index Sum of Two Lists [Easy]
> Similarity Distance: 0.5054

### >> Reminder: 219 Contains Duplicate II [Easy]
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.
##### Optimal Python solution:
```python
def containsNearbyDuplicate(nums, k):
    num_dict = {}
    for i, num in enumerate(nums):
        if num in num_dict and i - num_dict[num] <= k:
            return True
        num_dict[num] = i
    return False
```
Check if there are two distinct indices with the same number and a difference of at most k.
    
### >> 599 Minimum Index Sum of Two Lists [Easy]
You are given two lists of strings `list1` and `list2` of equal length. Find the minimum index sum of a common element between the two lists. If there are multiple common elements, return the one with the smallest index sum. If there are no common elements, return an empty list.
##### Sample input:

- ["Shogun","Tapioca Express","Burger King","KFC"]
- ["Piatti","The Grill at Torrey Pines","Hungry Hunter Steakhouse","Shogun"]
##### Sample output:
["Shogun"]

##### Questions to ask to clarify requirements:

- Can the lists contain duplicate elements?
- Can the lists be empty?
- What should be returned if there are no common elements?

##### Optimal Python solution:
```python

- def findRestaurant(list1, list2):
-     index_sum = float('inf')
-     common = []
-     for i, r in enumerate(list1):
-         if r in list2:
-             if i + list2.index(r) < index_sum:
-                 index_sum = i + list2.index(r)
-                 common = [r]
-             elif i + list2.index(r) == index_sum:
-                 common.append(r)
-     return common
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a hash table to store the elements of list1 and their indices
- Iterate through list2 and check if each element is in the hash table
- Calculate the index sum for each common element and keep track of the minimum index sum
- Return the common element(s) with the minimum index sum
N/A
N/A
N/A
    
### >> Comparison: 219 Contains Duplicate II [Easy] *VS* 599 Minimum Index Sum of Two Lists [Easy]
> Similarity distance: 0.5054
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve finding duplicates or similarities in a list of elements.
- Both questions require iterating through the list and keeping track of indices or positions.
##### Differences

- Question 219 focuses on finding duplicates with a specific distance constraint, while question 599 focuses on finding common elements with the minimum sum of indices.
- Question 219 requires checking if there are any duplicates within a given distance, while question 599 requires finding the common elements with the smallest sum of indices.
- Question 219 uses a sliding window approach to efficiently solve the problem, while question 599 uses a hash map to store the indices of elements in one list.
##### New Insights in 599 Minimum Index Sum of Two Lists [Easy]

- Question 219 introduces the concept of using a sliding window to efficiently solve problems involving duplicates within a distance constraint.
- Question 599 introduces the concept of using a hash map to store indices and efficiently find common elements with the minimum sum of indices.


---
# 4. From 599 Minimum Index Sum of Two Lists [Easy] to 454 4Sum II [Medium]
> Similarity Distance: 0.4903

### >> Reminder: 599 Minimum Index Sum of Two Lists [Easy]
You are given two lists of strings `list1` and `list2` of equal length. Find the minimum index sum of a common element between the two lists. If there are multiple common elements, return the one with the smallest index sum. If there are no common elements, return an empty list.
##### Optimal Python solution:
```python

- def findRestaurant(list1, list2):
-     index_sum = float('inf')
-     common = []
-     for i, r in enumerate(list1):
-         if r in list2:
-             if i + list2.index(r) < index_sum:
-                 index_sum = i + list2.index(r)
-                 common = [r]
-             elif i + list2.index(r) == index_sum:
-                 common.append(r)
-     return common
```
Find the minimum index sum of a common element between two lists.
    
### >> 454 4Sum II [Medium]
Given four lists A, B, C, D of integer values, compute how many tuples (i, j, k, l) there are such that A[i] + B[j] + C[k] + D[l] is zero.
##### Sample input:
[1,2]
[-2,-1]
[-1,2]
[0,2]
##### Sample output:
2

##### Questions to ask to clarify requirements:
Can the lists contain duplicate values? Can the tuples contain duplicate elements?

##### Optimal Python solution:
```python
def fourSumCount(A, B, C, D):
    count = 0
    sum_dict = {}
    for a in A:
        for b in B:
            if a + b in sum_dict:
                sum_dict[a + b] += 1
            else:
                sum_dict[a + b] = 1
    for c in C:
        for d in D:
            if -c - d in sum_dict:
                count += sum_dict[-c - d]
    return count
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:
Use a hash table to store the sums of pairs from lists A and B. Then, iterate through lists C and D and check if the negative of the sum is in the hash table.
Use a hash table to store the sums of pairs from lists A and B.
None
None
    
### >> Comparison: 599 Minimum Index Sum of Two Lists [Easy] *VS* 454 4Sum II [Medium]
> Similarity distance: 0.4903
##### Similarities

- Both questions involve finding the sum of elements from multiple lists.
- Both questions require finding combinations of elements that satisfy a certain condition.
##### Differences

- Minimum Index Sum of Two Lists involves finding the minimum index sum of elements from two lists.
- 4Sum II involves finding the number of quadruplets that sum to zero from four lists.
- Minimum Index Sum of Two Lists is an easy level question, while 4Sum II is a medium level question.
##### New Insights in 454 4Sum II [Medium]

- Minimum Index Sum of Two Lists teaches us how to find the minimum index sum of elements efficiently.
- 4Sum II teaches us how to find the number of quadruplets that sum to zero efficiently.


---
# 5. From 1 Two Sum [Easy] to 387 First Unique Character in a String [Easy]
> Similarity Distance: 0.5678

### >> Reminder: 1 Two Sum [Easy]
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
##### Optimal Python solution:
```python
def twoSum(nums, target):
    num_dict = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_dict:
            return [num_dict[complement], i]
        num_dict[num] = i
    return []
```
Using a hash table to efficiently find the complement of each number.
    
### >> 387 First Unique Character in a String [Easy]
Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.
##### Sample input:
"leetcode"
##### Sample output:
0

##### Questions to ask to clarify requirements:
Can the string contain uppercase and lowercase letters? Can it contain special characters or spaces?

##### Optimal Python solution:
```python
def firstUniqChar(s):
    count = collections.Counter(s)
    for i in range(len(s)):
        if count[s[i]] == 1:
            return i
    return -1
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use a hash table to count the occurrences of each character. Iterate through the string and return the index of the first character with count 1.
Use the collections.Counter() function to count the occurrences of each character in the string.
None
None
    
### >> Comparison: 1 Two Sum [Easy] *VS* 387 First Unique Character in a String [Easy]
> Similarity distance: 0.5678
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating arrays or strings.
- Both questions require finding a specific element or character in the given input.
- Both questions have a time complexity of O(n).
##### Differences

- Two Sum involves finding two numbers in the array that add up to the target, while First Unique Character in a String involves finding the first non-repeating character in the string.
- Two Sum allows the use of any element in the array multiple times to achieve the target sum, while First Unique Character in a String considers each character only once.
- Two Sum requires returning the indices of the two numbers that add up to the target, while First Unique Character in a String requires returning the index of the first unique character.
- Two Sum can have multiple valid solutions, while First Unique Character in a String has only one valid solution.
##### New Insights in 387 First Unique Character in a String [Easy]

- From Two Sum, we can learn how to efficiently use a hash map to store the complement of each element in the array.
- From First Unique Character in a String, we can learn how to use an array or hash map to count the occurrences of each character in the string and find the first character with a count of 1.


---
# 6. From 387 First Unique Character in a String [Easy] to 187 Repeated DNA Sequences [Medium]
> Similarity Distance: 0.4598

### >> Reminder: 387 First Unique Character in a String [Easy]
Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.
##### Optimal Python solution:
```python
def firstUniqChar(s):
    count = collections.Counter(s)
    for i in range(len(s)):
        if count[s[i]] == 1:
            return i
    return -1
```
The essence of this problem is to efficiently find the first non-repeating character in a string.
    
### >> 187 Repeated DNA Sequences [Medium]
All DNA is composed of a series of nucleotides abbreviated as 'A', 'C', 'G', and 'T'. Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.
##### Sample input:
"AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"
##### Sample output:
["AAAAACCCCC", "CCCCCAAAAA"]

##### Questions to ask to clarify requirements:
1. Can the DNA molecule contain other characters besides 'A', 'C', 'G', and 'T'? 2. Should the output be sorted? 3. Can the input string be empty?

##### Optimal Python solution:
```python
class Solution:
    def findRepeatedDnaSequences(self, s: str) -> List[str]:
        sequences = {}
        for i in range(len(s) - 9):
            sequence = s[i:i+10]
            sequences[sequence] = sequences.get(sequence, 0) + 1
        return [sequence for sequence, count in sequences.items() if count > 1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a hash table to store the count of each 10-letter sequence. 2. Return the sequences that occur more than once.
1. Use a hash table to efficiently store and retrieve the count of each sequence. 2. Use a sliding window approach to iterate through the input string.
None
None
    
### >> Comparison: 387 First Unique Character in a String [Easy] *VS* 187 Repeated DNA Sequences [Medium]
> Similarity distance: 0.4598
##### Similarities

- Both questions involve processing a string
- Both questions require finding unique or repeated elements in the string
##### Differences

- 387 First Unique Character in a String [Easy] requires finding the first unique character in the string
- 187 Repeated DNA Sequences [Medium] requires finding all the repeated DNA sequences of length 10 in the string
##### New Insights in 187 Repeated DNA Sequences [Medium]

- 387 First Unique Character in a String [Easy] teaches us how to efficiently find the first unique character using a hashmap
- 187 Repeated DNA Sequences [Medium] teaches us how to efficiently find repeated sequences using a sliding window and a hashmap


---
# 7. From 187 Repeated DNA Sequences [Medium] to 347 Top K Frequent Elements [Medium]
> Similarity Distance: 0.5595

### >> Reminder: 187 Repeated DNA Sequences [Medium]
All DNA is composed of a series of nucleotides abbreviated as 'A', 'C', 'G', and 'T'. Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.
##### Optimal Python solution:
```python
class Solution:
    def findRepeatedDnaSequences(self, s: str) -> List[str]:
        sequences = {}
        for i in range(len(s) - 9):
            sequence = s[i:i+10]
            sequences[sequence] = sequences.get(sequence, 0) + 1
        return [sequence for sequence, count in sequences.items() if count > 1]
```
The essence of this problem is to find repeated 10-letter sequences in a DNA molecule.
    
### >> 347 Top K Frequent Elements [Medium]
Given a non-empty array of integers, return the k most frequent elements.
##### Sample input:
[1,1,1,2,2,3]
##### Sample output:
[1,2]

##### Questions to ask to clarify requirements:
What should be returned if there are multiple elements with the same frequency?

##### Optimal Python solution:
```python
def topKFrequent(nums, k):
    count = collections.Counter(nums)
    return [num for num, _ in count.most_common(k)]
```
##### Time complexity:
O(n log k)
##### Space complexity:
O(n)
##### Notes:
Use a hash table to count the frequency of each element. Use a heap to keep track of the k most frequent elements.
Use the Counter class in Python to count the frequency of elements in an array.
Using a heap to keep track of the k most frequent elements.
Sorting the entire array.
    
### >> Comparison: 187 Repeated DNA Sequences [Medium] *VS* 347 Top K Frequent Elements [Medium]
> Similarity distance: 0.5595
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating sequences of elements.
- Both questions require finding patterns or frequencies in the given data.
##### Differences

- Question 187 focuses on finding repeated DNA sequences, while question 347 focuses on finding the top k frequent elements.
- Question 187 deals with DNA sequences, which consist of characters 'A', 'C', 'G', and 'T', while question 347 deals with any type of elements.
- Question 187 requires finding sequences of length 10, while question 347 requires finding the top k frequent elements.
- Question 187 has a time complexity of O(N), where N is the length of the input string, while question 347 has a time complexity of O(N log k), where N is the number of elements and k is the given value.
##### New Insights in 347 Top K Frequent Elements [Medium]

- Question 187 introduces the concept of finding repeated patterns in DNA sequences, which can be useful in genetic research and analysis.
- Question 347 introduces the concept of finding the top k frequent elements, which can be applied in various scenarios such as analyzing user behavior or identifying popular items.


---
# 8. From 387 First Unique Character in a String [Easy] to 49 Group Anagrams [Medium]
> Similarity Distance: 0.5431

### >> Reminder: 387 First Unique Character in a String [Easy]
Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.
##### Optimal Python solution:
```python
def firstUniqChar(s):
    count = collections.Counter(s)
    for i in range(len(s)):
        if count[s[i]] == 1:
            return i
    return -1
```
The essence of this problem is to efficiently find the first non-repeating character in a string.
    
### >> 49 Group Anagrams [Medium]
Given an array of strings, group anagrams together.
##### Sample input:
["eat","tea","tan","ate","nat","bat"]
##### Sample output:
[["bat"],["nat","tan"],["ate","eat","tea"]]

##### Questions to ask to clarify requirements:

- Can the input array be empty?
- Can the strings in the array be empty?
- Are the strings case-sensitive?

##### Optimal Python solution:
```python
def groupAnagrams(strs):
    anagrams = {}
    for s in strs:
        sorted_s = ''.join(sorted(s))
        if sorted_s in anagrams:
            anagrams[sorted_s].append(s)
        else:
            anagrams[sorted_s] = [s]
    return list(anagrams.values())
```
##### Time complexity:
O(n * k log k)
##### Space complexity:
O(n * k)
##### Notes:

- Use a hash table to group anagrams
- Sort each string and use it as a key in the hash table

- Use the sorted string as a key in the hash table to group anagrams.
- Handle empty input array or empty strings as special cases.

- Using the sorted string as a key in the hash table

- Comparing each string with every other string in the array
    
### >> Comparison: 387 First Unique Character in a String [Easy] *VS* 49 Group Anagrams [Medium]
> Similarity distance: 0.5431
##### Similarities

- Both questions involve manipulating strings.
- Both questions require counting or grouping characters in a string.
##### Differences

- Question 387 focuses on finding the first unique character in a string, while question 49 focuses on grouping anagrams.
- Question 387 has a complexity of O(n), while question 49 has a complexity of O(nk log k), where n is the number of strings and k is the maximum length of a string.
##### New Insights in 49 Group Anagrams [Medium]

- Question 387 teaches us how to efficiently find the first unique character in a string using a hashmap.
- Question 49 teaches us how to group anagrams by sorting the characters in each string and using a hashmap.

