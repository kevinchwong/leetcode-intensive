
# Leetcode Intensive Tutorial Day 39 
> [Difficulty Score: 20]

> [Version: 20231226_040350]

> [Including this day, you had studied : 323 leetcode problems]


## Courses overview of the day

- 16 3Sum Closest [Medium]
  - 15 3Sum [Medium]
    - 259 3Sum Smaller [Medium]
  - 4 Median of Two Sorted Arrays [Hard]
    - 462 Minimum Moves to Equal Array Elements II [Medium]
      - 480 Sliding Window Median [Hard]
    - 571 Find Median Given Frequency of Numbers [Hard]

#### Step by step

 - [1. From 16 3Sum Closest [Medium] to 15 3Sum [Medium]](#1-from-16-3sum-closest-medium-to-15-3sum-medium))

 - [2. From 15 3Sum [Medium] to 259 3Sum Smaller [Medium]](#2-from-15-3sum-medium-to-259-3sum-smaller-medium))

 - [3. From 16 3Sum Closest [Medium] to 4 Median of Two Sorted Arrays [Hard]](#3-from-16-3sum-closest-medium-to-4-median-of-two-sorted-arrays-hard))

 - [4. From 4 Median of Two Sorted Arrays [Hard] to 462 Minimum Moves to Equal Array Elements II [Medium]](#4-from-4-median-of-two-sorted-arrays-hard-to-462-minimum-moves-to-equal-array-elements-ii-medium))

 - [5. From 462 Minimum Moves to Equal Array Elements II [Medium] to 480 Sliding Window Median [Hard]](#5-from-462-minimum-moves-to-equal-array-elements-ii-medium-to-480-sliding-window-median-hard))

 - [6. From 4 Median of Two Sorted Arrays [Hard] to 571 Find Median Given Frequency of Numbers [Hard]](#6-from-4-median-of-two-sorted-arrays-hard-to-571-find-median-given-frequency-of-numbers-hard))

    

#### Summary


- 571 Find Median Given Frequency of Numbers : Given a list of numbers and their frequencies, find the median of the numbers.
- 480 Sliding Window Median : The essence of this problem is to find the median of each window in a given array using a sliding window approach.
- 16 3Sum Closest : Finding three integers in an array that have the closest sum to a target.
- 259 3Sum Smaller : Given an array and a target, find the number of triplets with sum less than the target.
- 4 Median of Two Sorted Arrays : The essence of this problem is to merge and sort two sorted arrays to find the median.
- 462 Minimum Moves to Equal Array Elements II : The minimum number of moves required to make all array elements equal is the sum of absolute differences between each element and the median.
- 15 3Sum : Finding unique triplets that sum up to zero in an array.
> Similarity Diameter of these problems: 0.6861


---
# 1. From 16 3Sum Closest [Medium] to 15 3Sum [Medium]
> Similarity Distance: 0.2184

### >> 16 3Sum Closest [Medium]
Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers.
##### Sample input:
[-1,2,1,-4], 1
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can the input array contain duplicate triplets?
- Can the input array contain negative numbers?

##### Optimal Python solution:
```python
def threeSumClosest(nums, target):
    nums.sort()
    closest_sum = float('inf')
    for i in range(len(nums)-2):
        l, r = i+1, len(nums)-1
        while l < r:
            curr_sum = nums[i] + nums[l] + nums[r]
            if curr_sum == target:
                return curr_sum
            if abs(curr_sum - target) < abs(closest_sum - target):
                closest_sum = curr_sum
            if curr_sum < target:
                l += 1
            else:
                r -= 1
    return closest_sum
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(1)
##### Notes:

- Sort the array
- Use two pointers to find the closest sum

- Remember to handle duplicate triplets by skipping duplicate elements during the iteration.

- Handling duplicate triplets

- Using a brute force approach
    
### >> 15 3Sum [Medium]
Given an array nums of n integers, find all unique triplets in the array which gives the sum of zero.
##### Sample input:
[-1,0,1,2,-1,-4]
##### Sample output:
[[-1,-1,2],[-1,0,1]]

##### Questions to ask to clarify requirements:

- Can the input array contain duplicate triplets?
- Can the input array contain negative numbers?

##### Optimal Python solution:
```python
def threeSum(nums):
    nums.sort()
    res = []
    for i in range(len(nums)-2):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        l, r = i+1, len(nums)-1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s < 0:
                l += 1
            elif s > 0:
                r -= 1
            else:
                res.append([nums[i], nums[l], nums[r]])
                while l < r and nums[l] == nums[l+1]:
                    l += 1
                while l < r and nums[r] == nums[r-1]:
                    r -= 1
                l += 1
                r -= 1
    return res
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(1)
##### Notes:

- Sort the array
- Use two pointers to find the triplets

- Remember to handle duplicate triplets by skipping duplicate elements during the iteration.

- Handling duplicate triplets

- Using a brute force approach
    
### >> Comparison: 16 3Sum Closest [Medium] *VS* 15 3Sum [Medium]
> Similarity distance: 0.2184
##### Similarities

- Both questions are related to finding three numbers in an array that sum up to a target value.
- Both questions have a similar input format, where an array of integers is given as input.
##### Differences

- The 3Sum Closest question requires finding the sum of three numbers that is closest to a target value, while the 3Sum question requires finding the unique triplets that sum up to zero.
- The 3Sum Closest question has a single target value, while the 3Sum question has a target value of zero.
- The 3Sum Closest question has a return type of integer, representing the sum of the three numbers, while the 3Sum question has a return type of array of arrays, representing the unique triplets.
##### New Insights in 15 3Sum [Medium]

- Both questions require using a two-pointer approach to efficiently find the desired triplets or sum.
- Both questions can benefit from sorting the input array to optimize the solution.
- Both questions involve handling duplicate elements in the input array to avoid duplicate triplets or sums.


---
# 2. From 15 3Sum [Medium] to 259 3Sum Smaller [Medium]
> Similarity Distance: 0.2721

### >> Reminder: 15 3Sum [Medium]
Given an array nums of n integers, find all unique triplets in the array which gives the sum of zero.
##### Optimal Python solution:
```python
def threeSum(nums):
    nums.sort()
    res = []
    for i in range(len(nums)-2):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        l, r = i+1, len(nums)-1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s < 0:
                l += 1
            elif s > 0:
                r -= 1
            else:
                res.append([nums[i], nums[l], nums[r]])
                while l < r and nums[l] == nums[l+1]:
                    l += 1
                while l < r and nums[r] == nums[r-1]:
                    r -= 1
                l += 1
                r -= 1
    return res
```
Finding unique triplets that sum up to zero in an array.
    
### >> 259 3Sum Smaller [Medium]
Given an array of n integers nums and a target, find the number of index triplets i, j, k with 0 <= i < j < k < n that satisfy the condition nums[i] + nums[j] + nums[k] < target.
##### Sample input:
nums = [-2,0,1,3], target = 2
##### Sample output:
2

##### Questions to ask to clarify requirements:
Are there any constraints on the size of the array? Can the array contain duplicate elements?

##### Optimal Python solution:
```python
def threeSumSmaller(nums, target):
    nums.sort()
    count = 0
    for i in range(len(nums)-2):
        left = i + 1
        right = len(nums) - 1
        while left < right:
            if nums[i] + nums[left] + nums[right] < target:
                count += right - left
                left += 1
            else:
                right -= 1
    return count
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(1)
##### Notes:

- Sort the array in ascending order
- Use two pointers to find the triplets that satisfy the condition
- Count the number of valid triplets

- Handle duplicate elements in the array

- Handling duplicate triplets

- Using a brute force approach with three nested loops
    
### >> Comparison: 15 3Sum [Medium] *VS* 259 3Sum Smaller [Medium]
> Similarity distance: 0.2721
##### Similarities

- Both questions are related to finding triplets in an array that sum up to a target value.
- Both questions have a time complexity of O(n^2).
##### Differences

- Question 15 (3Sum) requires finding unique triplets that sum up to zero, while question 259 (3Sum Smaller) requires finding the number of triplets that sum up to a target value.
- Question 15 (3Sum) allows duplicate numbers in the array, while question 259 (3Sum Smaller) does not.
- Question 15 (3Sum) returns the unique triplets, while question 259 (3Sum Smaller) returns the count of valid triplets.
##### New Insights in 259 3Sum Smaller [Medium]

- Question 15 (3Sum) can be solved using a two-pointer approach, where the array is sorted and two pointers are used to find the triplets.
- Question 259 (3Sum Smaller) can be solved using a two-pointer approach as well, but with a slight modification to count the valid triplets.


---
# 3. From 16 3Sum Closest [Medium] to 4 Median of Two Sorted Arrays [Hard]
> Similarity Distance: 0.5388

### >> Reminder: 16 3Sum Closest [Medium]
Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers.
##### Optimal Python solution:
```python
def threeSumClosest(nums, target):
    nums.sort()
    closest_sum = float('inf')
    for i in range(len(nums)-2):
        l, r = i+1, len(nums)-1
        while l < r:
            curr_sum = nums[i] + nums[l] + nums[r]
            if curr_sum == target:
                return curr_sum
            if abs(curr_sum - target) < abs(closest_sum - target):
                closest_sum = curr_sum
            if curr_sum < target:
                l += 1
            else:
                r -= 1
    return closest_sum
```
Finding three integers in an array that have the closest sum to a target.
    
### >> 4 Median of Two Sorted Arrays [Hard]
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
##### Sample input:
nums1 = [1,3], nums2 = [2]
##### Sample output:
2.00000

##### Questions to ask to clarify requirements:
What should be the output if both arrays are empty?

##### Optimal Python solution:
```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        merged = sorted(nums1 + nums2)
        n = len(merged)
        if n % 2 == 0:
            return (merged[n // 2 - 1] + merged[n // 2]) / 2
        else:
            return merged[n // 2]
```
##### Time complexity:
O((m + n) log(m + n))
##### Space complexity:
O(m + n)
##### Notes:
Merge the two sorted arrays and find the median. If the total number of elements is odd, return the middle element. If the total number of elements is even, return the average of the two middle elements.
Use the sorted() function to merge and sort the arrays. Handle the case when both arrays are empty separately.
Handling the case when both arrays are empty.
Using brute force approach to merge and sort the arrays.
    
### >> Comparison: 16 3Sum Closest [Medium] *VS* 4 Median of Two Sorted Arrays [Hard]
> Similarity distance: 0.5388
##### Similarities

- Both questions involve finding the closest sum or median of elements in arrays.
- Both questions require sorting the input arrays.
- Both questions have a time complexity of O(n^2) or O(log(m+n)).
##### Differences

- 3Sum Closest involves finding the closest sum of three elements, while Median of Two Sorted Arrays involves finding the median of two arrays.
- 3Sum Closest uses a two-pointer approach, while Median of Two Sorted Arrays uses a binary search approach.
- 3Sum Closest has a time complexity of O(n^2), while Median of Two Sorted Arrays has a time complexity of O(log(m+n)).
##### New Insights in 4 Median of Two Sorted Arrays [Hard]

- From 3Sum Closest, we can learn how to efficiently find the closest sum of three elements in an array.
- From Median of Two Sorted Arrays, we can learn how to find the median of two sorted arrays in an efficient manner.


---
# 4. From 4 Median of Two Sorted Arrays [Hard] to 462 Minimum Moves to Equal Array Elements II [Medium]
> Similarity Distance: 0.4688

### >> Reminder: 4 Median of Two Sorted Arrays [Hard]
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
##### Optimal Python solution:
```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        merged = sorted(nums1 + nums2)
        n = len(merged)
        if n % 2 == 0:
            return (merged[n // 2 - 1] + merged[n // 2]) / 2
        else:
            return merged[n // 2]
```
The essence of this problem is to merge and sort two sorted arrays to find the median.
    
### >> 462 Minimum Moves to Equal Array Elements II [Medium]
Given an integer array nums of size n, return the minimum number of moves required to make all array elements equal. In one move, you can increment or decrement an element of the array by 1.
##### Sample input:
[1,2,3]
##### Sample output:
2

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def minMoves2(nums: List[int]) -> int:
    nums.sort()
    median = nums[len(nums) // 2]
    return sum(abs(num - median) for num in nums)
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(1)
##### Notes:
Find the median of the array and calculate the sum of absolute differences between each element and the median.
None
None
None
    
### >> Comparison: 4 Median of Two Sorted Arrays [Hard] *VS* 462 Minimum Moves to Equal Array Elements II [Medium]
> Similarity distance: 0.4688
##### Similarities

- Both questions involve manipulating arrays.
- Both questions require finding a specific value or range of values in the arrays.
- Both questions have a complexity of O(log(min(m, n))) in terms of time complexity.
##### Differences

- Median of Two Sorted Arrays involves finding the median value of the combined sorted arrays.
- Minimum Moves to Equal Array Elements II involves finding the minimum number of moves required to make all elements in the array equal.
- Median of Two Sorted Arrays is classified as a Hard level question, while Minimum Moves to Equal Array Elements II is classified as a Medium level question.
- Median of Two Sorted Arrays requires a more complex algorithm, such as the binary search approach, to solve the problem efficiently.
- Minimum Moves to Equal Array Elements II can be solved using the median value of the array.
##### New Insights in 462 Minimum Moves to Equal Array Elements II [Medium]

- Median of Two Sorted Arrays teaches us how to efficiently find the median value of two sorted arrays.
- Minimum Moves to Equal Array Elements II teaches us how to find the minimum number of moves required to make all elements in an array equal, using the median value as a pivot.


---
# 5. From 462 Minimum Moves to Equal Array Elements II [Medium] to 480 Sliding Window Median [Hard]
> Similarity Distance: 0.4941

### >> Reminder: 462 Minimum Moves to Equal Array Elements II [Medium]
Given an integer array nums of size n, return the minimum number of moves required to make all array elements equal. In one move, you can increment or decrement an element of the array by 1.
##### Optimal Python solution:
```python
def minMoves2(nums: List[int]) -> int:
    nums.sort()
    median = nums[len(nums) // 2]
    return sum(abs(num - median) for num in nums)
```
The minimum number of moves required to make all array elements equal is the sum of absolute differences between each element and the median.
    
### >> 480 Sliding Window Median [Hard]
Find the median of each window in a given array.
##### Sample input:
[1,3,-1,-3,5,3,6,7]
3

Output:
[1,-1,-1,3,5,6]
##### Sample output:
[1,-1,-1,3,5,6]

##### Questions to ask to clarify requirements:
What should be the output format? Can the input array contain duplicates?

##### Optimal Python solution:
```python
import bisect

class Solution:
    def medianSlidingWindow(self, nums: List[int], k: int) -> List[float]:
        window = sorted(nums[:k])
        medians = []
        for i in range(k, len(nums) + 1):
            medians.append((window[k // 2] + window[(k - 1) // 2]) / 2)
            if i == len(nums):
                break
            window.remove(nums[i - k])
            bisect.insort(window, nums[i])
        return medians
```
##### Time complexity:
O(n * k * log(k))
##### Space complexity:
O(k)
##### Notes:
1. Use a sliding window to iterate through the array.
2. Maintain a sorted window to efficiently find the median.
3. Calculate the median by taking the average of the middle two elements if the window size is even.
4. Remove the first element of the window and insert the next element in the sorted window for each iteration.
5. Return the list of medians.
1. Use the bisect module to efficiently maintain a sorted window.
2. Use the remove() and insort() methods to remove and insert elements in a sorted list.
3. Use the index() method to find the position of an element in a list.
4. Use if statements to handle edge cases.
1. Maintaining a sorted window efficiently by using the bisect module.
2. Calculating the median by taking the average of the middle two elements if the window size is even.
3. Removing the first element of the window and inserting the next element in the sorted window.
4. Handling edge cases where the window size is larger than the array size.
1. Sorting the window for each iteration.
2. Calculating the median by finding the middle element(s) of the window.
3. Removing and inserting elements in the window by using the index() and insert() methods.
4. Handling edge cases where the window size is larger than the array size by using if statements.
    
### >> Comparison: 462 Minimum Moves to Equal Array Elements II [Medium] *VS* 480 Sliding Window Median [Hard]
> Similarity distance: 0.4941
##### Similarities

- Both questions involve manipulating an array of numbers.
- Both questions require finding the median of a subset of the array.
##### Differences

- Question 462 involves finding the minimum number of moves to make all array elements equal, while question 480 involves finding the median of each sliding window in the array.
- Question 462 is classified as medium difficulty, while question 480 is classified as hard difficulty.
##### New Insights in 480 Sliding Window Median [Hard]

- Question 462 teaches us how to minimize the number of moves required to equalize array elements.
- Question 480 teaches us how to efficiently find the median of sliding windows in an array.


---
# 6. From 4 Median of Two Sorted Arrays [Hard] to 571 Find Median Given Frequency of Numbers [Hard]
> Similarity Distance: 0.4846

### >> Reminder: 4 Median of Two Sorted Arrays [Hard]
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
##### Optimal Python solution:
```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        merged = sorted(nums1 + nums2)
        n = len(merged)
        if n % 2 == 0:
            return (merged[n // 2 - 1] + merged[n // 2]) / 2
        else:
            return merged[n // 2]
```
The essence of this problem is to merge and sort two sorted arrays to find the median.
    
### >> 571 Find Median Given Frequency of Numbers [Hard]
Given a list of numbers and their frequencies, find the median of the numbers.
##### Sample input:
[1, 3, 2, 2, 2, 3, 4, 4, 4, 4, 5, 5, 5, 5, 5]
##### Sample output:
4

##### Questions to ask to clarify requirements:

- What is the maximum number of elements in the list?
- Can the list contain negative numbers?
- Can the list be empty?

##### Optimal Python solution:
```python
def findMedian(nums):
    freq = []
    for i in range(len(nums)):
        freq.extend([nums[i][0]] * nums[i][1])
    freq.sort()
    n = len(freq)
    if n % 2 == 0:
        return (freq[n // 2 - 1] + freq[n // 2]) / 2
    else:
        return freq[n // 2]
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(n)
##### Notes:

- Create a frequency list from the given numbers and frequencies
- Sort the frequency list
- Find the median of the sorted list

- Use the built-in sort function in Python to sort the frequency list.
- Handle the case when the number of elements is even by taking the average of the middle two elements.

- Handling the case when the number of elements is even

- Using a brute force approach to find the median
    
### >> Comparison: 4 Median of Two Sorted Arrays [Hard] *VS* 571 Find Median Given Frequency of Numbers [Hard]
> Similarity distance: 0.4846
##### Similarities

- Both questions are related to finding the median of a set of numbers.
- Both questions are classified as 'Hard' level difficulty.
##### Differences

- Question 4 requires finding the median of two sorted arrays, while question 571 requires finding the median given the frequency of numbers.
- Question 4 involves working with arrays, while question 571 involves working with frequency counts.
- Question 4 has a time complexity requirement of O(log(m+n)), while question 571 does not have a specific time complexity requirement.
##### New Insights in 571 Find Median Given Frequency of Numbers [Hard]

- Question 4 introduces the concept of merging two sorted arrays to find the median.
- Question 571 introduces the concept of calculating the median given the frequency of numbers.

