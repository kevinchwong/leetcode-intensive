
# Leetcode Intensive Tutorial Day 51 
> [Difficulty Score: 24]

> [Version: 20231226_040350]

> [Including this day, you had studied : 431 leetcode problems]


## Courses overview of the day

- 34 Find First and Last Position of Element in Sorted Array [Medium]
  - 33 Search in Rotated Sorted Array [Medium]
    - 81 Search in Rotated Sorted Array II [Medium]
      - 230 Kth Smallest Element in a BST [Medium]
        - 440 K-th Smallest in Lexicographical Order [Hard]
        - 378 Kth Smallest Element in a Sorted Matrix [Medium]
        - 162 Find Peak Element [Medium]
        - 483 Smallest Good Base [Hard]
      - 398 Random Pick Index [Medium]
        - 528 Random Pick with Weight [Medium]

#### Step by step

 - [1. From 34 Find First and Last Position of Element in Sorted Array [Medium] to 33 Search in Rotated Sorted Array [Medium]](#1-from-34-find-first-and-last-position-of-element-in-sorted-array-medium-to-33-search-in-rotated-sorted-array-medium))

 - [2. From 33 Search in Rotated Sorted Array [Medium] to 81 Search in Rotated Sorted Array II [Medium]](#2-from-33-search-in-rotated-sorted-array-medium-to-81-search-in-rotated-sorted-array-ii-medium))

 - [3. From 81 Search in Rotated Sorted Array II [Medium] to 230 Kth Smallest Element in a BST [Medium]](#3-from-81-search-in-rotated-sorted-array-ii-medium-to-230-kth-smallest-element-in-a-bst-medium))

 - [4. From 230 Kth Smallest Element in a BST [Medium] to 440 K-th Smallest in Lexicographical Order [Hard]](#4-from-230-kth-smallest-element-in-a-bst-medium-to-440-k-th-smallest-in-lexicographical-order-hard))

 - [5. From 230 Kth Smallest Element in a BST [Medium] to 378 Kth Smallest Element in a Sorted Matrix [Medium]](#5-from-230-kth-smallest-element-in-a-bst-medium-to-378-kth-smallest-element-in-a-sorted-matrix-medium))

 - [6. From 230 Kth Smallest Element in a BST [Medium] to 162 Find Peak Element [Medium]](#6-from-230-kth-smallest-element-in-a-bst-medium-to-162-find-peak-element-medium))

 - [7. From 230 Kth Smallest Element in a BST [Medium] to 483 Smallest Good Base [Hard]](#7-from-230-kth-smallest-element-in-a-bst-medium-to-483-smallest-good-base-hard))

 - [8. From 81 Search in Rotated Sorted Array II [Medium] to 398 Random Pick Index [Medium]](#8-from-81-search-in-rotated-sorted-array-ii-medium-to-398-random-pick-index-medium))

 - [9. From 398 Random Pick Index [Medium] to 528 Random Pick with Weight [Medium]](#9-from-398-random-pick-index-medium-to-528-random-pick-with-weight-medium))

    

#### Summary


- 34 Find First and Last Position of Element in Sorted Array : The essence of this problem is to use binary search to find the leftmost and rightmost occurrences of the target in a sorted array by adjusting the search range based on the comparison with the target.
- 378 Kth Smallest Element in a Sorted Matrix : The essence of this problem is to find the kth smallest element in a sorted matrix using a min heap.
- 483 Smallest Good Base : The essence of this problem is to find the smallest good base of a given number n.
- 398 Random Pick Index : The essence of the problem is to randomly select an index of a given target number in an array.
- 33 Search in Rotated Sorted Array : The essence of this problem is to use binary search to find the target in a rotated sorted array by dividing the array into two parts and adjusting the search range based on the sorted part.
- 440 K-th Smallest in Lexicographical Order : Find the k-th smallest integer in lexicographical order.
- 162 Find Peak Element : Finding a peak element in an array using binary search.
- 81 Search in Rotated Sorted Array II : Binary search to find target in rotated sorted array with duplicates.
- 528 Random Pick with Weight : The essence of the problem is to randomly pick an index in proportion to its weight.
- 230 Kth Smallest Element in a BST : The essence of this problem is to perform an inorder traversal of a binary search tree to find the kth smallest element.
> Similarity Diameter of these problems: 0.6793


---
# 1. From 34 Find First and Last Position of Element in Sorted Array [Medium] to 33 Search in Rotated Sorted Array [Medium]
> Similarity Distance: 0.4219

### >> 34 Find First and Last Position of Element in Sorted Array [Medium]
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value. If the target is not found in the array, return [-1, -1]. You must write an algorithm with O(log n) runtime complexity.
##### Sample input:
[5,7,7,8,8,10]
8
##### Sample output:
[3,4]

##### Questions to ask to clarify requirements:
Can the array contain duplicates? What should be returned if the array is empty?

##### Optimal Python solution:
```python
def searchRange(nums, target):
    def findLeft(nums, target):
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
    def findRight(nums, target):
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] <= target:
                left = mid + 1
            else:
                right = mid - 1
        return right
    left = findLeft(nums, target)
    right = findRight(nums, target)
    if left <= right:
        return [left, right]
    else:
        return [-1, -1]
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Use binary search to find the leftmost and rightmost occurrences of the target.
2. Implement separate functions to find the leftmost and rightmost occurrences.
3. Adjust the search range based on the comparison with the target.
1. Understand the concept of binary search.
2. Implement separate functions to find the leftmost and rightmost occurrences.
3. Test the solution with different inputs to ensure correctness.
1. Handling the case when the target is not found.
2. Determining the leftmost and rightmost occurrences of the target.
1. Using linear search instead of binary search.
2. Not considering the case when the target is not found.
3. Not handling duplicates in the array.
    
### >> 33 Search in Rotated Sorted Array [Medium]
You are given an integer array nums sorted in ascending order (with distinct values), and an integer target. Suppose that nums is rotated at some pivot unknown to you beforehand (i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]). You should search for target in nums and if you found return its index, otherwise return -1.
##### Sample input:
[4,5,6,7,0,1,2]
0
##### Sample output:
4

##### Questions to ask to clarify requirements:
Can the array contain duplicates? What should be returned if the array is empty?

##### Optimal Python solution:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target <= nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] <= target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Use binary search to find the target.
2. Divide the array into two parts and determine which part is sorted.
3. Adjust the search range based on the sorted part of the array.
1. Understand the concept of binary search.
2. Pay attention to the conditions for updating the search range.
3. Test the solution with different inputs to ensure correctness.
1. Handling the case when the array is rotated.
2. Determining which part of the array is sorted.
1. Using linear search instead of binary search.
2. Not considering the case when the array is rotated.
3. Not handling the case when the target is not in the array.
    
### >> Comparison: 34 Find First and Last Position of Element in Sorted Array [Medium] *VS* 33 Search in Rotated Sorted Array [Medium]
> Similarity distance: 0.4219
##### Similarities

- Both questions are related to searching for an element in a sorted array.
- Both questions have a time complexity requirement of O(log n).
##### Differences

- Question 34 focuses on finding the first and last position of an element in a sorted array, while question 33 focuses on searching for an element in a rotated sorted array.
- Question 34 requires finding the first and last position, while question 33 only requires finding the existence of the element.
- Question 34 can be solved using binary search twice, while question 33 requires a modified binary search algorithm to handle the rotated array.
##### New Insights in 33 Search in Rotated Sorted Array [Medium]

- Question 34 teaches us how to modify the binary search algorithm to find the first and last position of an element in a sorted array.
- Question 33 teaches us how to handle the rotated sorted array and perform a modified binary search to find an element.


---
# 2. From 33 Search in Rotated Sorted Array [Medium] to 81 Search in Rotated Sorted Array II [Medium]
> Similarity Distance: 0.3797

### >> Reminder: 33 Search in Rotated Sorted Array [Medium]
You are given an integer array nums sorted in ascending order (with distinct values), and an integer target. Suppose that nums is rotated at some pivot unknown to you beforehand (i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]). You should search for target in nums and if you found return its index, otherwise return -1.
##### Optimal Python solution:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target <= nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] <= target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```
The essence of this problem is to use binary search to find the target in a rotated sorted array by dividing the array into two parts and adjusting the search range based on the sorted part.
    
### >> 81 Search in Rotated Sorted Array II [Medium]
Given an array of integers nums and an integer target, return true if target is in the array, and false otherwise.
##### Sample input:
[2,5,6,0,0,1,2], 0
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the array contain duplicates?
- Can the array be empty?
- What is the range of the integers in the array?

##### Optimal Python solution:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return True
        while left < mid and nums[left] == nums[mid]:
            left += 1
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return False
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:

- Use binary search to find the target element.
- Handle the case where the array contains duplicates by skipping duplicate elements.
- Handle the case where the array is rotated by checking the order of elements at the left and right boundaries.

- Use the binary search algorithm to efficiently find the target element.
- Handle the case where the array contains duplicates by skipping duplicate elements.
- Handle the case where the array is rotated by checking the order of elements at the left and right boundaries.

- Handling the case where the array contains duplicates.
- Handling the case where the array is rotated.

- Using linear search.
- Using extra space.
    
### >> Comparison: 33 Search in Rotated Sorted Array [Medium] *VS* 81 Search in Rotated Sorted Array II [Medium]
> Similarity distance: 0.3797
##### Similarities

- Both questions involve searching for a target element in a rotated sorted array.
##### Differences

- Question 33 assumes that there are no duplicates in the array, while question 81 allows duplicates.
- Question 33 guarantees that the target element is always present in the array, while question 81 does not provide this guarantee.
##### New Insights in 81 Search in Rotated Sorted Array II [Medium]

- Both questions can be solved using a modified binary search algorithm.
- In question 33, we can determine the pivot point of the rotated array to perform the search.
- In question 81, we need to handle the case of duplicates by adjusting the search range.


---
# 3. From 81 Search in Rotated Sorted Array II [Medium] to 230 Kth Smallest Element in a BST [Medium]
> Similarity Distance: 0.5119

### >> Reminder: 81 Search in Rotated Sorted Array II [Medium]
Given an array of integers nums and an integer target, return true if target is in the array, and false otherwise.
##### Optimal Python solution:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return True
        while left < mid and nums[left] == nums[mid]:
            left += 1
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return False
```
Binary search to find target in rotated sorted array with duplicates.
    
### >> 230 Kth Smallest Element in a BST [Medium]
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
##### Sample input:
root = [3,1,4,null,2], k = 1
##### Sample output:
1

##### Questions to ask to clarify requirements:
Can the binary search tree contain duplicate values? What should be returned if k is larger than the number of elements in the tree?

##### Optimal Python solution:
```python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
##### Time complexity:
O(k)
##### Space complexity:
O(h)
##### Notes:
1. Perform an inorder traversal of the binary search tree using a stack.
2. Keep track of the number of elements visited to find the kth smallest element.
Understand how the inorder traversal and stack are used to find the kth smallest element.
The solution uses a stack to simulate the inorder traversal of the binary search tree.
Performing a complete inorder traversal of the binary search tree.
    
### >> Comparison: 81 Search in Rotated Sorted Array II [Medium] *VS* 230 Kth Smallest Element in a BST [Medium]
> Similarity distance: 0.5119
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve searching for an element in a data structure.
- Both questions require handling special cases or conditions.
##### Differences

- The first question involves searching in a rotated sorted array, while the second question involves searching in a binary search tree.
- The first question allows duplicates in the array, while the second question does not allow duplicates in the tree.
- The first question requires a modified binary search algorithm to handle the rotated array, while the second question uses the standard binary search algorithm.
- The first question has a time complexity of O(log n), while the second question has a time complexity of O(k + log n), where k is the value of kth smallest element.
##### New Insights in 230 Kth Smallest Element in a BST [Medium]

- From the first question, we can learn how to modify the binary search algorithm to handle special cases like a rotated sorted array.
- From the second question, we can learn how to find the kth smallest element in a binary search tree efficiently.


---
# 4. From 230 Kth Smallest Element in a BST [Medium] to 440 K-th Smallest in Lexicographical Order [Hard]
> Similarity Distance: 0.4454

### >> Reminder: 230 Kth Smallest Element in a BST [Medium]
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
##### Optimal Python solution:
```python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
The essence of this problem is to perform an inorder traversal of a binary search tree to find the kth smallest element.
    
### >> 440 K-th Smallest in Lexicographical Order [Hard]
Given integers n and k, find the k-th smallest integer in the lexicographical order from 1 to n.
##### Sample input:
n = 13, k = 2
##### Sample output:
10

##### Questions to ask to clarify requirements:
What is the maximum value of n and k? Can n be negative?

##### Optimal Python solution:
```python
def findKthNumber(n, k):
    curr = 1
    k -= 1
    while k > 0:
        steps = calculate_steps(n, curr, curr + 1)
        if steps <= k:
            curr += 1
            k -= steps
        else:
            curr *= 10
            k -= 1
    return curr


def calculate_steps(n, n1, n2):
    steps = 0
    while n1 <= n:
        steps += min(n + 1, n2) - n1
        n1 *= 10
        n2 *= 10
    return steps
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Use a while loop to iterate until k becomes 0.
2. Calculate the number of steps between curr and curr + 1 using the calculate_steps function.
3. If steps <= k, increment curr by 1 and subtract steps from k. Otherwise, multiply curr by 10 and subtract 1 from k.
Make sure to handle the case when n is negative.
None
None
    
### >> Comparison: 230 Kth Smallest Element in a BST [Medium] *VS* 440 K-th Smallest in Lexicographical Order [Hard]
> Similarity distance: 0.4454
##### Similarities

- Both questions involve finding the kth smallest element in a given data structure.
- Both questions require traversing the data structure in a specific order.
##### Differences

- Question 230 involves a binary search tree (BST) while question 440 involves lexicographical ordering.
- Question 230 is classified as medium difficulty while question 440 is classified as hard difficulty.
- Question 230 requires finding the kth smallest element in a BST, while question 440 requires finding the kth smallest element in a lexicographically ordered sequence.
##### New Insights in 440 K-th Smallest in Lexicographical Order [Hard]

- Question 230 teaches us how to traverse a BST in order to find the kth smallest element.
- Question 440 introduces the concept of lexicographical ordering and challenges us to find the kth smallest element in such a sequence.


---
# 5. From 230 Kth Smallest Element in a BST [Medium] to 378 Kth Smallest Element in a Sorted Matrix [Medium]
> Similarity Distance: 0.4598

### >> Reminder: 230 Kth Smallest Element in a BST [Medium]
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
##### Optimal Python solution:
```python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
The essence of this problem is to perform an inorder traversal of a binary search tree to find the kth smallest element.
    
### >> 378 Kth Smallest Element in a Sorted Matrix [Medium]
Given an n x n matrix where each of the rows and columns are sorted in ascending order, return the kth smallest element in the matrix.
##### Sample input:
[[1,5,9],[10,11,13],[12,13,15]], k = 8
##### Sample output:
13

##### Questions to ask to clarify requirements:
Can the matrix contain duplicate elements? Can k be larger than the number of elements in the matrix?

##### Optimal Python solution:
```python
import heapq

def kthSmallest(matrix, k):
    n = len(matrix)
    heap = []
    for i in range(n):
        for j in range(n):
            heapq.heappush(heap, matrix[i][j])
            if len(heap) > k:
                heapq.heappop(heap)
    return heapq.heappop(heap)
```
##### Time complexity:
O(n^2 log k)
##### Space complexity:
O(k)
##### Notes:
1. Use a min heap to keep track of the k smallest elements.
2. Iterate through the matrix and add each element to the heap.
3. If the heap size exceeds k, remove the smallest element.
4. Return the smallest element in the heap as the result.
Try to optimize the solution by using a data structure that allows efficient insertion and removal of elements.
The matrix is sorted both row-wise and column-wise.
Avoid sorting the entire matrix as it would be less efficient.
    
### >> Comparison: 230 Kth Smallest Element in a BST [Medium] *VS* 378 Kth Smallest Element in a Sorted Matrix [Medium]
> Similarity distance: 0.4598
##### Similarities

- Both questions involve finding the kth smallest element in a data structure.
- Both questions have a medium difficulty level.
##### Differences

- Question 230 involves a binary search tree (BST) while question 378 involves a sorted matrix.
- Question 230 requires traversing a BST in order to find the kth smallest element, while question 378 requires searching a sorted matrix.
- Question 230 has a time complexity of O(h + k), where h is the height of the BST, while question 378 has a time complexity of O(n + k log n), where n is the size of the matrix.
- Question 230 guarantees that the kth smallest element exists in the BST, while question 378 assumes that the matrix is sorted and may not have the kth smallest element.
##### New Insights in 378 Kth Smallest Element in a Sorted Matrix [Medium]

- Question 230 introduces the concept of traversing a binary search tree to find the kth smallest element.
- Question 378 introduces the concept of searching a sorted matrix to find the kth smallest element.


---
# 6. From 230 Kth Smallest Element in a BST [Medium] to 162 Find Peak Element [Medium]
> Similarity Distance: 0.5399

### >> Reminder: 230 Kth Smallest Element in a BST [Medium]
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
##### Optimal Python solution:
```python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
The essence of this problem is to perform an inorder traversal of a binary search tree to find the kth smallest element.
    
### >> 162 Find Peak Element [Medium]
A peak element is an element that is strictly greater than its neighbors. Given an integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.
##### Sample input:
[1,2,3,1]
##### Sample output:
2

##### Questions to ask to clarify requirements:
Can the array be empty? Can the array have multiple peaks?

##### Optimal Python solution:
```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        left, right = 0, len(nums) - 1
        while left < right:
            mid = (left + right) // 2
            if nums[mid] < nums[mid + 1]:
                left = mid + 1
            else:
                right = mid
        return left
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
Use binary search to find a peak element. Compare the middle element with its neighbors to determine the direction to move.
Carefully determine the direction to move in the binary search.
Determining the direction to move in the binary search.
Using linear search.
    
### >> Comparison: 230 Kth Smallest Element in a BST [Medium] *VS* 162 Find Peak Element [Medium]
> Similarity distance: 0.5399
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve searching for an element in a given data structure.
- Both questions require a binary search approach.
##### Differences

- Question 230 involves finding the Kth smallest element in a binary search tree (BST), while question 162 involves finding a peak element in an array.
- Question 230 requires traversing a BST, while question 162 requires searching in an array.
- Question 230 has a time complexity of O(log N + K), while question 162 has a time complexity of O(log N).
##### New Insights in 162 Find Peak Element [Medium]

- Question 230 teaches us how to perform an in-order traversal of a BST to find the Kth smallest element.
- Question 162 teaches us how to find a peak element in an array using a binary search approach.


---
# 7. From 230 Kth Smallest Element in a BST [Medium] to 483 Smallest Good Base [Hard]
> Similarity Distance: 0.5602

### >> Reminder: 230 Kth Smallest Element in a BST [Medium]
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
##### Optimal Python solution:
```python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
The essence of this problem is to perform an inorder traversal of a binary search tree to find the kth smallest element.
    
### >> 483 Smallest Good Base [Hard]
For an integer n, we call k>=2 a good base of n, if all digits of n base k are 1. Now given a string representing n, you should return the smallest good base of n in string format.
##### Sample input:
13
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be negative?

##### Optimal Python solution:
```python
def smallestGoodBase(n: str) -> str:
    n = int(n)
    m_max = int(math.log(n, 2))
    for m in range(m_max, 1, -1):
        k = int(n ** (1 / m))
        if (k ** (m + 1) - 1) // (k - 1) == n:
            return str(k)
    return str(n - 1)
```
##### Time complexity:
O(log^2(n))
##### Space complexity:
O(1)
##### Notes:
1. The good base k must be between 2 and n-1.
2. The maximum value of k can be found using binary search.
3. The smallest good base can be found by iterating from the maximum value of k to 2 and checking if k is a good base for n.
Use binary search to find the maximum value of k.
Use logarithms to calculate the power of k.
The maximum value of k can be found using binary search.
Avoid brute force approach to check all possible values of k.
    
### >> Comparison: 230 Kth Smallest Element in a BST [Medium] *VS* 483 Smallest Good Base [Hard]
> Similarity distance: 0.5602
##### Similarities

- Both questions involve finding the smallest element in a given range.
- Both questions require traversing a binary search tree.
- Both questions have a time complexity of O(log n).
##### Differences

- Question 230 involves finding the kth smallest element in a BST, while question 483 involves finding the smallest good base for a given number.
- Question 230 is classified as medium difficulty, while question 483 is classified as hard difficulty.
- Question 230 requires a depth-first search approach, while question 483 requires a binary search approach.
##### New Insights in 483 Smallest Good Base [Hard]

- Question 230 teaches us how to perform an in-order traversal of a binary search tree to find the kth smallest element.
- Question 483 introduces the concept of finding the smallest good base for a given number, which involves mathematical calculations.


---
# 8. From 81 Search in Rotated Sorted Array II [Medium] to 398 Random Pick Index [Medium]
> Similarity Distance: 0.5314

### >> Reminder: 81 Search in Rotated Sorted Array II [Medium]
Given an array of integers nums and an integer target, return true if target is in the array, and false otherwise.
##### Optimal Python solution:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return True
        while left < mid and nums[left] == nums[mid]:
            left += 1
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return False
```
Binary search to find target in rotated sorted array with duplicates.
    
### >> 398 Random Pick Index [Medium]
Given an array of integers with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.
##### Sample input:
[1,2,3,3,3]

3
##### Sample output:
2 or 3 or 4

##### Questions to ask to clarify requirements:
Can the array be empty? Can the target number be negative?

##### Optimal Python solution:
```python
import random

class Solution:
    def __init__(self, nums: List[int]):
        self.nums = nums

    def pick(self, target: int) -> int:
        indices = []
        for i in range(len(self.nums)):
            if self.nums[i] == target:
                indices.append(i)
        return random.choice(indices)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Randomly output the index of a given target number in an array.
2. The target number must exist in the array.
Use a dictionary to store the indices of each element for faster lookup.
The tricky part is efficiently selecting a random index from the list of indices.
Avoid using a linear search to find the indices of the target number.
    
### >> Comparison: 81 Search in Rotated Sorted Array II [Medium] *VS* 398 Random Pick Index [Medium]
> Similarity distance: 0.5314
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve searching for elements in an array.
- Both questions require handling rotated or shuffled arrays.
- Both questions involve random selection of elements.
##### Differences

- 81 Search in Rotated Sorted Array II involves searching for a target element in a rotated sorted array, while 398 Random Pick Index involves randomly selecting an index of a target element in an array.
- 81 Search in Rotated Sorted Array II allows duplicate elements in the array, while 398 Random Pick Index assumes distinct elements in the array.
- 81 Search in Rotated Sorted Array II requires a modified binary search algorithm, while 398 Random Pick Index requires a random sampling algorithm.
##### New Insights in 398 Random Pick Index [Medium]

- From 81 Search in Rotated Sorted Array II, we can learn how to modify the binary search algorithm to handle rotated arrays and duplicate elements.
- From 398 Random Pick Index, we can learn how to efficiently select a random index of a target element in an array.


---
# 9. From 398 Random Pick Index [Medium] to 528 Random Pick with Weight [Medium]
> Similarity Distance: 0.4669

### >> Reminder: 398 Random Pick Index [Medium]
Given an array of integers with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.
##### Optimal Python solution:
```python
import random

class Solution:
    def __init__(self, nums: List[int]):
        self.nums = nums

    def pick(self, target: int) -> int:
        indices = []
        for i in range(len(self.nums)):
            if self.nums[i] == target:
                indices.append(i)
        return random.choice(indices)
```
The essence of the problem is to randomly select an index of a given target number in an array.
    
### >> 528 Random Pick with Weight [Medium]
Given an array w of positive integers, where w[i] describes the weight of index i, write a function pickIndex which randomly picks an index in proportion to its weight.

Note:

1 <= w.length <= 10000

1 <= w[i] <= 10^5

pickIndex will be called at most 10000 times.

Example 1:

Input:
["Solution","pickIndex"]
[[[1]],[]]
Output: [null,0]

Example 2:

Input:
["Solution","pickIndex","pickIndex","pickIndex","pickIndex","pickIndex"]
[[[1,3]],[],[],[],[],[]]
Output: [null,0,1,1,1,0]

Explanation of Input Syntax:

The input is two lists: the subroutines called and their arguments. Solution's constructor has one argument, the array w. pickIndex has no arguments. Arguments are always wrapped with a list.
##### Sample input:
[["Solution","pickIndex"],[[[1]],[]]]
##### Sample output:
[null,0]

##### Questions to ask to clarify requirements:
What is the maximum length of the array? What is the maximum weight of an element in the array? How many times will pickIndex be called?

##### Optimal Python solution:
```python
class Solution:

    def __init__(self, w: List[int]):
        self.prefix_sum = []
        prefix_sum = 0
        for weight in w:
            prefix_sum += weight
            self.prefix_sum.append(prefix_sum)
        self.total_sum = prefix_sum

    def pickIndex(self) -> int:
        target = self.total_sum * random.random()
        left, right = 0, len(self.prefix_sum)
        while left < right:
            mid = left + (right - left) // 2
            if target > self.prefix_sum[mid]:
                left = mid + 1
            else:
                right = mid
        return left
```
##### Time complexity:
O(n), where n is the length of the array.
##### Space complexity:
O(n), where n is the length of the array.
##### Notes:
Use prefix sum to calculate the cumulative weights. Use binary search to find the index corresponding to the random target.
Use binary search to efficiently find the index corresponding to the random target.
Calculating the target using the total sum of weights multiplied by a random number.
Using a linear search to find the index corresponding to the random target.
    
### >> Comparison: 398 Random Pick Index [Medium] *VS* 528 Random Pick with Weight [Medium]
> Similarity distance: 0.4669
##### Similarities

- Both questions involve random selection of elements.
- Both questions require the use of random number generation.
- Both questions have a similar goal of selecting elements based on certain criteria.
##### Differences

- 398 Random Pick Index: Selects an index randomly from an array where the target element is present.
- 528 Random Pick with Weight: Selects an index randomly from an array based on the weight of each element.
##### New Insights in 528 Random Pick with Weight [Medium]

- 398 Random Pick Index: The solution involves reservoir sampling to achieve uniform random selection.
- 528 Random Pick with Weight: The solution involves prefix sum and binary search to achieve weighted random selection.

