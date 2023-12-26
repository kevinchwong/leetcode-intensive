
# Leetcode Intensive Tutorial Day 31 
> [Difficulty Score: 18]

> [Version: 20231226_040350]

> [Including this day, you had studied : 244 leetcode problems]


## Courses overview of the day

- 496 Next Greater Element I [Easy]
  - 284 Peeking Iterator [Medium]
    - 228 Summary Ranges [Medium]
      - 152 Maximum Product Subarray [Medium]
  - 525 Contiguous Array [Medium]
    - 565 Array Nesting [Medium]
      - 485 Max Consecutive Ones [Easy]
  - 503 Next Greater Element II [Medium]
    - 239 Sliding Window Maximum [Hard]

#### Step by step

 - [1. From 496 Next Greater Element I [Easy] to 284 Peeking Iterator [Medium]](#1-from-496-next-greater-element-i-easy-to-284-peeking-iterator-medium))

 - [2. From 284 Peeking Iterator [Medium] to 228 Summary Ranges [Medium]](#2-from-284-peeking-iterator-medium-to-228-summary-ranges-medium))

 - [3. From 228 Summary Ranges [Medium] to 152 Maximum Product Subarray [Medium]](#3-from-228-summary-ranges-medium-to-152-maximum-product-subarray-medium))

 - [4. From 496 Next Greater Element I [Easy] to 525 Contiguous Array [Medium]](#4-from-496-next-greater-element-i-easy-to-525-contiguous-array-medium))

 - [5. From 525 Contiguous Array [Medium] to 565 Array Nesting [Medium]](#5-from-525-contiguous-array-medium-to-565-array-nesting-medium))

 - [6. From 565 Array Nesting [Medium] to 485 Max Consecutive Ones [Easy]](#6-from-565-array-nesting-medium-to-485-max-consecutive-ones-easy))

 - [7. From 496 Next Greater Element I [Easy] to 503 Next Greater Element II [Medium]](#7-from-496-next-greater-element-i-easy-to-503-next-greater-element-ii-medium))

 - [8. From 503 Next Greater Element II [Medium] to 239 Sliding Window Maximum [Hard]](#8-from-503-next-greater-element-ii-medium-to-239-sliding-window-maximum-hard))

    

#### Summary


- 152 Maximum Product Subarray : The essence of this problem is to find the contiguous subarray with the largest product.
- 496 Next Greater Element I : Use stack to track next greater elements.
- 228 Summary Ranges : Return the summary of ranges in a sorted integer array.
- 284 Peeking Iterator : Design an iterator that supports peek, hasNext, and next operations on a list.
- 239 Sliding Window Maximum : The essence of this problem is to efficiently find the maximum element in each window of size k using the sliding window technique and a deque.
- 503 Next Greater Element II : The essence of this problem is to find the next greater element for each element in a circular array.
- 525 Contiguous Array : The essence of this problem is to find the longest contiguous subarray with equal number of 0s and 1s in a binary array.
- 485 Max Consecutive Ones : The essence of this problem is to find the maximum number of consecutive ones in a binary array.
- 565 Array Nesting : Given an array of integers, find the longest length of a set where each element is the index of the next element in the set.
> Similarity Diameter of these problems: 0.6657


---
# 1. From 496 Next Greater Element I [Easy] to 284 Peeking Iterator [Medium]
> Similarity Distance: 0.4364

### >> 496 Next Greater Element I [Easy]
You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.
##### Sample input:
[4,1,2]
[1,3,4,2]
##### Sample output:
[-1,3,-1]

##### Questions to ask to clarify requirements:
Can the arrays contain duplicates? Can the arrays be empty?

##### Optimal Python solution:
```python
def nextGreaterElement(nums1, nums2):
    stack = []
    next_greater = {}
    for num in nums2:
        while stack and stack[-1] < num:
            next_greater[stack.pop()] = num
        stack.append(num)
    return [next_greater.get(num, -1) for num in nums1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to keep track of the next greater elements.
2. Iterate through nums2 and update the stack and next_greater dictionary.
3. Return the next greater elements for nums1.
None
None
None
    
### >> 284 Peeking Iterator [Medium]
Design an iterator that supports the peek operation on a list in addition to the hasNext and next operations.
##### Sample input:
['PeekingIterator', 'next', 'peek', 'next', 'next', 'hasNext'], [[[1,2,3]], [], [], [], [], []]
##### Sample output:
[null, 1, 2, 2, 3, false]

##### Questions to ask to clarify requirements:
Do we need to handle empty lists?

##### Optimal Python solution:
```python
class PeekingIterator:
    def __init__(self, iterator):
        self.iterator = iterator
        self.next_element = self.iterator.next()
        self.has_next_element = self.iterator.hasNext()

    def peek(self):
        return self.next_element

    def next(self):
        element = self.next_element
        self.next_element = self.iterator.next() if self.iterator.hasNext() else None
        self.has_next_element = self.next_element is not None
        return element

    def hasNext(self):
        return self.has_next_element
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:

- Initialize the iterator with the given list
- Keep track of the next element and whether there is a next element
- Return the next element when peek or next is called
- Update the next element and has_next_element variables when next is called
Handle edge cases such as empty lists and modifying the list during iteration.
None
None
    
### >> Comparison: 496 Next Greater Element I [Easy] *VS* 284 Peeking Iterator [Medium]
> Similarity distance: 0.4364
##### Similarities

- Both questions involve iterating over a collection of elements.
- Both questions require finding the next greater element.
##### Differences

- 496 Next Greater Element I focuses on finding the next greater element in a different array.
- 284 Peeking Iterator focuses on iterating and peeking at the next element in an iterator.
##### New Insights in 284 Peeking Iterator [Medium]

- 496 Next Greater Element I introduces the concept of using a stack to solve the problem efficiently.
- 284 Peeking Iterator introduces the concept of peeking at the next element without advancing the iterator.


---
# 2. From 284 Peeking Iterator [Medium] to 228 Summary Ranges [Medium]
> Similarity Distance: 0.5334

### >> Reminder: 284 Peeking Iterator [Medium]
Design an iterator that supports the peek operation on a list in addition to the hasNext and next operations.
##### Optimal Python solution:
```python
class PeekingIterator:
    def __init__(self, iterator):
        self.iterator = iterator
        self.next_element = self.iterator.next()
        self.has_next_element = self.iterator.hasNext()

    def peek(self):
        return self.next_element

    def next(self):
        element = self.next_element
        self.next_element = self.iterator.next() if self.iterator.hasNext() else None
        self.has_next_element = self.next_element is not None
        return element

    def hasNext(self):
        return self.has_next_element
```
Design an iterator that supports peek, hasNext, and next operations on a list.
    
### >> 228 Summary Ranges [Medium]
Given a sorted integer array without duplicates, return the summary of its ranges.
##### Sample input:
[0,1,2,4,5,7]
##### Sample output:
["0->2","4->5","7"]

##### Questions to ask to clarify requirements:
Can the input array be empty? Can the input array contain negative numbers?

##### Optimal Python solution:
```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        if not nums:
            return []
        ranges = []
        start = nums[0]
        end = nums[0]
        for i in range(1, len(nums)):
            if nums[i] == end + 1:
                end = nums[i]
            else:
                if start == end:
                    ranges.append(str(start))
                else:
                    ranges.append(str(start) + '->' + str(end))
                start = nums[i]
                end = nums[i]
        if start == end:
            ranges.append(str(start))
        else:
            ranges.append(str(start) + '->' + str(end))
        return ranges
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Initialize start and end variables
2. Iterate through the array
3. Update start and end based on the current element
4. Append the range to the result list
5. Return the result list
1. Use two variables to track the start and end of each range
2. Update the variables based on the current element
3. Append the range to the result list
4. Handle the last range separately
Handling the last range
Using additional data structures
    
### >> Comparison: 284 Peeking Iterator [Medium] *VS* 228 Summary Ranges [Medium]
> Similarity distance: 0.5334
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve iterating over a collection of numbers.
- Both questions require implementing an iterator.
##### Differences

- 284 Peeking Iterator focuses on providing a way to peek at the next element in the iterator without advancing it, while 228 Summary Ranges focuses on finding and returning the summary ranges of consecutive numbers in the iterator.
- 284 Peeking Iterator requires implementing the `peek()` method, while 228 Summary Ranges requires implementing the `summaryRanges()` method.
- 284 Peeking Iterator allows multiple calls to `peek()` without advancing the iterator, while 228 Summary Ranges only requires a single call to `summaryRanges()` to find all the summary ranges.
- 284 Peeking Iterator requires keeping track of the current element and the next element, while 228 Summary Ranges only requires keeping track of the start and end of each summary range.
##### New Insights in 228 Summary Ranges [Medium]

- 284 Peeking Iterator provides a way to access the next element in the iterator without advancing it, which can be useful in certain scenarios where you need to check the next element before deciding whether to advance the iterator or not.
- 228 Summary Ranges introduces the concept of summary ranges, which are consecutive ranges of numbers in the iterator. This can be a useful technique for analyzing and summarizing data.


---
# 3. From 228 Summary Ranges [Medium] to 152 Maximum Product Subarray [Medium]
> Similarity Distance: 0.4963

### >> Reminder: 228 Summary Ranges [Medium]
Given a sorted integer array without duplicates, return the summary of its ranges.
##### Optimal Python solution:
```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        if not nums:
            return []
        ranges = []
        start = nums[0]
        end = nums[0]
        for i in range(1, len(nums)):
            if nums[i] == end + 1:
                end = nums[i]
            else:
                if start == end:
                    ranges.append(str(start))
                else:
                    ranges.append(str(start) + '->' + str(end))
                start = nums[i]
                end = nums[i]
        if start == end:
            ranges.append(str(start))
        else:
            ranges.append(str(start) + '->' + str(end))
        return ranges
```
Return the summary of ranges in a sorted integer array.
    
### >> 152 Maximum Product Subarray [Medium]
Given an integer array nums, find the contiguous subarray within an array (containing at least one number) which has the largest product.
##### Sample input:
nums = [2,3,-2,4]
Output: 6
##### Sample output:
6

##### Questions to ask to clarify requirements:
Can the input array contain zeros? Can the input array be empty?

##### Optimal Python solution:
```python
def maxProduct(nums):
    max_product = nums[0]
    min_product = nums[0]
    result = nums[0]
    for i in range(1, len(nums)):
        if nums[i] < 0:
            max_product, min_product = min_product, max_product
        max_product = max(nums[i], max_product * nums[i])
        min_product = min(nums[i], min_product * nums[i])
        result = max(result, max_product)
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Initialize max_product, min_product, and result to the first element of the array.
2. Iterate through the array and update max_product, min_product, and result based on the current element.
1. Use dynamic programming to keep track of the maximum product, minimum product, and overall result.
2. Handle edge cases like an empty array and negative numbers.
3. Update max_product and min_product when encountering a negative number.
1. Handling negative numbers.
2. Handling zeros.
3. Updating max_product and min_product when encountering a negative number.
1. Using a nested loop to check all subarrays.
2. Using extra space.
    
### >> Comparison: 228 Summary Ranges [Medium] *VS* 152 Maximum Product Subarray [Medium]
> Similarity distance: 0.4963
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating arrays.
- Both questions require finding a specific pattern or property in the array.
- Both questions have multiple possible solutions.
##### Differences

- Question 228 involves finding summary ranges in an array, while question 152 involves finding the maximum product subarray.
- Question 228 requires identifying consecutive numbers in the array, while question 152 requires identifying subarrays with maximum product.
- Question 228 has a linear time complexity solution, while question 152 has a dynamic programming solution.
- Question 228 has a simpler implementation compared to question 152.
##### New Insights in 152 Maximum Product Subarray [Medium]

- Question 228 teaches us how to identify consecutive numbers in an array.
- Question 152 teaches us how to find the maximum product subarray using dynamic programming.
- Both questions provide insights into different array manipulation techniques.


---
# 4. From 496 Next Greater Element I [Easy] to 525 Contiguous Array [Medium]
> Similarity Distance: 0.4928

### >> Reminder: 496 Next Greater Element I [Easy]
You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.
##### Optimal Python solution:
```python
def nextGreaterElement(nums1, nums2):
    stack = []
    next_greater = {}
    for num in nums2:
        while stack and stack[-1] < num:
            next_greater[stack.pop()] = num
        stack.append(num)
    return [next_greater.get(num, -1) for num in nums1]
```
Use stack to track next greater elements.
    
### >> 525 Contiguous Array [Medium]
Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.
##### Sample input:
[0,1]
##### Sample output:
2

##### Questions to ask to clarify requirements:

- What is the maximum length of the binary array?
- Can the binary array be empty?
- Can the binary array contain elements other than 0 and 1?

##### Optimal Python solution:
```python
def findMaxLength(nums):
    count = 0
    max_length = 0
    count_dict = {0: -1}
    for i in range(len(nums)):
        if nums[i] == 0:
            count -= 1
        else:
            count += 1
        if count in count_dict:
            max_length = max(max_length, i - count_dict[count])
        else:
            count_dict[count] = i
    return max_length
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a count variable to keep track of the difference between the number of 0s and 1s encountered so far.
- Use a dictionary to store the count and its corresponding index.
- Update the maximum length whenever the count is encountered again.

- Use a dictionary to store the count and its corresponding index for efficient lookup.
- Update the maximum length whenever the count is encountered again to keep track of the longest contiguous subarray.

- Using a dictionary to store the count and its corresponding index.
- Updating the maximum length whenever the count is encountered again.

- Using nested loops to check all possible subarrays.
    
### >> Comparison: 496 Next Greater Element I [Easy] *VS* 525 Contiguous Array [Medium]
> Similarity distance: 0.4928
##### Similarities

- Both questions involve finding the next greater element in an array.
- Both questions require iterating through the array to find the solution.
- Both questions have a time complexity of O(n).
##### Differences

- 496 Next Greater Element I focuses on finding the next greater element for each element in one array from another array.
- 525 Contiguous Array focuses on finding the maximum length of a contiguous subarray with an equal number of 0s and 1s.
- 496 Next Greater Element I requires using a stack to efficiently find the next greater element.
- 525 Contiguous Array requires using a hashmap to keep track of the running sum and its corresponding index.
##### New Insights in 525 Contiguous Array [Medium]

- 496 Next Greater Element I introduces the concept of using a stack to solve problems efficiently.
- 525 Contiguous Array introduces the concept of using a hashmap to keep track of running sums.


---
# 5. From 525 Contiguous Array [Medium] to 565 Array Nesting [Medium]
> Similarity Distance: 0.4992

### >> Reminder: 525 Contiguous Array [Medium]
Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.
##### Optimal Python solution:
```python
def findMaxLength(nums):
    count = 0
    max_length = 0
    count_dict = {0: -1}
    for i in range(len(nums)):
        if nums[i] == 0:
            count -= 1
        else:
            count += 1
        if count in count_dict:
            max_length = max(max_length, i - count_dict[count])
        else:
            count_dict[count] = i
    return max_length
```
The essence of this problem is to find the longest contiguous subarray with equal number of 0s and 1s in a binary array.
    
### >> 565 Array Nesting [Medium]
You are given an integer array nums of length n where nums is a permutation of the numbers in the range [0, n - 1]. You should build a set s[k] = {nums[k], nums[nums[k]], nums[nums[nums[k]]], ... } subjected to the following rule:

The first element in s[k] starts with the selection of the element nums[k] of index = k.
The next element in s[k] should be nums[nums[k]], and then nums[nums[nums[k]]], and so on.
We stop adding right before a duplicate element occurs in s[k].
Return the longest length of a set s[k].
##### Sample input:
[0,2,1]
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the input array be empty?

##### Optimal Python solution:
```python
def arrayNesting(nums):
    n = len(nums)
    visited = [False] * n
    ans = 0
    for i in range(n):
        if not visited[i]:
            start = nums[i]
            count = 0
            while True:
                start = nums[start]
                count += 1
                visited[start] = True
                if start == nums[i]:
                    break
            ans = max(ans, count)
    return ans
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use a visited array to keep track of visited elements
Iterate through each element and count the length of the set
Update the maximum length
Use a while loop to iterate through the set until a duplicate element is found.
None
None
    
### >> Comparison: 525 Contiguous Array [Medium] *VS* 565 Array Nesting [Medium]
> Similarity distance: 0.4992
##### Similarities

- Both questions are categorized as medium difficulty.
- Both questions involve arrays.
- Both questions require finding a contiguous subarray.
##### Differences

- 525 Contiguous Array requires finding the maximum length of a contiguous subarray with equal number of 0 and 1.
- 565 Array Nesting requires finding the length of the longest set of consecutive elements in an array.
##### New Insights in 565 Array Nesting [Medium]

- In 525 Contiguous Array, we can convert all 0s to -1s and then find the maximum length of a subarray with sum 0.
- In 565 Array Nesting, we can mark visited elements as -1 to avoid counting them again.


---
# 6. From 565 Array Nesting [Medium] to 485 Max Consecutive Ones [Easy]
> Similarity Distance: 0.5085

### >> Reminder: 565 Array Nesting [Medium]
You are given an integer array nums of length n where nums is a permutation of the numbers in the range [0, n - 1]. You should build a set s[k] = {nums[k], nums[nums[k]], nums[nums[nums[k]]], ... } subjected to the following rule:

The first element in s[k] starts with the selection of the element nums[k] of index = k.
The next element in s[k] should be nums[nums[k]], and then nums[nums[nums[k]]], and so on.
We stop adding right before a duplicate element occurs in s[k].
Return the longest length of a set s[k].
##### Optimal Python solution:
```python
def arrayNesting(nums):
    n = len(nums)
    visited = [False] * n
    ans = 0
    for i in range(n):
        if not visited[i]:
            start = nums[i]
            count = 0
            while True:
                start = nums[start]
                count += 1
                visited[start] = True
                if start == nums[i]:
                    break
            ans = max(ans, count)
    return ans
```
Given an array of integers, find the longest length of a set where each element is the index of the next element in the set.
    
### >> 485 Max Consecutive Ones [Easy]
Given a binary array, find the maximum number of consecutive 1s in this array.
##### Sample input:
[1,1,0,1,1,1]
##### Sample output:
3

##### Questions to ask to clarify requirements:
Are there any constraints on the length of the array? Can the array be empty?

##### Optimal Python solution:
```python
def findMaxConsecutiveOnes(nums):
    max_count = 0
    count = 0
    for num in nums:
        if num == 1:
            count += 1
            max_count = max(max_count, count)
        else:
            count = 0
    return max_count
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a variable to keep track of the maximum count of consecutive ones.
2. Iterate through the array and update the count of consecutive ones.
3. Reset the count when encountering a zero.
4. Return the maximum count.
None
None
None
    
### >> Comparison: 565 Array Nesting [Medium] *VS* 485 Max Consecutive Ones [Easy]
> Similarity distance: 0.5085
##### Similarities

- Both questions involve manipulating arrays.
- Both questions require finding a consecutive sequence in the array.
- Both questions have a time complexity of O(n).
##### Differences

- Question 565 involves finding the length of the longest nesting sequence in the array, while question 485 involves finding the maximum number of consecutive ones in the array.
- Question 565 requires using a set to keep track of visited indices, while question 485 does not require any additional data structure.
- Question 565 requires iterating through the array and checking if the current index has been visited, while question 485 only requires counting consecutive ones.
- Question 565 has a nested loop to find the nesting sequence, while question 485 only requires a single loop to count consecutive ones.
##### New Insights in 485 Max Consecutive Ones [Easy]

- Question 565 introduces the concept of nesting sequences in arrays.
- Question 485 demonstrates a simple approach to counting consecutive ones in an array.


---
# 7. From 496 Next Greater Element I [Easy] to 503 Next Greater Element II [Medium]
> Similarity Distance: 0.5214

### >> Reminder: 496 Next Greater Element I [Easy]
You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.
##### Optimal Python solution:
```python
def nextGreaterElement(nums1, nums2):
    stack = []
    next_greater = {}
    for num in nums2:
        while stack and stack[-1] < num:
            next_greater[stack.pop()] = num
        stack.append(num)
    return [next_greater.get(num, -1) for num in nums1]
```
Use stack to track next greater elements.
    
### >> 503 Next Greater Element II [Medium]
Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.
##### Sample input:
[1,2,1]
##### Sample output:
[2,-1,2]

##### Questions to ask to clarify requirements:
What should be the output if the input array is empty?

##### Optimal Python solution:
```python
def nextGreaterElements(nums):
    n = len(nums)
    stack = []
    res = [-1] * n
    for i in range(2 * n):
        while stack and nums[stack[-1]] < nums[i % n]:
            res[stack.pop()] = nums[i % n]
        stack.append(i % n)
    return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to store the indices of the elements in the array.
2. Iterate through the array twice to handle the circular nature.
3. For each element, pop elements from the stack until a greater element is found.
4. Store the next greater element in the result array.
5. If no greater element is found, store -1.
6. Return the result array.
1. Understand the problem statement and the requirements.
2. Use a stack to keep track of the indices of the elements.
3. Iterate through the array twice to handle the circular nature.
4. Use modulo operator to handle the circular indexing.
5. Pop elements from the stack until a greater element is found.
6. Store the next greater element in the result array.
7. If no greater element is found, store -1.
8. Return the result array.
Handling the circular nature of the array.
Using nested loops to find the next greater element.
    
### >> Comparison: 496 Next Greater Element I [Easy] *VS* 503 Next Greater Element II [Medium]
> Similarity distance: 0.5214
##### Similarities

- Both questions are about finding the next greater element in an array.
- Both questions have a similar input format: an array of integers.
##### Differences

- Question 496 is classified as Easy, while question 503 is classified as Medium.
- In question 496, the next greater element is to be found in the same array, while in question 503, the array is circular and the next greater element can be found in a circular manner.
- Question 496 has a constraint that the input array will have distinct elements, while question 503 does not have this constraint.
##### New Insights in 503 Next Greater Element II [Medium]

- Question 503 introduces the concept of circular arrays and finding the next greater element in a circular manner.
- Both questions provide an opportunity to practice array manipulation and understanding of stack data structure.


---
# 8. From 503 Next Greater Element II [Medium] to 239 Sliding Window Maximum [Hard]
> Similarity Distance: 0.5440

### >> Reminder: 503 Next Greater Element II [Medium]
Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.
##### Optimal Python solution:
```python
def nextGreaterElements(nums):
    n = len(nums)
    stack = []
    res = [-1] * n
    for i in range(2 * n):
        while stack and nums[stack[-1]] < nums[i % n]:
            res[stack.pop()] = nums[i % n]
        stack.append(i % n)
    return res
```
The essence of this problem is to find the next greater element for each element in a circular array.
    
### >> 239 Sliding Window Maximum [Hard]
Given an array nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.
##### Sample input:
[1,3,-1,-3,5,3,6,7]
3
##### Sample output:
[3,3,5,5,6,7]

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the array contain negative numbers? What should be returned if the array is empty?

##### Optimal Python solution:
```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        if not nums:
            return []
        if k == 0:
            return nums
        res = []
        window = []
        for i, num in enumerate(nums):
            if i >= k and window[0] <= i - k:
                window.pop(0)
            while window and nums[window[-1]] <= num:
                window.pop()
            window.append(i)
            if i >= k - 1:
                res.append(nums[window[0]])
        return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(k)
##### Notes:
1. Use a sliding window to keep track of the maximum element
2. Use a deque to store the indices of the elements in the window
3. Remove indices that are out of the window
4. Remove indices of elements that are smaller than the current element
5. Append the index of the current element to the deque
6. Append the maximum element in the window to the result
1. Use a deque to efficiently remove indices that are out of the window and indices of elements that are smaller than the current element
2. Use the sliding window technique to solve problems where we need to perform a certain operation on a fixed-size window as it moves through the array
1. Using a deque to store the indices instead of the elements
2. Removing indices that are out of the window
3. Removing indices of elements that are smaller than the current element
1. Using a sorted data structure to keep track of the maximum element
2. Using a nested loop to find the maximum element in each window
    
### >> Comparison: 503 Next Greater Element II [Medium] *VS* 239 Sliding Window Maximum [Hard]
> Similarity distance: 0.5440
##### Similarities

- Both questions involve finding the maximum element in a sliding window.
##### Differences

- 503 Next Greater Element II requires finding the next greater element for each element in a circular array.
- 239 Sliding Window Maximum requires finding the maximum element in a sliding window of fixed size.
##### New Insights in 239 Sliding Window Maximum [Hard]

- 503 Next Greater Element II introduces the concept of a circular array and requires handling wrap-around scenarios.
- 239 Sliding Window Maximum introduces the concept of a sliding window and requires efficient data structure and algorithm choices to find the maximum element.

