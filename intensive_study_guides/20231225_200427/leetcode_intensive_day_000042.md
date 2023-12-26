
# Leetcode Intensive Tutorial Day 42 
> [Difficulty Score: 22]

> [Version: 20231225_200427]

## Courses overview of the day

- 204 Count Primes [Easy]
  - 532 K-diff Pairs in an Array [Medium]
    - 315 Count of Smaller Numbers After Self [Hard]
      - 75 Sort Colors [Medium]
    - 350 Intersection of Two Arrays II [Easy]
      - 349 Intersection of Two Arrays [Easy]
    - 172 Factorial Trailing Zeroes [Easy]
    - 163 Missing Ranges [Medium]
      - 41 First Missing Positive [Hard]
    - 327 Count of Range Sum [Hard]

#### Steps by steps

 - [1. From 204 Count Primes [Easy] to 532 K-diff Pairs in an Array [Medium]](#1-from-204-count-primes-easy-to-532-k-diff-pairs-in-an-array-medium)

 - [2. From 532 K-diff Pairs in an Array [Medium] to 315 Count of Smaller Numbers After Self [Hard]](#2-from-532-k-diff-pairs-in-an-array-medium-to-315-count-of-smaller-numbers-after-self-hard)

 - [3. From 315 Count of Smaller Numbers After Self [Hard] to 75 Sort Colors [Medium]](#3-from-315-count-of-smaller-numbers-after-self-hard-to-75-sort-colors-medium)

 - [4. From 532 K-diff Pairs in an Array [Medium] to 350 Intersection of Two Arrays II [Easy]](#4-from-532-k-diff-pairs-in-an-array-medium-to-350-intersection-of-two-arrays-ii-easy)

 - [5. From 350 Intersection of Two Arrays II [Easy] to 349 Intersection of Two Arrays [Easy]](#5-from-350-intersection-of-two-arrays-ii-easy-to-349-intersection-of-two-arrays-easy)

 - [6. From 532 K-diff Pairs in an Array [Medium] to 172 Factorial Trailing Zeroes [Easy]](#6-from-532-k-diff-pairs-in-an-array-medium-to-172-factorial-trailing-zeroes-easy)

 - [7. From 532 K-diff Pairs in an Array [Medium] to 163 Missing Ranges [Medium]](#7-from-532-k-diff-pairs-in-an-array-medium-to-163-missing-ranges-medium)

 - [8. From 163 Missing Ranges [Medium] to 41 First Missing Positive [Hard]](#8-from-163-missing-ranges-medium-to-41-first-missing-positive-hard)

 - [9. From 532 K-diff Pairs in an Array [Medium] to 327 Count of Range Sum [Hard]](#9-from-532-k-diff-pairs-in-an-array-medium-to-327-count-of-range-sum-hard)

#### Summary


- 315 Count of Smaller Numbers After Self : Count the number of smaller elements to the right of each element in an array.
- 204 Count Primes : Counting prime numbers less than a given number.
- 532 K-diff Pairs in an Array : Finding the number of unique k-diff pairs in an array
- 350 Intersection of Two Arrays II : Finding the intersection of two arrays using counters.
- 163 Missing Ranges : Iterate through the array and check for missing ranges. Format the ranges using a helper function. Handle edge cases where the lower and upper bounds are included in the missing ranges.
- 172 Factorial Trailing Zeroes : Count the number of factors of 5 in the range [1, n].
- 75 Sort Colors : Sort the objects in the input array in-place based on their colors.
- 349 Intersection of Two Arrays : Finding the intersection of two arrays using sets.
- 327 Count of Range Sum : The essence of the problem is to count the number of range sums that lie in the given range using divide and conquer, merge sort, and binary search.
- 41 First Missing Positive : Using the array itself to store information and swapping elements to their correct positions.
> Similarity Diameter of these problems: 0.6648


---
# 1. From 204 Count Primes [Easy] to 532 K-diff Pairs in an Array [Medium]
> Similarity Distance: 0.5099

### >> 204 Count Primes [Easy]
Count the number of prime numbers less than a non-negative number, n.
##### Sample input:
n = 10
##### Sample output:
4

##### Questions to ask to clarify requirements:
Is the input number inclusive or exclusive?

##### Optimal Python solution:
```python
def countPrimes(n):
    if n < 3:
        return 0
    primes = [True] * n
    primes[0] = primes[1] = False
    for i in range(2, int(n ** 0.5) + 1):
        if primes[i]:
            primes[i*i:n:i] = [False] * len(primes[i*i:n:i])
    return sum(primes)
```
##### Time complexity:
O(n log log n)
##### Space complexity:
O(n)
##### Notes:
1. Use the sieve of Eratosthenes algorithm to find prime numbers.
2. Initialize a boolean list to track prime numbers.
3. Iterate through the list and mark non-prime numbers.
4. Count the number of prime numbers.
1. Initialize the boolean list with all True values.
2. Use slicing to mark non-prime numbers.
3. Sum the boolean list to count prime numbers.
1. Handling the edge case of n < 3.
2. Optimizing the sieve of Eratosthenes algorithm.
1. Checking each number for primality individually.
2. Using a brute force approach to count prime numbers.
    
### >> 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Sample input:

- [3, 1, 4, 1, 5],
- 2
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can the array contain negative numbers?
- Can the array contain duplicates?
- Should the solution consider pairs with negative difference?

##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Count the occurrences of each number in the array
- Check if the number plus k exists in the array

- Use a dictionary to count occurrences
- Optimize the solution by avoiding unnecessary iterations

- Use a dictionary to count the occurrences of each number
- Handle the case when k is 0 separately

- Using a brute force approach to find pairs
    
### >> Comparison: 204 Count Primes [Easy] *VS* 532 K-diff Pairs in an Array [Medium]
> Similarity distance: 0.5099
##### Similarities

- Both questions involve manipulating an array of numbers.
- Both questions require counting or finding pairs of numbers.
- Both questions have a time complexity of O(n^2).
##### Differences

- Question 204 involves counting prime numbers in the array, while question 532 involves finding pairs with a specific difference.
- Question 204 has a time complexity of O(n log log n), while question 532 has a time complexity of O(n).
- Question 204 requires checking if a number is prime, while question 532 requires checking if a pair has a specific difference.
##### New Insights in 532 K-diff Pairs in an Array [Medium]

- Question 204 teaches us how to efficiently count prime numbers using the Sieve of Eratosthenes algorithm.
- Question 532 teaches us how to use a hash set to efficiently find pairs with a specific difference.


---
# 2. From 532 K-diff Pairs in an Array [Medium] to 315 Count of Smaller Numbers After Self [Hard]
> Similarity Distance: 0.4404

### >> Reminder: 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
Finding the number of unique k-diff pairs in an array
    
### >> 315 Count of Smaller Numbers After Self [Hard]
You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].
##### Sample input:
[5,2,6,1]
##### Sample output:
[2,1,1,0]

##### Questions to ask to clarify requirements:

- What is the range of the input array?
- Can the input array contain duplicates?
- What is the maximum length of the input array?

##### Optimal Python solution:
```python
def countSmaller(nums):
    counts = [0] * len(nums)
    sorted_nums = []
    for num in reversed(nums):
        index = bisect_left(sorted_nums, num)
        counts.append(index)
        sorted_nums.insert(index, num)
    return counts[::-1]
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:

- Use a sorted list to keep track of the numbers encountered so far.
- Count the number of elements smaller than the current element using binary search.
- Insert the current element at the correct position in the sorted list.

- Reversing the input array allows counting the elements to the right.
- Using a sorted list and binary search improves the time complexity.

- Using a sorted list and binary search to count the number of smaller elements.
- Reversing the input array to count the elements to the right.

- Using a nested loop to compare each element with the elements to its right.
    
### >> Comparison: 532 K-diff Pairs in an Array [Medium] *VS* 315 Count of Smaller Numbers After Self [Hard]
> Similarity distance: 0.4404
##### Similarities

- Both questions involve manipulating an array of numbers.
- Both questions require counting or finding pairs of numbers that meet certain conditions.
##### Differences

- 532 K-diff Pairs in an Array focuses on finding pairs of numbers with a specific difference, while 315 Count of Smaller Numbers After Self focuses on counting the number of smaller elements after each element in the array.
- 532 K-diff Pairs in an Array has a complexity requirement of O(n), while 315 Count of Smaller Numbers After Self does not have a specific complexity requirement.
- 532 K-diff Pairs in an Array has a medium difficulty level, while 315 Count of Smaller Numbers After Self has a hard difficulty level.
##### New Insights in 315 Count of Smaller Numbers After Self [Hard]

- From 532 K-diff Pairs in an Array, we can learn how to efficiently find pairs of numbers with a specific difference using a hash map.
- From 315 Count of Smaller Numbers After Self, we can learn how to use the merge sort algorithm to count the number of smaller elements after each element in the array.


---
# 3. From 315 Count of Smaller Numbers After Self [Hard] to 75 Sort Colors [Medium]
> Similarity Distance: 0.5292

### >> Reminder: 315 Count of Smaller Numbers After Self [Hard]
You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].
##### Optimal Python solution:
```python
def countSmaller(nums):
    counts = [0] * len(nums)
    sorted_nums = []
    for num in reversed(nums):
        index = bisect_left(sorted_nums, num)
        counts.append(index)
        sorted_nums.insert(index, num)
    return counts[::-1]
```
Count the number of smaller elements to the right of each element in an array.
    
### >> 75 Sort Colors [Medium]
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
##### Sample input:
[2,0,2,1,1,0]
##### Sample output:
[0,0,1,1,2,2]

##### Questions to ask to clarify requirements:

- Can we use extra space?
- Can we assume the input array only contains the colors red, white, and blue?

##### Optimal Python solution:
```python
def sortColors(nums):
    counts = [0, 0, 0]
    for num in nums:
        counts[num] += 1
    for i in range(len(nums)):
        if i < counts[0]:
            nums[i] = 0
        elif i < counts[0] + counts[1]:
            nums[i] = 1
        else:
            nums[i] = 2
    return nums
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use counting sort to count the number of red, white, and blue objects
- Modify the input array in-place based on the counts

- Use two pointers to keep track of the boundaries between the red, white, and blue objects

- Handling the indices correctly when modifying the input array in-place

- Using a sorting algorithm with higher time complexity
    
### >> Comparison: 315 Count of Smaller Numbers After Self [Hard] *VS* 75 Sort Colors [Medium]
> Similarity distance: 0.5292
##### Similarities

- Both questions involve sorting elements in an array.
- Both questions require counting or tracking certain elements in the array.
- Both questions have a time complexity requirement of O(n).
##### Differences

- 315 Count of Smaller Numbers After Self focuses on counting the number of smaller elements to the right of each element in the array.
- 75 Sort Colors focuses on sorting an array of 0s, 1s, and 2s in-place.
- 315 Count of Smaller Numbers After Self requires the use of a modified merge sort algorithm.
- 75 Sort Colors can be solved using a two-pointer approach.
##### New Insights in 75 Sort Colors [Medium]

- 315 Count of Smaller Numbers After Self introduces the concept of using a modified merge sort algorithm to solve counting problems efficiently.
- 75 Sort Colors introduces the concept of using a two-pointer approach to sort elements in-place.


---
# 4. From 532 K-diff Pairs in an Array [Medium] to 350 Intersection of Two Arrays II [Easy]
> Similarity Distance: 0.4675

### >> Reminder: 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
Finding the number of unique k-diff pairs in an array
    
### >> 350 Intersection of Two Arrays II [Easy]
Given two arrays, write a function to compute their intersection.
##### Sample input:
[1,2,2,1]
[2,2]
##### Sample output:
[2,2]

##### Questions to ask to clarify requirements:
Are the arrays sorted?

##### Optimal Python solution:
```python
def intersect(nums1, nums2):
    counter1 = collections.Counter(nums1)
    counter2 = collections.Counter(nums2)
    return list((counter1 & counter2).elements())
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use counters to find the intersection of two arrays.
Use the & operator to find the intersection of two counters.
None
None
    
### >> Comparison: 532 K-diff Pairs in an Array [Medium] *VS* 350 Intersection of Two Arrays II [Easy]
> Similarity distance: 0.4675
##### Similarities

- Both questions involve finding pairs or intersections in arrays.
- Both questions have a time complexity of O(n).
##### Differences

- 532 K-diff Pairs in an Array focuses on finding pairs with a specific difference, while 350 Intersection of Two Arrays II focuses on finding common elements in two arrays.
- 532 K-diff Pairs in an Array allows duplicate elements in the array, while 350 Intersection of Two Arrays II does not.
- 532 K-diff Pairs in an Array requires the pairs to have a non-negative difference, while 350 Intersection of Two Arrays II does not have such a requirement.
##### New Insights in 350 Intersection of Two Arrays II [Easy]

- 532 K-diff Pairs in an Array introduces the concept of finding pairs with a specific difference, which can be useful in various scenarios.
- 350 Intersection of Two Arrays II introduces the concept of finding common elements in two arrays efficiently using a hash map.


---
# 5. From 350 Intersection of Two Arrays II [Easy] to 349 Intersection of Two Arrays [Easy]
> Similarity Distance: 0.2965

### >> Reminder: 350 Intersection of Two Arrays II [Easy]
Given two arrays, write a function to compute their intersection.
##### Optimal Python solution:
```python
def intersect(nums1, nums2):
    counter1 = collections.Counter(nums1)
    counter2 = collections.Counter(nums2)
    return list((counter1 & counter2).elements())
```
Finding the intersection of two arrays using counters.
    
### >> 349 Intersection of Two Arrays [Easy]
Given two arrays, write a function to compute their intersection.
##### Sample input:
[1,2,2,1]
[2,2]
##### Sample output:
[2]

##### Questions to ask to clarify requirements:
Are the arrays sorted?

##### Optimal Python solution:
```python
def intersection(nums1, nums2):
    set1 = set(nums1)
    set2 = set(nums2)
    return list(set1 & set2)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use sets to find the intersection of two arrays.
Use the & operator to find the intersection of two sets.
None
None
    
### >> Comparison: 350 Intersection of Two Arrays II [Easy] *VS* 349 Intersection of Two Arrays [Easy]
> Similarity distance: 0.2965
##### Similarities

- Both questions are about finding the intersection of two arrays.
- Both questions have an easy difficulty level.
##### Differences

- Question 350 allows duplicate elements in the intersection, while question 349 does not.
- Question 350 requires returning the intersection as an array, while question 349 requires returning a boolean value indicating if the arrays have any common elements.
##### New Insights in 349 Intersection of Two Arrays [Easy]

- Question 350 can be solved using a hash map to count the occurrences of each element in one array, and then iterating through the other array to find the common elements.
- Question 349 can be solved using two pointers to iterate through the arrays and compare the elements.


---
# 6. From 532 K-diff Pairs in an Array [Medium] to 172 Factorial Trailing Zeroes [Easy]
> Similarity Distance: 0.4723

### >> Reminder: 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
Finding the number of unique k-diff pairs in an array
    
### >> 172 Factorial Trailing Zeroes [Easy]
Given an integer n, return the number of trailing zeroes in n!.
##### Sample input:
3
5
0
10
30
50
##### Sample output:
0
1
0
2
7
12

##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        count = 0
        while n > 0:
            n = n // 5
            count += n
        return count
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
Count the number of factors of 5 in the range [1, n].
Use integer division to calculate the number of factors of 5.
None
None
    
### >> Comparison: 532 K-diff Pairs in an Array [Medium] *VS* 172 Factorial Trailing Zeroes [Easy]
> Similarity distance: 0.4723
##### Similarities

- Both questions are related to arrays and require some form of counting or comparison.
- Both questions have a time complexity of O(n).
##### Differences

- 532 K-diff Pairs in an Array focuses on finding the number of unique k-diff pairs in an array.
- 172 Factorial Trailing Zeroes focuses on finding the number of trailing zeroes in the factorial of a given number.
- 532 K-diff Pairs in an Array requires using a hash map to efficiently count the pairs.
- 172 Factorial Trailing Zeroes requires understanding the concept of trailing zeroes in factorials and using mathematical calculations.
##### New Insights in 172 Factorial Trailing Zeroes [Easy]

- 532 K-diff Pairs in an Array teaches us how to efficiently count pairs using a hash map.
- 172 Factorial Trailing Zeroes teaches us the concept of trailing zeroes in factorials and how to calculate them.


---
# 7. From 532 K-diff Pairs in an Array [Medium] to 163 Missing Ranges [Medium]
> Similarity Distance: 0.4961

### >> Reminder: 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
Finding the number of unique k-diff pairs in an array
    
### >> 163 Missing Ranges [Medium]
Given a sorted integer array nums, where the range of elements are in the inclusive range [lower, upper], return its missing ranges.
##### Sample input:
[0, 1, 3, 50, 75], lower = 0, upper = 99
##### Sample output:
["2", "4->49", "51->74", "76->99"]

##### Questions to ask to clarify requirements:

- Can the input array be empty?
- Can the lower and upper bounds be negative?
- Can the lower and upper bounds be the same number?

##### Optimal Python solution:
```python
def findMissingRanges(nums, lower, upper):
    def formatRange(lower, upper):
        if lower == upper:
            return str(lower)
        else:
            return str(lower) + "->" + str(upper)
    result = []
    prev = lower - 1
    for i in range(len(nums) + 1):
        curr = nums[i] if i < len(nums) else upper + 1
        if prev + 1 <= curr - 1:
            result.append(formatRange(prev + 1, curr - 1))
        prev = curr
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Iterate through the array and check for missing ranges
- Use a helper function to format the ranges
- Handle edge cases where the lower and upper bounds are included in the missing ranges

- Use a helper function to format the ranges
- Handle edge cases where the lower and upper bounds are included in the missing ranges

- Handling edge cases where the lower and upper bounds are included in the missing ranges

- Using extra space
    
### >> Comparison: 532 K-diff Pairs in an Array [Medium] *VS* 163 Missing Ranges [Medium]
> Similarity distance: 0.4961
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating an array of numbers.
- Both questions require finding certain patterns or ranges within the array.
##### Differences

- 532 K-diff Pairs in an Array involves finding the number of unique k-diff pairs in the array.
- 163 Missing Ranges involves finding the missing ranges in a given range and array of numbers.
##### New Insights in 163 Missing Ranges [Medium]

- 532 K-diff Pairs in an Array teaches us how to efficiently count unique pairs using a hashmap.
- 163 Missing Ranges teaches us how to handle edge cases and generate missing ranges in a concise manner.


---
# 8. From 163 Missing Ranges [Medium] to 41 First Missing Positive [Hard]
> Similarity Distance: 0.5265

### >> Reminder: 163 Missing Ranges [Medium]
Given a sorted integer array nums, where the range of elements are in the inclusive range [lower, upper], return its missing ranges.
##### Optimal Python solution:
```python
def findMissingRanges(nums, lower, upper):
    def formatRange(lower, upper):
        if lower == upper:
            return str(lower)
        else:
            return str(lower) + "->" + str(upper)
    result = []
    prev = lower - 1
    for i in range(len(nums) + 1):
        curr = nums[i] if i < len(nums) else upper + 1
        if prev + 1 <= curr - 1:
            result.append(formatRange(prev + 1, curr - 1))
        prev = curr
    return result
```
Iterate through the array and check for missing ranges. Format the ranges using a helper function. Handle edge cases where the lower and upper bounds are included in the missing ranges.
    
### >> 41 First Missing Positive [Hard]
Given an unsorted integer array nums, find the smallest missing positive integer.
##### Sample input:
[1,2,0]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- What should be the time complexity of the solution?
- What should be the space complexity of the solution?

##### Optimal Python solution:
```python
def firstMissingPositive(nums):
    n = len(nums)
    for i in range(n):
        while 0 < nums[i] <= n and nums[nums[i] - 1] != nums[i]:
            nums[nums[i] - 1], nums[i] = nums[i], nums[nums[i] - 1]
    for i in range(n):
        if nums[i] != i + 1:
            return i + 1
    return n + 1
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use the array itself to store the information about the missing positive integers.
- Swap elements to their correct positions.
- Return the first missing positive integer.

- Understand the swapping technique.
- Handle edge cases such as negative numbers and empty arrays.

- Swapping elements in the array to their correct positions.

- Using extra space.
- Sorting the array.
    
### >> Comparison: 163 Missing Ranges [Medium] *VS* 41 First Missing Positive [Hard]
> Similarity distance: 0.5265
##### Similarities

- Both questions involve finding missing elements in a given range.
- Both questions require iterating through an array of numbers.
##### Differences

- 163 Missing Ranges focuses on finding missing ranges within a given range, while 41 First Missing Positive focuses on finding the first missing positive integer in an array.
- 163 Missing Ranges allows missing ranges to be inclusive or exclusive, while 41 First Missing Positive only considers positive integers.
- 163 Missing Ranges has a complexity of O(n), while 41 First Missing Positive has a complexity of O(n) as well but with additional space complexity of O(1).
##### New Insights in 41 First Missing Positive [Hard]

- From 163 Missing Ranges, we can learn how to handle missing ranges within a given range efficiently.
- From 41 First Missing Positive, we can learn how to find the first missing positive integer in an array using constant space.


---
# 9. From 532 K-diff Pairs in an Array [Medium] to 327 Count of Range Sum [Hard]
> Similarity Distance: 0.5058

### >> Reminder: 532 K-diff Pairs in an Array [Medium]
Given an array of integers and an integer k, find the number of unique k-diff pairs in the array.
##### Optimal Python solution:
```python

- def findPairs(nums, k):
-     count = 0
-     if k < 0:
-         return count
-     num_count = {}
-     for num in nums:
-         num_count[num] = num_count.get(num, 0) + 1
-     for num in num_count:
-         if k == 0:
-             if num_count[num] > 1:
-                 count += 1
-         else:
-             if num + k in num_count:
-                 count += 1
-     return count
- 
- nums = [3, 1, 4, 1, 5]
- k = 2
- print(findPairs(nums, k))
```
Finding the number of unique k-diff pairs in an array
    
### >> 327 Count of Range Sum [Hard]
Given an integer array nums, return the number of range sums that lie in [lower, upper] inclusive.
Range sum S(i, j) is defined as the sum of the elements in nums between indices i and j (i ≤ j), inclusive.
##### Sample input:
[-2,5,-1]
-2
2
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the maximum length of the input array? Can the input array contain negative numbers? Can the input array be empty?

##### Optimal Python solution:
```python
class Solution:
    def countRangeSum(self, nums: List[int], lower: int, upper: int) -> int:
        def countRangeSumRecursive(nums, lower, upper, left, right) -> int:
            if left == right:
                return 0
            mid = (left + right) // 2
            n1 = countRangeSumRecursive(nums, lower, upper, left, mid)
            n2 = countRangeSumRecursive(nums, lower, upper, mid + 1, right)
            res = n1 + n2
            i = left
            l = mid + 1
            r = mid + 1
            while i <= mid:
                while l <= right and sums[l] - sums[i] < lower:
                    l += 1
                while r <= right and sums[r] - sums[i] <= upper:
                    r += 1
                res += r - l
                i += 1
            sorted_nums = [0] * (right - left + 1)
            p1 = left
            p2 = mid + 1
            p = 0
            while p1 <= mid or p2 <= right:
                if p1 > mid:
                    sorted_nums[p] = sums[p2]
                    p2 += 1
                elif p2 > right:
                    sorted_nums[p] = sums[p1]
                    p1 += 1
                else:
                    if sums[p1] < sums[p2]:
                        sorted_nums[p] = sums[p1]
                        p1 += 1
                    else:
                        sorted_nums[p] = sums[p2]
                        p2 += 1
                p += 1
            for i in range(len(sorted_nums)):
                sums[left + i] = sorted_nums[i]
            return res
        if not nums:
            return 0
        sums = [0] * (len(nums) + 1)
        for i in range(len(nums)):
            sums[i + 1] = sums[i] + nums[i]
        return countRangeSumRecursive(sums, lower, upper, 0, len(sums) - 1)
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:
1. Use divide and conquer approach to count the number of range sums.
2. Use merge sort to merge the range sums.
3. Use binary search to find the lower and upper bounds of the range sums.
1. Use prefix sums to calculate the range sums.
2. Use merge sort to merge the range sums.
3. Use binary search to find the lower and upper bounds of the range sums.
The range sums can be negative, so we need to consider the lower and upper bounds carefully.
Avoid using brute force approach to count the range sums.
    
### >> Comparison: 532 K-diff Pairs in an Array [Medium] *VS* 327 Count of Range Sum [Hard]
> Similarity distance: 0.5058
##### Similarities

- Both questions involve manipulating an array of numbers.
- Both questions require counting or finding pairs of numbers that meet certain criteria.
- Both questions have complexity requirements that make brute force solutions inefficient.
##### Differences

- 532 K-diff Pairs in an Array focuses on finding pairs of numbers with a specific difference, while 327 Count of Range Sum focuses on counting the number of ranges with a specific sum.
- 532 K-diff Pairs in an Array has a complexity requirement of O(n), while 327 Count of Range Sum has a complexity requirement of O(n log n).
- 532 K-diff Pairs in an Array can have duplicate pairs, while 327 Count of Range Sum does not have duplicate ranges.
##### New Insights in 327 Count of Range Sum [Hard]

- 532 K-diff Pairs in an Array teaches us how to efficiently find pairs of numbers with a specific difference using a hashmap.
- 327 Count of Range Sum teaches us how to efficiently count the number of ranges with a specific sum using a modified merge sort algorithm.

