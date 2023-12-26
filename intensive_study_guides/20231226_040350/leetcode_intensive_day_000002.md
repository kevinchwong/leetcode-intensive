
# Leetcode Intensive Tutorial Day 2 
> [Difficulty Score: 10]

> [Version: 20231226_040350]

> [Including this day, you had studied : 14 leetcode problems]


## Courses overview of the day

- 88 Merge Sorted Array [Easy]
  - 283 Move Zeroes [Easy]
  - 18 4Sum [Medium]
    - 167 Two Sum II - Input array is sorted [Easy]
    - 27 Remove Element [Easy]
      - 540 Single Element in a Sorted Array [Medium]
        - 74 Search a 2D Matrix [Medium]

#### Step by step

 - [1. From 88 Merge Sorted Array [Easy] to 283 Move Zeroes [Easy]](#1-from-88-merge-sorted-array-easy-to-283-move-zeroes-easy))

 - [2. From 88 Merge Sorted Array [Easy] to 18 4Sum [Medium]](#2-from-88-merge-sorted-array-easy-to-18-4sum-medium))

 - [3. From 18 4Sum [Medium] to 167 Two Sum II - Input array is sorted [Easy]](#3-from-18-4sum-medium-to-167-two-sum-ii---input-array-is-sorted-easy))

 - [4. From 18 4Sum [Medium] to 27 Remove Element [Easy]](#4-from-18-4sum-medium-to-27-remove-element-easy))

 - [5. From 27 Remove Element [Easy] to 540 Single Element in a Sorted Array [Medium]](#5-from-27-remove-element-easy-to-540-single-element-in-a-sorted-array-medium))

 - [6. From 540 Single Element in a Sorted Array [Medium] to 74 Search a 2D Matrix [Medium]](#6-from-540-single-element-in-a-sorted-array-medium-to-74-search-a-2d-matrix-medium))

    

#### Summary


- 540 Single Element in a Sorted Array : Given a sorted array with duplicate elements, find the single element.
- 88 Merge Sorted Array : The essence of this problem is to use two pointers to merge two sorted arrays in-place.
- 18 4Sum : The essence of this problem is to find all unique quadruplets in the array that sum up to the target.
- 167 Two Sum II - Input array is sorted : Given a sorted array, find two numbers that add up to a target number.
- 27 Remove Element : Remove all instances of a value from an array in-place.
- 283 Move Zeroes : Move non-zero elements to the front of the array while preserving their order.
- 74 Search a 2D Matrix : The essence of the problem is to perform binary search on a sorted matrix by treating it as a 1D array.
> Similarity Diameter of these problems: 0.6232


---
# 1. From 88 Merge Sorted Array [Easy] to 283 Move Zeroes [Easy]
> Similarity Distance: 0.4236

### >> 88 Merge Sorted Array [Easy]
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
##### Sample input:
[1,2,3,0,0,0]
3
[2,5,6]
3
##### Sample output:
[1,2,2,3,5,6]

##### Questions to ask to clarify requirements:
Can the input arrays be empty? Can the input arrays contain negative numbers?

##### Optimal Python solution:
```python
def merge(nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    i = m - 1
    j = n - 1
    k = m + n - 1
    while i >= 0 and j >= 0:
        if nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1
    while j >= 0:
        nums1[k] = nums2[j]
        j -= 1
        k -= 1
```
##### Time complexity:
O(m + n)
##### Space complexity:
O(1)
##### Notes:
1. Use two pointers to merge the arrays in-place.
2. Start from the end of the arrays and compare the elements.
3. Time complexity is O(m + n) and space complexity is O(1), where m and n are the lengths of the arrays.
Be careful with the indices when merging the arrays in-place.
Be careful with the indices when merging the arrays in-place.
Avoid using extra space to store the merged array.
    
### >> 283 Move Zeroes [Easy]
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.
##### Sample input:
[0,1,0,3,12]
##### Sample output:
[1,3,12,0,0]

##### Questions to ask to clarify requirements:
Do we need to preserve the order of non-zero elements?

##### Optimal Python solution:
```python
def moveZeroes(nums):
    zero_count = 0
    for i in range(len(nums)):
        if nums[i] != 0:
            nums[i], nums[zero_count] = nums[zero_count], nums[i]
            zero_count += 1
    return nums
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to keep track of the current position and the position of the next non-zero element
- Swap the current element with the next non-zero element
- Increment the pointer for non-zero elements
Try to minimize the number of operations by swapping elements only when necessary.
None
None
    
### >> Comparison: 88 Merge Sorted Array [Easy] *VS* 283 Move Zeroes [Easy]
> Similarity distance: 0.4236
##### Similarities

- Both questions are categorized as 'Easy' level.
- Both questions involve manipulating arrays.
- Both questions require rearranging elements in the array.
##### Differences

- Merge Sorted Array involves merging two sorted arrays into one sorted array.
- Move Zeroes involves moving all the zeroes in the array to the end while maintaining the relative order of the non-zero elements.
##### New Insights in 283 Move Zeroes [Easy]

- Merge Sorted Array teaches us how to merge two sorted arrays efficiently.
- Move Zeroes teaches us how to manipulate arrays by moving elements while maintaining their relative order.


---
# 2. From 88 Merge Sorted Array [Easy] to 18 4Sum [Medium]
> Similarity Distance: 0.4309

### >> Reminder: 88 Merge Sorted Array [Easy]
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
##### Optimal Python solution:
```python
def merge(nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    i = m - 1
    j = n - 1
    k = m + n - 1
    while i >= 0 and j >= 0:
        if nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1
    while j >= 0:
        nums1[k] = nums2[j]
        j -= 1
        k -= 1
```
The essence of this problem is to use two pointers to merge two sorted arrays in-place.
    
### >> 18 4Sum [Medium]
Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.
##### Sample input:
[1,0,-1,0,-2,2]
0
##### Sample output:
[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

##### Questions to ask to clarify requirements:
Can the input array contain duplicate elements? Can the output contain duplicate quadruplets?

##### Optimal Python solution:
```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        result = []
        for i in range(n - 3):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            for j in range(i + 1, n - 2):
                if j > i + 1 and nums[j] == nums[j - 1]:
                    continue
                left = j + 1
                right = n - 1
                while left < right:
                    total = nums[i] + nums[j] + nums[left] + nums[right]
                    if total == target:
                        result.append([nums[i], nums[j], nums[left], nums[right]])
                        while left < right and nums[left] == nums[left + 1]:
                            left += 1
                        while left < right and nums[right] == nums[right - 1]:
                            right -= 1
                        left += 1
                        right -= 1
                    elif total < target:
                        left += 1
                    else:
                        right -= 1
        return result
```
##### Time complexity:
O(n^3)
##### Space complexity:
O(1)
##### Notes:
1. Sort the input array in ascending order.
2. Use two nested loops to iterate through each pair of elements.
3. Use two pointers to find the remaining two elements that sum up to the target.
4. Skip duplicate elements to avoid duplicate quadruplets.
5. Update the pointers based on the sum of the four elements.
6. Return the unique quadruplets as the result.
1. Sort the input array in ascending order.
2. Use two nested loops to iterate through each pair of elements.
3. Use two pointers to find the remaining two elements that sum up to the target.
4. Skip duplicate elements to avoid duplicate quadruplets.
5. Update the pointers based on the sum of the four elements.
6. Return the unique quadruplets as the result.
The input array needs to be sorted in ascending order to skip duplicate elements.
Avoid using recursion as it can lead to stack overflow for large inputs.
    
### >> Comparison: 88 Merge Sorted Array [Easy] *VS* 18 4Sum [Medium]
> Similarity distance: 0.4309
##### Similarities

- Both questions involve manipulating arrays.
- Both questions require sorting the input arrays.
- Both questions involve finding combinations of elements from the arrays.
##### Differences

- Merge Sorted Array merges two sorted arrays into one, while 4Sum finds four elements that sum up to a target value.
- Merge Sorted Array modifies one of the input arrays, while 4Sum does not modify the input arrays.
- Merge Sorted Array has a time complexity of O(m+n), where m and n are the lengths of the input arrays, while 4Sum has a time complexity of O(n^3), where n is the length of the input array.
##### New Insights in 18 4Sum [Medium]

- Merge Sorted Array can be solved by starting from the end of the merged array and comparing elements from the input arrays.
- 4Sum can be solved by using a combination of two-pointer technique and sorting the input array.


---
# 3. From 18 4Sum [Medium] to 167 Two Sum II - Input array is sorted [Easy]
> Similarity Distance: 0.3170

### >> Reminder: 18 4Sum [Medium]
Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.
##### Optimal Python solution:
```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        result = []
        for i in range(n - 3):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            for j in range(i + 1, n - 2):
                if j > i + 1 and nums[j] == nums[j - 1]:
                    continue
                left = j + 1
                right = n - 1
                while left < right:
                    total = nums[i] + nums[j] + nums[left] + nums[right]
                    if total == target:
                        result.append([nums[i], nums[j], nums[left], nums[right]])
                        while left < right and nums[left] == nums[left + 1]:
                            left += 1
                        while left < right and nums[right] == nums[right - 1]:
                            right -= 1
                        left += 1
                        right -= 1
                    elif total < target:
                        left += 1
                    else:
                        right -= 1
        return result
```
The essence of this problem is to find all unique quadruplets in the array that sum up to the target.
    
### >> 167 Two Sum II - Input array is sorted [Easy]
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

Note:

- Your returned answers (both index1 and index2) are not zero-based.
- You may assume that each input would have exactly one solution and you may not use the same element twice.

Example:

Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
##### Sample input:
[2,7,11,15], 9
##### Sample output:
[1,2]

##### Questions to ask to clarify requirements:
Are the numbers always sorted in ascending order? Can the input array be empty?

##### Optimal Python solution:
```python
def twoSum(numbers, target):
    left, right = 0, len(numbers) - 1
    while left < right:
        curr_sum = numbers[left] + numbers[right]
        if curr_sum == target:
            return [left + 1, right + 1]
        elif curr_sum < target:
            left += 1
        else:
            right -= 1
    return []
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use two pointers to traverse the array.
2. Adjust the pointers based on the sum of the current numbers.
3. Return the indices of the numbers that add up to the target.
1. Remember to adjust the pointers based on the sum of the current numbers.
2. Be careful with the indices, as they are not zero-based.
None
None
    
### >> Comparison: 18 4Sum [Medium] *VS* 167 Two Sum II - Input array is sorted [Easy]
> Similarity distance: 0.3170
##### Similarities

- Both questions involve finding pairs of numbers that add up to a target value.
- Both questions require manipulating an array of numbers.
- Both questions have a time complexity of O(n^2) in the worst case.
##### Differences

- 4Sum involves finding four numbers that add up to a target value, while Two Sum II involves finding two numbers.
- 4Sum allows duplicate numbers in the array, while Two Sum II does not.
- 4Sum has a higher time complexity of O(n^3) in the worst case, while Two Sum II has a time complexity of O(n).
##### New Insights in 167 Two Sum II - Input array is sorted [Easy]

- In 4Sum, we can use a combination of two pointers and recursion to find all possible combinations of four numbers that add up to the target value.
- In Two Sum II, we can use a two-pointer approach to find the two numbers that add up to the target value efficiently.


---
# 4. From 18 4Sum [Medium] to 27 Remove Element [Easy]
> Similarity Distance: 0.4304

### >> Reminder: 18 4Sum [Medium]
Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.
##### Optimal Python solution:
```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        result = []
        for i in range(n - 3):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            for j in range(i + 1, n - 2):
                if j > i + 1 and nums[j] == nums[j - 1]:
                    continue
                left = j + 1
                right = n - 1
                while left < right:
                    total = nums[i] + nums[j] + nums[left] + nums[right]
                    if total == target:
                        result.append([nums[i], nums[j], nums[left], nums[right]])
                        while left < right and nums[left] == nums[left + 1]:
                            left += 1
                        while left < right and nums[right] == nums[right - 1]:
                            right -= 1
                        left += 1
                        right -= 1
                    elif total < target:
                        left += 1
                    else:
                        right -= 1
        return result
```
The essence of this problem is to find all unique quadruplets in the array that sum up to the target.
    
### >> 27 Remove Element [Easy]
Given an array nums and a value val, remove all instances of that value in-place and return the new length.
##### Sample input:
[3,2,2,3]
3
##### Sample output:
2
[2,2]

##### Questions to ask to clarify requirements:
Can the array contain duplicate values? Can the array be empty?

##### Optimal Python solution:
```python
def removeElement(nums, val):
    i = 0
    for j in range(len(nums)):
        if nums[j] != val:
            nums[i] = nums[j]
            i += 1
    return i
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use two pointers to iterate through the array. If the current element is not equal to the target value, move it to the left pointer and increment the left pointer.
Make sure to handle edge cases such as an empty array or an array with no instances of the target value.
None
None
    
### >> Comparison: 18 4Sum [Medium] *VS* 27 Remove Element [Easy]
> Similarity distance: 0.4304
##### Similarities
Both questions involve manipulating arrays.
##### Differences
4Sum involves finding four numbers in an array that sum up to a target value, while Remove Element involves removing all instances of a specific value from an array.
##### New Insights in 27 Remove Element [Easy]
In 4Sum, we can use a combination of two pointers and a nested loop to find the four numbers that sum up to the target value. In Remove Element, we can use two pointers to swap elements and remove the target value efficiently.


---
# 5. From 27 Remove Element [Easy] to 540 Single Element in a Sorted Array [Medium]
> Similarity Distance: 0.5114

### >> Reminder: 27 Remove Element [Easy]
Given an array nums and a value val, remove all instances of that value in-place and return the new length.
##### Optimal Python solution:
```python
def removeElement(nums, val):
    i = 0
    for j in range(len(nums)):
        if nums[j] != val:
            nums[i] = nums[j]
            i += 1
    return i
```
Remove all instances of a value from an array in-place.
    
### >> 540 Single Element in a Sorted Array [Medium]
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once, find this single element that appears only once.
##### Sample input:

- [1,1,2,3,3,4,4,8,8]
- [3,3,7,7,10,11,11]
##### Sample output:

- 2
- 10

##### Questions to ask to clarify requirements:

- Can the array be empty?
- Can the array contain negative numbers?

##### Optimal Python solution:
```python

- def singleNonDuplicate(nums):
-     left = 0
-     right = len(nums) - 1
-     while left < right:
-         mid = (left + right) // 2
-         if mid % 2 == 1:
-             mid -= 1
-         if nums[mid] == nums[mid + 1]:
-             left = mid + 2
-         else:
-             right = mid
-     return nums[left]
```
##### Time complexity:
O(logn)
##### Space complexity:
O(1)
##### Notes:

- Use binary search to find the single element
- Check if the middle element is the single element by comparing it with its adjacent element
- Update the left or right pointer based on the comparison result

- Use the modulo operator to handle the case where the single element is at an odd index

- Handling the case where the single element is at an odd index

- Using linear search to find the single element
    
### >> Comparison: 27 Remove Element [Easy] *VS* 540 Single Element in a Sorted Array [Medium]
> Similarity distance: 0.5114
##### Similarities

- Both questions involve manipulating an array.
- Both questions require removing elements from the array.
- Both questions have a target element that needs to be removed.
##### Differences

- Question 27 is classified as Easy, while question 540 is classified as Medium.
- Question 27 requires removing all instances of the target element, while question 540 requires finding the single element in the array.
- Question 27 allows modifying the original array, while question 540 requires a solution with a time complexity of O(log n).
##### New Insights in 540 Single Element in a Sorted Array [Medium]

- Question 27 can be solved by using two pointers to swap elements, while question 540 can be solved using binary search.
- Both questions require careful handling of array indices to avoid out-of-bounds errors.
- Question 540 introduces the concept of finding a single element in a sorted array using binary search, which can be a useful technique in other problems.


---
# 6. From 540 Single Element in a Sorted Array [Medium] to 74 Search a 2D Matrix [Medium]
> Similarity Distance: 0.4440

### >> Reminder: 540 Single Element in a Sorted Array [Medium]
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once, find this single element that appears only once.
##### Optimal Python solution:
```python

- def singleNonDuplicate(nums):
-     left = 0
-     right = len(nums) - 1
-     while left < right:
-         mid = (left + right) // 2
-         if mid % 2 == 1:
-             mid -= 1
-         if nums[mid] == nums[mid + 1]:
-             left = mid + 2
-         else:
-             right = mid
-     return nums[left]
```
Given a sorted array with duplicate elements, find the single element.
    
### >> 74 Search a 2D Matrix [Medium]
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties: Integers in each row are sorted from left to right. The first integer of each row is greater than the last integer of the previous row.
##### Sample input:
[[1,3,5,7],[10,11,16,20],[23,30,34,60]]
3
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the matrix be empty? Can the target be negative?

##### Optimal Python solution:
```python
def searchMatrix(matrix, target):
    m, n = len(matrix), len(matrix[0])
    left, right = 0, m * n - 1

    while left <= right:
        mid = (left + right) // 2
        row, col = mid // n, mid % n
        if matrix[row][col] == target:
            return True
        elif matrix[row][col] < target:
            left = mid + 1
        else:
            right = mid - 1

    return False
```
##### Time complexity:
O(log(m * n))
##### Space complexity:
O(1)
##### Notes:
1. Use binary search to find the target in the matrix.
2. Treat the matrix as a 1D array and perform binary search on it.
3. Convert the 1D index to 2D row and column indices.
4. Update the left and right pointers based on the comparison between the target and the middle element.
5. Repeat the binary search until the target is found or the left and right pointers cross each other.
1. Treat the matrix as a 1D array and perform binary search on it.
2. Convert the 1D index to 2D row and column indices.
3. Update the left and right pointers based on the comparison between the target and the middle element.
The tricky part is to convert the 1D index to 2D row and column indices.
Avoid using extra space.
    
### >> Comparison: 540 Single Element in a Sorted Array [Medium] *VS* 74 Search a 2D Matrix [Medium]
> Similarity distance: 0.4440
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve searching for an element in an array or matrix.
- Both questions require efficient algorithms to solve.
##### Differences

- Question 540 involves finding a single element in a sorted array, while question 74 involves searching for an element in a 2D matrix.
- Question 540 requires finding the element that appears only once in the array, while question 74 requires finding the element in the matrix.
- Question 540 can be solved using binary search, while question 74 requires a different approach.
- Question 540 has a time complexity of O(log n), while question 74 has a time complexity of O(m + n).
##### New Insights in 74 Search a 2D Matrix [Medium]

- Question 540 introduces the concept of finding a single element in a sorted array efficiently.
- Question 74 introduces the concept of searching for an element in a 2D matrix using a specific algorithm.

