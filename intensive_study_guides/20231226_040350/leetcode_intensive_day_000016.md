
# Leetcode Intensive Tutorial Day 16 
> [Difficulty Score: 15]

> [Version: 20231226_040350]

> [Including this day, you had studied : 121 leetcode problems]


## Courses overview of the day

- 561 Array Partition I [Easy]
  - 215 Kth Largest Element in an Array [Medium]
    - 324 Wiggle Sort II [Medium]
  - 280 Wiggle Sort [Medium]
    - 179 Largest Number [Medium]
      - 522 Longest Uncommon Subsequence II [Medium]
        - 581 Shortest Unsorted Continuous Subarray [Medium]
  - 360 Sort Transformed Array [Medium]

#### Step by step

 - [1. From 561 Array Partition I [Easy] to 215 Kth Largest Element in an Array [Medium]](#1-from-561-array-partition-i-easy-to-215-kth-largest-element-in-an-array-medium))

 - [2. From 215 Kth Largest Element in an Array [Medium] to 324 Wiggle Sort II [Medium]](#2-from-215-kth-largest-element-in-an-array-medium-to-324-wiggle-sort-ii-medium))

 - [3. From 561 Array Partition I [Easy] to 280 Wiggle Sort [Medium]](#3-from-561-array-partition-i-easy-to-280-wiggle-sort-medium))

 - [4. From 280 Wiggle Sort [Medium] to 179 Largest Number [Medium]](#4-from-280-wiggle-sort-medium-to-179-largest-number-medium))

 - [5. From 179 Largest Number [Medium] to 522 Longest Uncommon Subsequence II [Medium]](#5-from-179-largest-number-medium-to-522-longest-uncommon-subsequence-ii-medium))

 - [6. From 522 Longest Uncommon Subsequence II [Medium] to 581 Shortest Unsorted Continuous Subarray [Medium]](#6-from-522-longest-uncommon-subsequence-ii-medium-to-581-shortest-unsorted-continuous-subarray-medium))

 - [7. From 561 Array Partition I [Easy] to 360 Sort Transformed Array [Medium]](#7-from-561-array-partition-i-easy-to-360-sort-transformed-array-medium))

    

#### Summary


- 581 Shortest Unsorted Continuous Subarray : Find the shortest unsorted subarray in an array.
- 280 Wiggle Sort : The essence of this problem is to reorder the array in-place such that nums[0] <= nums[1] >= nums[2] <= nums[3]....
- 522 Longest Uncommon Subsequence II : The essence of this question is to find the longest uncommon subsequence among a list of strings.
- 215 Kth Largest Element in an Array : The essence of this problem is to find the kth largest element in an unsorted array.
- 179 Largest Number : Sorting
- 324 Wiggle Sort II : The essence of this problem is to reorder an unsorted array in a way that satisfies the wiggle sort condition.
- 561 Array Partition I : The essence of this problem is to find the optimal pairing of elements to maximize the sum of the minimum elements in each pair.
- 360 Sort Transformed Array : Apply a quadratic function to each element in a sorted array and return the sorted result.
> Similarity Diameter of these problems: 0.6841


---
# 1. From 561 Array Partition I [Easy] to 215 Kth Largest Element in an Array [Medium]
> Similarity Distance: 0.4379

### >> 561 Array Partition I [Easy]
Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.
##### Sample input:
[1,4,3,2]
##### Sample output:
4

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the array contain duplicates?

##### Optimal Python solution:
```python
def arrayPairSum(nums):
    nums.sort()
    return sum(nums[::2])
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(1)
##### Notes:
The sum of min(ai, bi) is maximized when the pairs are formed by adjacent elements in the sorted array.
Use the built-in sort function in Python.
None
None
    
### >> 215 Kth Largest Element in an Array [Medium]
Find the kth largest element in an unsorted array.
##### Sample input:
[3,2,1,5,6,4]
2
##### Sample output:
5

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the array contain duplicates? What should be returned if k is larger than the length of the array?

##### Optimal Python solution:
```python
def findKthLargest(nums, k):
    return sorted(nums)[-k]
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(1)
##### Notes:
1. Sort the array in descending order.
2. Return the kth element from the sorted array.
Use the sorted() function in Python to sort the array in descending order.
Using a heap data structure can improve the time complexity to O(n log k).
Avoid using a brute force approach to sort the array.
    
### >> Comparison: 561 Array Partition I [Easy] *VS* 215 Kth Largest Element in an Array [Medium]
> Similarity distance: 0.4379
##### Similarities

- Both questions involve manipulating arrays.
- Both questions require finding a specific element in the array.
- Both questions have a time complexity of O(nlogn).
##### Differences

- 561 Array Partition I involves dividing the array into pairs and summing the minimum value of each pair, while 215 Kth Largest Element in an Array involves finding the kth largest element in the array.
- 561 Array Partition I has an input constraint of an even number of elements in the array, while 215 Kth Largest Element in an Array has no specific input constraint.
- 561 Array Partition I has an output of the maximum sum of the minimum values of each pair, while 215 Kth Largest Element in an Array has an output of the kth largest element in the array.
##### New Insights in 215 Kth Largest Element in an Array [Medium]

- 561 Array Partition I teaches us how to efficiently divide an array into pairs and find the sum of the minimum values.
- 215 Kth Largest Element in an Array teaches us how to efficiently find the kth largest element in an array using a partitioning algorithm.


---
# 2. From 215 Kth Largest Element in an Array [Medium] to 324 Wiggle Sort II [Medium]
> Similarity Distance: 0.4925

### >> Reminder: 215 Kth Largest Element in an Array [Medium]
Find the kth largest element in an unsorted array.
##### Optimal Python solution:
```python
def findKthLargest(nums, k):
    return sorted(nums)[-k]
```
The essence of this problem is to find the kth largest element in an unsorted array.
    
### >> 324 Wiggle Sort II [Medium]
Given an unsorted array nums, reorder it such that nums[0] < nums[1] > nums[2] < nums[3]....
##### Sample input:
nums = [1, 5, 1, 1, 6, 4]
nums = [1, 3, 2, 2, 3, 1]
##### Sample output:
[1, 6, 1, 5, 1, 4]
[2, 3, 1, 3, 1, 2]

##### Questions to ask to clarify requirements:
Can the input array contain duplicate elements? Can the input array be empty?

##### Optimal Python solution:
```python
class Solution:
    def wiggleSort(self, nums: List[int]) -> None:
        n = len(nums)
        sorted_nums = sorted(nums)
        mid = (n - 1) // 2
        nums[::2] = sorted_nums[:mid+1][::-1]
        nums[1::2] = sorted_nums[mid+1:][::-1]
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:
Sort the array in ascending order.
Split the sorted array into two halves.
Reverse each half.
Interleave the two halves to get the wiggle sorted array.
Understand the concept of wiggle sort and how it can be achieved by sorting and manipulating arrays.
Optimize the solution by reversing the two halves of the sorted array instead of using additional space.
Handle edge cases such as empty arrays and arrays with duplicate elements.
Reversing the two halves of the sorted array to achieve the wiggle sort.
Using a brute force approach to reorder the array.
    
### >> Comparison: 215 Kth Largest Element in an Array [Medium] *VS* 324 Wiggle Sort II [Medium]
> Similarity distance: 0.4925
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating an array.
- Both questions require finding the kth largest element in the array.
##### Differences

- 215 Kth Largest Element in an Array focuses on finding the kth largest element in the array.
- 324 Wiggle Sort II focuses on rearranging the array in a specific order.
- 215 Kth Largest Element in an Array uses a partitioning algorithm like QuickSelect.
- 324 Wiggle Sort II uses a combination of sorting and rearranging techniques.
##### New Insights in 324 Wiggle Sort II [Medium]

- 215 Kth Largest Element in an Array teaches us how to use the QuickSelect algorithm to efficiently find the kth largest element.
- 324 Wiggle Sort II teaches us how to rearrange an array in a specific order to satisfy the wiggle sort property.


---
# 3. From 561 Array Partition I [Easy] to 280 Wiggle Sort [Medium]
> Similarity Distance: 0.4393

### >> Reminder: 561 Array Partition I [Easy]
Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.
##### Optimal Python solution:
```python
def arrayPairSum(nums):
    nums.sort()
    return sum(nums[::2])
```
The essence of this problem is to find the optimal pairing of elements to maximize the sum of the minimum elements in each pair.
    
### >> 280 Wiggle Sort [Medium]
Given an unsorted array nums, reorder it in-place such that nums[0] <= nums[1] >= nums[2] <= nums[3]....
##### Sample input:
[3,5,2,1,6,4]
[1,2,3,4,5,6]
##### Sample output:
[3,5,1,6,2,4]
[1,3,2,5,4,6]

##### Questions to ask to clarify requirements:
Can the array contain duplicate elements?

##### Optimal Python solution:
```python
class Solution:
    def wiggleSort(self, nums: List[int]) -> None:
        for i in range(1, len(nums)):
            if (i % 2 == 1 and nums[i] < nums[i - 1]) or (i % 2 == 0 and nums[i] > nums[i - 1]):
                nums[i], nums[i - 1] = nums[i - 1], nums[i]
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Iterate through the array and swap adjacent elements if they don't satisfy the wiggle sort condition.
2. Use the modulo operator to determine the position of the element in the array.
3. The time complexity of the solution is O(n), where n is the length of the array.
1. Use the modulo operator to determine the position of the element in the array.
2. Iterate through the array and swap adjacent elements if they don't satisfy the wiggle sort condition.
None
None
    
### >> Comparison: 561 Array Partition I [Easy] *VS* 280 Wiggle Sort [Medium]
> Similarity distance: 0.4393
##### Similarities

- Both questions involve manipulating arrays.
- Both questions have a specific requirement for rearranging the elements of the array.
##### Differences

- 561 Array Partition I: The goal is to divide the array into pairs and find the sum of the minimum element in each pair.
- 280 Wiggle Sort: The goal is to rearrange the array such that nums[0] <= nums[1] >= nums[2] <= nums[3]...
##### New Insights in 280 Wiggle Sort [Medium]

- 561 Array Partition I: The insight is to sort the array and then sum the elements at even indices.
- 280 Wiggle Sort: The insight is to iterate through the array and swap elements to achieve the desired ordering.


---
# 4. From 280 Wiggle Sort [Medium] to 179 Largest Number [Medium]
> Similarity Distance: 0.4560

### >> Reminder: 280 Wiggle Sort [Medium]
Given an unsorted array nums, reorder it in-place such that nums[0] <= nums[1] >= nums[2] <= nums[3]....
##### Optimal Python solution:
```python
class Solution:
    def wiggleSort(self, nums: List[int]) -> None:
        for i in range(1, len(nums)):
            if (i % 2 == 1 and nums[i] < nums[i - 1]) or (i % 2 == 0 and nums[i] > nums[i - 1]):
                nums[i], nums[i - 1] = nums[i - 1], nums[i]
```
The essence of this problem is to reorder the array in-place such that nums[0] <= nums[1] >= nums[2] <= nums[3]....
    
### >> 179 Largest Number [Medium]
Given a list of non-negative integers, arrange them such that they form the largest number.
##### Sample input:
[10,2]
##### Sample output:
"210"

##### Questions to ask to clarify requirements:
Can the input list be empty?

##### Optimal Python solution:
```python
def largestNumber(nums):
    nums = [str(num) for num in nums]
    nums.sort(key=lambda x: x*10, reverse=True)
    return str(int(''.join(nums)))
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(n)
##### Notes:

- Convert the numbers to strings
- Sort the strings based on their concatenation
- Join the sorted strings
Use the key parameter of the sort function to define a custom sorting order
Handling leading zeros
Converting the numbers to integers
    
### >> Comparison: 280 Wiggle Sort [Medium] *VS* 179 Largest Number [Medium]
> Similarity distance: 0.4560
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve sorting.
- Both questions require rearranging elements in a specific order.
##### Differences

- 280 Wiggle Sort: The goal is to rearrange the array such that nums[0] <= nums[1] >= nums[2] <= nums[3]...
- 179 Largest Number: The goal is to rearrange the array to form the largest possible number.
##### New Insights in 179 Largest Number [Medium]

- 280 Wiggle Sort: We can solve this problem in linear time without using any extra space.
- 179 Largest Number: We can use a custom comparator to sort the array in a specific order.


---
# 5. From 179 Largest Number [Medium] to 522 Longest Uncommon Subsequence II [Medium]
> Similarity Distance: 0.5737

### >> Reminder: 179 Largest Number [Medium]
Given a list of non-negative integers, arrange them such that they form the largest number.
##### Optimal Python solution:
```python
def largestNumber(nums):
    nums = [str(num) for num in nums]
    nums.sort(key=lambda x: x*10, reverse=True)
    return str(int(''.join(nums)))
```
Sorting
    
### >> 522 Longest Uncommon Subsequence II [Medium]
Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.
##### Sample input:
["aba", "cdc", "aba"]
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is a subsequence of a string?

##### Optimal Python solution:
```python
def findLUSlength(strs: List[str]) -> int:
    def is_subsequence(s: str, t: str) -> bool:
        i = 0
        for c in t:
            if i < len(s) and s[i] == c:
                i += 1
        return i == len(s)
    strs.sort(key=len, reverse=True)
    for i, s in enumerate(strs):
        if all(not is_subsequence(s, t) for j, t in enumerate(strs) if i != j):
            return len(s)
    return -1
```
##### Time complexity:
O(n^2 * m)
##### Space complexity:
O(1)
##### Notes:
1. The longest uncommon subsequence is the longest string in the list if it is not a subsequence of any other string.
2. If all strings in the list are subsequences of each other, there is no uncommon subsequence.
3. The longest uncommon subsequence cannot be a subsequence of any other string.
There is no specific programming tip for this question.
There is no tricky part in this question.
There is no specific thing to avoid in this question.
    
### >> Comparison: 179 Largest Number [Medium] *VS* 522 Longest Uncommon Subsequence II [Medium]
> Similarity distance: 0.5737
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating strings.
- Both questions require finding the longest subsequence.
- Both questions have multiple test cases.
##### Differences

- Question 179 involves sorting the numbers in a specific way to form the largest number.
- Question 522 involves finding the longest uncommon subsequence among a list of strings.
- Question 179 has a time complexity of O(nlogn), while question 522 has a time complexity of O(n^2).
- Question 179 has a space complexity of O(n), while question 522 has a space complexity of O(1).
##### New Insights in 522 Longest Uncommon Subsequence II [Medium]

- Question 179 teaches us how to sort numbers in a custom way to form the largest number.
- Question 522 teaches us how to find the longest uncommon subsequence among a list of strings efficiently.


---
# 6. From 522 Longest Uncommon Subsequence II [Medium] to 581 Shortest Unsorted Continuous Subarray [Medium]
> Similarity Distance: 0.5610

### >> Reminder: 522 Longest Uncommon Subsequence II [Medium]
Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.
##### Optimal Python solution:
```python
def findLUSlength(strs: List[str]) -> int:
    def is_subsequence(s: str, t: str) -> bool:
        i = 0
        for c in t:
            if i < len(s) and s[i] == c:
                i += 1
        return i == len(s)
    strs.sort(key=len, reverse=True)
    for i, s in enumerate(strs):
        if all(not is_subsequence(s, t) for j, t in enumerate(strs) if i != j):
            return len(s)
    return -1
```
The essence of this question is to find the longest uncommon subsequence among a list of strings.
    
### >> 581 Shortest Unsorted Continuous Subarray [Medium]
Given an integer array nums, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order.

Return the shortest such subarray and output its length.
##### Sample input:
[2,6,4,8,10,9,15]
##### Sample output:
5

##### Questions to ask to clarify requirements:
What is the maximum length of the input array? Can the array contain duplicates?

##### Optimal Python solution:
```python
def findUnsortedSubarray(nums):
    sorted_nums = sorted(nums)
    start = len(nums)
    end = 0
    for i in range(len(nums)):
        if nums[i] != sorted_nums[i]:
            start = min(start, i)
            end = max(end, i)
    return end - start + 1
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(n)
##### Notes:
1. Sort the array and compare it with the original array to find the start and end indices of the unsorted subarray.
2. Return the length of the subarray.
Use the sorted() function to sort the array.
None
None
    
### >> Comparison: 522 Longest Uncommon Subsequence II [Medium] *VS* 581 Shortest Unsorted Continuous Subarray [Medium]
> Similarity distance: 0.5610
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding subsequences in an array.
- Both questions require understanding of array manipulation.
##### Differences

- 522 Longest Uncommon Subsequence II involves finding the longest uncommon subsequence among a list of strings.
- 581 Shortest Unsorted Continuous Subarray involves finding the length of the shortest subarray that, when sorted, makes the entire array sorted.
##### New Insights in 581 Shortest Unsorted Continuous Subarray [Medium]

- From 522 Longest Uncommon Subsequence II, we can learn how to efficiently compare and find uncommon subsequences among a list of strings.
- From 581 Shortest Unsorted Continuous Subarray, we can learn how to identify the shortest unsorted subarray in an array.


---
# 7. From 561 Array Partition I [Easy] to 360 Sort Transformed Array [Medium]
> Similarity Distance: 0.5570

### >> Reminder: 561 Array Partition I [Easy]
Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.
##### Optimal Python solution:
```python
def arrayPairSum(nums):
    nums.sort()
    return sum(nums[::2])
```
The essence of this problem is to find the optimal pairing of elements to maximize the sum of the minimum elements in each pair.
    
### >> 360 Sort Transformed Array [Medium]
Given a sorted array of integers nums and integer values a, b and c. Apply a quadratic function of the form f(x) = ax^2 + bx + c to each element x in the array. The returned array must be in sorted order.
##### Sample input:
nums = [-4, -2, 2, 4], a = 1, b = 3, c = 5
##### Sample output:
[3, 9, 15, 33]

##### Questions to ask to clarify requirements:
1. Can the array contain duplicate elements?
2. Can the values of a, b, and c be negative?
3. Can the array be empty?

##### Optimal Python solution:
```python
class Solution:
    def sortTransformedArray(self, nums: List[int], a: int, b: int, c: int) -> List[int]:
        res = []
        left, right = 0, len(nums) - 1
        while left <= right:
            left_val = a * nums[left] * nums[left] + b * nums[left] + c
            right_val = a * nums[right] * nums[right] + b * nums[right] + c
            if a >= 0:
                if left_val >= right_val:
                    res.append(left_val)
                    left += 1
                else:
                    res.append(right_val)
                    right -= 1
            else:
                if left_val <= right_val:
                    res.append(left_val)
                    left += 1
                else:
                    res.append(right_val)
                    right -= 1
        if a >= 0:
            return res[::-1]
        else:
            return res
```
##### Time complexity:
O(N)
##### Space complexity:
O(1)
##### Notes:
1. Use two pointers to iterate from the start and end of the array.
2. Calculate the transformed value for each element using the quadratic function.
3. Append the transformed values to the result array in the correct order.
1. Use two pointers to iterate from the start and end of the array.
2. Calculate the transformed value for each element using the quadratic function.
3. Append the transformed values to the result array in the correct order.
1. Handling negative values of a.
2. Handling the case when a is equal to 0.
1. Sorting the array after applying the quadratic function.
2. Using additional data structures to store the transformed values.
    
### >> Comparison: 561 Array Partition I [Easy] *VS* 360 Sort Transformed Array [Medium]
> Similarity distance: 0.5570
##### Similarities

- Both questions involve manipulating arrays.
- Both questions require sorting the array in some way.
- Both questions have a time complexity of O(nlogn) for the sorting operation.
##### Differences

- 561 Array Partition I involves dividing the array into pairs and summing the minimum value of each pair.
- 360 Sort Transformed Array involves transforming the array elements using a quadratic function and then sorting the transformed array.
##### New Insights in 360 Sort Transformed Array [Medium]

- 561 Array Partition I teaches us how to efficiently divide an array into pairs and find the sum of the minimum values.
- 360 Sort Transformed Array teaches us how to transform array elements using a quadratic function and sort the transformed array.

