
# Leetcode Intensive Tutorial Day 12 
> [Difficulty Score: 14]

> [Version: 20231225_200427]

## Courses overview of the day

- 47 Permutations II [Medium]
  - 46 Permutations [Medium]
    - 491 Increasing Subsequences [Medium]
      - 78 Subsets [Medium]
    - 39 Combination Sum [Medium]
      - 40 Combination Sum II [Medium]
  - 90 Subsets II [Medium]

#### Steps by steps

 - [1. From 47 Permutations II [Medium] to 46 Permutations [Medium]](#1-from-47-permutations-ii-medium-to-46-permutations-medium)

 - [2. From 46 Permutations [Medium] to 491 Increasing Subsequences [Medium]](#2-from-46-permutations-medium-to-491-increasing-subsequences-medium)

 - [3. From 491 Increasing Subsequences [Medium] to 78 Subsets [Medium]](#3-from-491-increasing-subsequences-medium-to-78-subsets-medium)

 - [4. From 46 Permutations [Medium] to 39 Combination Sum [Medium]](#4-from-46-permutations-medium-to-39-combination-sum-medium)

 - [5. From 39 Combination Sum [Medium] to 40 Combination Sum II [Medium]](#5-from-39-combination-sum-medium-to-40-combination-sum-ii-medium)

 - [6. From 47 Permutations II [Medium] to 90 Subsets II [Medium]](#6-from-47-permutations-ii-medium-to-90-subsets-ii-medium)

#### Summary


- 47 Permutations II : Generate all possible unique permutations of a collection of numbers.
- 39 Combination Sum : Given a set of candidate numbers and a target number, find all unique combinations that sum to the target.
- 78 Subsets : The essence of this problem is to generate all possible subsets using backtracking.
- 40 Combination Sum II : Given a collection of candidate numbers and a target number, find all unique combinations that sum to the target, with each number used only once.
- 90 Subsets II : To generate all possible subsets, use backtracking and skip duplicate elements. The time complexity is O(2^n) and the space complexity is O(n).
- 491 Increasing Subsequences : Generate all possible increasing subsequences of an array using backtracking.
- 46 Permutations : Generate all possible permutations of a collection of distinct integers.
> Similarity Diameter of these problems: 0.3804


---
# 1. From 47 Permutations II [Medium] to 46 Permutations [Medium]
> Similarity Distance: 0.2170

### >> 47 Permutations II [Medium]
Given a collection of numbers that might contain duplicates, return all possible unique permutations.
##### Sample input:
[1,1,2]
##### Sample output:
[[1,1,2],[1,2,1],[2,1,1]]

##### Questions to ask to clarify requirements:

- Can the input contain negative numbers?
- Can the input be an empty list?

##### Optimal Python solution:
```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def backtrack(start):
            if start == n:
                output.append(nums[:])
                return
            for i in range(start, n):
                if i > start and nums[i] == nums[i-1]:
                    continue
                nums[start], nums[i] = nums[i], nums[start]
                backtrack(start + 1)
                nums[start], nums[i] = nums[i], nums[start]
        n = len(nums)
        nums.sort()
        output = []
        backtrack(0)
        return output
```
##### Time complexity:
O(n!)
##### Space complexity:
O(n)
##### Notes:

- Use backtracking to generate all possible permutations
- Sort the input list to handle duplicates
- Skip duplicates during backtracking

- Sort the input list to handle duplicates efficiently.
- Use a separate list to store the output permutations.

- Handling duplicates in the input list

- Using a brute force approach to generate all permutations
    
### >> 46 Permutations [Medium]
Given a collection of distinct integers, return all possible permutations.
##### Sample input:
[1,2,3]
##### Sample output:
[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

##### Questions to ask to clarify requirements:

- Can the input contain duplicates?
- Can the input be empty?

##### Optimal Python solution:
```python
def permute(nums):
    def backtrack(first = 0):
        if first == n:
            output.append(nums[:])
        for i in range(first, n):
            nums[first], nums[i] = nums[i], nums[first]
            backtrack(first + 1)
            nums[first], nums[i] = nums[i], nums[first]
    n = len(nums)
    output = []
    backtrack()
    return output
```
##### Time complexity:
O(n!)
##### Space complexity:
O(n)
##### Notes:

- Use backtracking to generate all possible permutations
- Swap elements to generate different permutations

- Use recursion to implement the backtracking algorithm.
- Swap elements to generate different permutations.

- Understanding the backtracking algorithm
- Generating all possible permutations

- Using nested loops
    
### >> Comparison: 47 Permutations II [Medium] *VS* 46 Permutations [Medium]
> Similarity distance: 0.2170
##### Similarities

- Both questions are about generating permutations of a given set of numbers.
- Both questions have a medium difficulty level.
##### Differences

- Question 47 (Permutations II) allows duplicate numbers in the input set, while question 46 (Permutations) does not.
- Question 47 requires removing duplicate permutations from the result.
- Question 46 does not have the requirement of removing duplicates.
- Question 47 has a larger input space compared to question 46 due to the presence of duplicate numbers.
##### New Insights in 46 Permutations [Medium]

- Question 47 requires using a hash set or a similar data structure to track duplicate permutations.
- Question 46 can be solved using backtracking or recursion.
- Both questions provide an opportunity to practice permutation generation algorithms.


---
# 2. From 46 Permutations [Medium] to 491 Increasing Subsequences [Medium]
> Similarity Distance: 0.2610

### >> Reminder: 46 Permutations [Medium]
Given a collection of distinct integers, return all possible permutations.
##### Optimal Python solution:
```python
def permute(nums):
    def backtrack(first = 0):
        if first == n:
            output.append(nums[:])
        for i in range(first, n):
            nums[first], nums[i] = nums[i], nums[first]
            backtrack(first + 1)
            nums[first], nums[i] = nums[i], nums[first]
    n = len(nums)
    output = []
    backtrack()
    return output
```
Generate all possible permutations of a collection of distinct integers.
    
### >> 491 Increasing Subsequences [Medium]
Given an integer array nums, return all the different possible increasing subsequences of the given array with at least two elements. You may return the answer in any order.
##### Sample input:
[4,6,7,7]
##### Sample output:
[[4,6],[4,7],[4,6,7],[4,6,7,7],[6,7],[6,7,7],[7,7],[4,7,7]]

##### Questions to ask to clarify requirements:

- Can the input array contain duplicates?
- Can the subsequences contain duplicates?
- What is the maximum length of the input array?

##### Optimal Python solution:
```python
class Solution:
    def findSubsequences(self, nums: List[int]) -> List[List[int]]:
        res = []
        def backtrack(nums, path):
            if len(path) > 1:
                res.append(path)
            used = []
            for i in range(len(nums)):
                if nums[i] in used:
                    continue
                if not path or nums[i] >= path[-1]:
                    used.append(nums[i])
                    backtrack(nums[i+1:], path+[nums[i]])
        backtrack(nums, [])
        return res
```
##### Time complexity:
O(2^N)
##### Space complexity:
O(N)
##### Notes:

- Use backtracking to generate all possible subsequences
- Avoid duplicates by using a set to track used elements

- Use a set to track used elements and avoid duplicates
- Start the backtracking from each element in the input array

- Avoid duplicates by skipping elements that have already been used in the current path

- Avoid using a brute force approach to generate all subsequences
    
### >> Comparison: 46 Permutations [Medium] *VS* 491 Increasing Subsequences [Medium]
> Similarity distance: 0.2610
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding permutations or subsequences.
- Both questions require exploring all possible combinations.
##### Differences

- Question 46 focuses on finding all permutations of a given array.
- Question 491 focuses on finding all increasing subsequences in a given array.
- Question 46 requires backtracking to explore all possible permutations.
- Question 491 requires a different approach using recursion and backtracking.
- Question 46 has a fixed input size of 1 to 9 elements.
- Question 491 has a larger input size of up to 200 elements.
##### New Insights in 491 Increasing Subsequences [Medium]

- Question 46 teaches the concept of backtracking to generate permutations.
- Question 491 introduces the concept of finding increasing subsequences.
- Both questions provide practice in problem-solving and algorithmic thinking.


---
# 3. From 491 Increasing Subsequences [Medium] to 78 Subsets [Medium]
> Similarity Distance: 0.2889

### >> Reminder: 491 Increasing Subsequences [Medium]
Given an integer array nums, return all the different possible increasing subsequences of the given array with at least two elements. You may return the answer in any order.
##### Optimal Python solution:
```python
class Solution:
    def findSubsequences(self, nums: List[int]) -> List[List[int]]:
        res = []
        def backtrack(nums, path):
            if len(path) > 1:
                res.append(path)
            used = []
            for i in range(len(nums)):
                if nums[i] in used:
                    continue
                if not path or nums[i] >= path[-1]:
                    used.append(nums[i])
                    backtrack(nums[i+1:], path+[nums[i]])
        backtrack(nums, [])
        return res
```
Generate all possible increasing subsequences of an array using backtracking.
    
### >> 78 Subsets [Medium]
Given an integer array nums, return all possible subsets (the power set).
##### Sample input:
nums = [1,2,3]
##### Sample output:
[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def subsets(nums: List[int]) -> List[List[int]]:
    def backtrack(start, curr):
        output.append(curr[:])
        for i in range(start, len(nums)):
            curr.append(nums[i])
            backtrack(i + 1, curr)
            curr.pop()
    output = []
    backtrack(0, [])
    return output
```
##### Time complexity:
O(2^n)
##### Space complexity:
O(n)
##### Notes:
Backtracking, Recursion
None
None
None
    
### >> Comparison: 491 Increasing Subsequences [Medium] *VS* 78 Subsets [Medium]
> Similarity distance: 0.2889
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve finding subsets or subsequences of a given array.
- Both questions require generating all possible combinations of elements.
##### Differences

- 491 Increasing Subsequences focuses on finding increasing subsequences of length greater than or equal to 2.
- 78 Subsets focuses on finding all possible subsets of the given array.
- 491 Increasing Subsequences requires maintaining the order of elements in the subsequences.
- 78 Subsets does not require maintaining the order of elements in the subsets.
##### New Insights in 78 Subsets [Medium]

- 491 Increasing Subsequences teaches us how to efficiently generate increasing subsequences using backtracking.
- 78 Subsets teaches us how to generate all possible subsets using backtracking.
- Both questions provide insights into backtracking algorithms and combination generation.


---
# 4. From 46 Permutations [Medium] to 39 Combination Sum [Medium]
> Similarity Distance: 0.2841

### >> Reminder: 46 Permutations [Medium]
Given a collection of distinct integers, return all possible permutations.
##### Optimal Python solution:
```python
def permute(nums):
    def backtrack(first = 0):
        if first == n:
            output.append(nums[:])
        for i in range(first, n):
            nums[first], nums[i] = nums[i], nums[first]
            backtrack(first + 1)
            nums[first], nums[i] = nums[i], nums[first]
    n = len(nums)
    output = []
    backtrack()
    return output
```
Generate all possible permutations of a collection of distinct integers.
    
### >> 39 Combination Sum [Medium]
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.
##### Sample input:
[2,3,6,7]
7
##### Sample output:
[[2,2,3],[7]]

##### Questions to ask to clarify requirements:

- Can the candidates contain duplicates?
- Can the candidates be negative?
- Can the target be negative?

##### Optimal Python solution:
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        result = []
        self.backtrack(candidates, target, [], result)
        return result

    def backtrack(self, candidates: List[int], target: int, path: List[int], result: List[List[int]]):
        if target < 0:
            return
        if target == 0:
            result.append(path)
            return
        for i in range(len(candidates)):
            self.backtrack(candidates[i:], target - candidates[i], path + [candidates[i]], result)
```
##### Time complexity:
O(N^target)
##### Space complexity:
O(target)
##### Notes:

- Use backtracking to generate all combinations
- Avoid duplicates by starting the next iteration from the current index

- Start the next iteration from the current index to avoid duplicates

- Avoid duplicates by starting the next iteration from the current index

- Avoid using recursion without pruning
    
### >> Comparison: 46 Permutations [Medium] *VS* 39 Combination Sum [Medium]
> Similarity distance: 0.2841
##### Similarities

- Both questions are categorized as 'Medium' difficulty level.
- Both questions involve generating combinations or permutations of a given set of numbers.
- Both questions require backtracking or recursion to find all possible combinations or permutations.
##### Differences

- Question 46 (Permutations) requires finding all possible permutations of a given set of numbers, while question 39 (Combination Sum) requires finding all possible combinations of numbers that sum up to a target value.
- In question 46, the order of the numbers in the permutation matters, while in question 39, the order of the numbers in the combination does not matter.
- Question 46 allows repetition of numbers in the permutation, while question 39 does not allow repetition of numbers in the combination.
##### New Insights in 39 Combination Sum [Medium]

- Question 46 teaches us how to generate all possible permutations of a given set of numbers using backtracking or recursion.
- Question 39 teaches us how to generate all possible combinations of numbers that sum up to a target value using backtracking or recursion.
- Both questions provide insights into how to efficiently generate combinations or permutations by pruning unnecessary branches in the backtracking process.


---
# 5. From 39 Combination Sum [Medium] to 40 Combination Sum II [Medium]
> Similarity Distance: 0.1165

### >> Reminder: 39 Combination Sum [Medium]
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.
##### Optimal Python solution:
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        result = []
        self.backtrack(candidates, target, [], result)
        return result

    def backtrack(self, candidates: List[int], target: int, path: List[int], result: List[List[int]]):
        if target < 0:
            return
        if target == 0:
            result.append(path)
            return
        for i in range(len(candidates)):
            self.backtrack(candidates[i:], target - candidates[i], path + [candidates[i]], result)
```
Given a set of candidate numbers and a target number, find all unique combinations that sum to the target.
    
### >> 40 Combination Sum II [Medium]
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target. Each number in candidates may only be used once in the combination.
##### Sample input:
[10,1,2,7,6,1,5]
8
##### Sample output:
[[1,1,6],[1,2,5],[1,7],[2,6]]

##### Questions to ask to clarify requirements:

- Can the candidates contain duplicates?
- Can the candidates be negative?
- Can the target be negative?

##### Optimal Python solution:
```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        result = []
        candidates.sort()
        self.backtrack(candidates, target, [], result)
        return result

    def backtrack(self, candidates: List[int], target: int, path: List[int], result: List[List[int]]):
        if target < 0:
            return
        if target == 0:
            result.append(path)
            return
        for i in range(len(candidates)):
            if i > 0 and candidates[i] == candidates[i-1]:
                continue
            self.backtrack(candidates[i+1:], target - candidates[i], path + [candidates[i]], result)
```
##### Time complexity:
O(N^target)
##### Space complexity:
O(target)
##### Notes:

- Use backtracking to generate all combinations
- Sort the candidates to avoid duplicates

- Sort the candidates to avoid duplicates

- Avoid duplicates by skipping candidates with the same value as the previous candidate

- Avoid using recursion without pruning
    
### >> Comparison: 39 Combination Sum [Medium] *VS* 40 Combination Sum II [Medium]
> Similarity distance: 0.1165
##### Similarities

- Both questions are about finding combinations of numbers that sum up to a target.
- Both questions have a similar input format, where a list of numbers and a target number are given.
##### Differences

- Combination Sum allows using the same number multiple times in a combination, while Combination Sum II does not allow duplicates.
- Combination Sum II requires the combinations to be unique, while Combination Sum does not have this requirement.
- Combination Sum II has an additional constraint that each number in a combination can only be used once.
##### New Insights in 40 Combination Sum II [Medium]

- Both questions can be solved using backtracking, where we explore all possible combinations.
- In Combination Sum II, we need to handle duplicates in the input list to avoid duplicate combinations.
- In Combination Sum II, we need to skip duplicate numbers in the backtracking process to ensure unique combinations.


---
# 6. From 47 Permutations II [Medium] to 90 Subsets II [Medium]
> Similarity Distance: 0.3085

### >> Reminder: 47 Permutations II [Medium]
Given a collection of numbers that might contain duplicates, return all possible unique permutations.
##### Optimal Python solution:
```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def backtrack(start):
            if start == n:
                output.append(nums[:])
                return
            for i in range(start, n):
                if i > start and nums[i] == nums[i-1]:
                    continue
                nums[start], nums[i] = nums[i], nums[start]
                backtrack(start + 1)
                nums[start], nums[i] = nums[i], nums[start]
        n = len(nums)
        nums.sort()
        output = []
        backtrack(0)
        return output
```
Generate all possible unique permutations of a collection of numbers.
    
### >> 90 Subsets II [Medium]
Given an integer array nums that may contain duplicates, return all possible subsets (the power set). The solution set must not contain duplicate subsets. Return the solution in any order.
##### Sample input:
[1,2,2]
##### Sample output:
[[],[1],[1,2],[1,2,2],[2],[2,2]]

##### Questions to ask to clarify requirements:
Can the input array contain negative numbers? Can the input array be empty?

##### Optimal Python solution:
```python
def subsetsWithDup(nums):
    res = []
    nums.sort()
    backtrack(nums, 0, [], res)
    return res


def backtrack(nums, start, path, res):
    res.append(path[:])
    for i in range(start, len(nums)):
        if i > start and nums[i] == nums[i-1]:
            continue
        path.append(nums[i])
        backtrack(nums, i+1, path, res)
        path.pop()
```
##### Time complexity:
O(2^n)
##### Space complexity:
O(n)
##### Notes:
To generate all possible subsets, we can use backtracking.
To avoid duplicate subsets, we need to sort the input array and skip duplicate elements during backtracking.
Understand how backtracking works and how to handle duplicate elements.
Handling duplicate elements and avoiding duplicate subsets.
Using a brute force approach to generate all possible subsets.
    
### >> Comparison: 47 Permutations II [Medium] *VS* 90 Subsets II [Medium]
> Similarity distance: 0.3085
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve generating subsets or permutations with certain constraints.
- Both questions require handling duplicates in the input.
##### Differences

- Question 47 Permutations II focuses on generating unique permutations of a given array, while question 90 Subsets II focuses on generating unique subsets of a given array.
- In question 47, the order of elements in the permutation matters, while in question 90, the order of elements in the subset does not matter.
- Question 47 requires backtracking to generate permutations, while question 90 can be solved using a combination of backtracking and bit manipulation.
- Question 47 has a time complexity of O(n!), while question 90 has a time complexity of O(2^n).
##### New Insights in 90 Subsets II [Medium]

- Both questions require handling duplicates in the input, which can be done by sorting the input array and skipping duplicate elements during the generation process.
- Question 47 can be solved using backtracking and maintaining a visited array to track used elements, while question 90 can be solved using backtracking and bit manipulation to generate all possible subsets.

