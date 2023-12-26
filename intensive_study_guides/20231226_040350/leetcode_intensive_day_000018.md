
# Leetcode Intensive Tutorial Day 18 
> [Difficulty Score: 15]

> [Version: 20231226_040350]

> [Including this day, you had studied : 137 leetcode problems]


## Courses overview of the day

- 169 Majority Element [Easy]
  - 229 Majority Element II [Medium]
    - 470 Implement Rand10() Using Rand7() [Medium]
      - 386 Lexicographical Numbers [Medium]
        - 60 Permutation Sequence [Medium]
          - 31 Next Permutation [Medium]
    - 262 Trips and Users [Hard]

#### Step by step

 - [1. From 169 Majority Element [Easy] to 229 Majority Element II [Medium]](#1-from-169-majority-element-easy-to-229-majority-element-ii-medium))

 - [2. From 229 Majority Element II [Medium] to 470 Implement Rand10() Using Rand7() [Medium]](#2-from-229-majority-element-ii-medium-to-470-implement-rand10-using-rand7-medium))

 - [3. From 470 Implement Rand10() Using Rand7() [Medium] to 386 Lexicographical Numbers [Medium]](#3-from-470-implement-rand10-using-rand7-medium-to-386-lexicographical-numbers-medium))

 - [4. From 386 Lexicographical Numbers [Medium] to 60 Permutation Sequence [Medium]](#4-from-386-lexicographical-numbers-medium-to-60-permutation-sequence-medium))

 - [5. From 60 Permutation Sequence [Medium] to 31 Next Permutation [Medium]](#5-from-60-permutation-sequence-medium-to-31-next-permutation-medium))

 - [6. From 229 Majority Element II [Medium] to 262 Trips and Users [Hard]](#6-from-229-majority-element-ii-medium-to-262-trips-and-users-hard))

    

#### Summary


- 470 Implement Rand10() Using Rand7() : Generating a random number in a specific range using a random number generator with a different range.
- 60 Permutation Sequence : The essence of this problem is to generate all permutations and select the kth permutation.
- 386 Lexicographical Numbers : The essence of this problem is to generate the numbers from 1 to n in lexicographical order.
- 229 Majority Element II : The essence of this problem is to find the majority elements that appear more than ⌊n/3⌋ times in an array.
- 262 Trips and Users : Get the banned users based on the Trips and Users tables.
- 169 Majority Element : The majority element appears more than n/2 times in the array.
- 31 Next Permutation : The essence of the problem is to find the next permutation of a given list of numbers.
> Similarity Diameter of these problems: 0.7398


---
# 1. From 169 Majority Element [Easy] to 229 Majority Element II [Medium]
> Similarity Distance: 0.2933

### >> 169 Majority Element [Easy]
Given an array nums of size n, return the majority element.
##### Sample input:
[3,2,3]
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the definition of majority element? Can the array be empty?

##### Optimal Python solution:
```python
def majorityElement(nums):
    count = 0
    candidate = None
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    return candidate
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
The majority element appears more than n/2 times in the array.
None
None
None
    
### >> 229 Majority Element II [Medium]
Given an integer array of size n, find all elements that appear more than ⌊n/3⌋ times.
##### Sample input:
[3,2,3]
##### Sample output:
[3]

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the array be empty?

##### Optimal Python solution:
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        count1, count2, candidate1, candidate2 = 0, 0, 0, 1
        for num in nums:
            if num == candidate1:
                count1 += 1
            elif num == candidate2:
                count2 += 1
            elif count1 == 0:
                candidate1, count1 = num, 1
            elif count2 == 0:
                candidate2, count2 = num, 1
            else:
                count1, count2 = count1 - 1, count2 - 1
        return [n for n in (candidate1, candidate2) if nums.count(n) > len(nums) // 3]
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use the voting algorithm to find the majority elements.
2. The majority elements must appear more than ⌊n/3⌋ times.
Understand the voting algorithm and how it guarantees finding the majority elements.
The voting algorithm requires two counters and two candidates to keep track of the majority elements.
Using a hashmap to count the occurrences of each element.
    
### >> Comparison: 169 Majority Element [Easy] *VS* 229 Majority Element II [Medium]
> Similarity distance: 0.2933
##### Similarities

- Both questions are about finding the majority element in an array.
- The majority element is the element that appears more than ⌊n/2⌋ times in the array.
- Both questions require finding the majority element in linear time and constant space.
##### Differences

- 169 Majority Element [Easy] requires finding the majority element that appears more than ⌊n/2⌋ times.
- 229 Majority Element II [Medium] requires finding all the majority elements that appear more than ⌊n/3⌋ times.
- 169 Majority Element [Easy] can assume that the majority element always exists.
- 229 Majority Element II [Medium] needs to handle the case where there may be no majority element.
##### New Insights in 229 Majority Element II [Medium]

- 169 Majority Element [Easy] can be solved using the Boyer-Moore Voting Algorithm.
- 229 Majority Element II [Medium] can be solved using the Boyer-Moore Voting Algorithm with a modification.


---
# 2. From 229 Majority Element II [Medium] to 470 Implement Rand10() Using Rand7() [Medium]
> Similarity Distance: 0.5740

### >> Reminder: 229 Majority Element II [Medium]
Given an integer array of size n, find all elements that appear more than ⌊n/3⌋ times.
##### Optimal Python solution:
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        count1, count2, candidate1, candidate2 = 0, 0, 0, 1
        for num in nums:
            if num == candidate1:
                count1 += 1
            elif num == candidate2:
                count2 += 1
            elif count1 == 0:
                candidate1, count1 = num, 1
            elif count2 == 0:
                candidate2, count2 = num, 1
            else:
                count1, count2 = count1 - 1, count2 - 1
        return [n for n in (candidate1, candidate2) if nums.count(n) > len(nums) // 3]
```
The essence of this problem is to find the majority elements that appear more than ⌊n/3⌋ times in an array.
    
### >> 470 Implement Rand10() Using Rand7() [Medium]
Implement the rand10() function using the rand7() function.
##### Sample input:
N/A
##### Sample output:
N/A

##### Questions to ask to clarify requirements:

- What is the range of numbers that rand10() should generate?
- Can we assume that rand7() is a perfect random number generator?

##### Optimal Python solution:
```python
class Solution:
    def rand10(self) -> int:
        while True:
            num = (rand7() - 1) * 7 + rand7()
            if num <= 40:
                return num % 10 + 1
```
##### Time complexity:
O(1) on average
##### Space complexity:
O(1)
##### Notes:

- The solution uses rejection sampling to generate a random number in the range 1 to 10.
- The probability of each number in the range 1 to 10 is equal.
- The solution discards numbers greater than 40 and uses modular arithmetic to map the remaining numbers to the range 1 to 10.

- Understand the probability distribution of the generated numbers.
- Consider the worst case scenario when analyzing the time complexity.

- Using rejection sampling to generate a random number in a specific range

- Using a loop to generate random numbers until a desired range is obtained
    
### >> Comparison: 229 Majority Element II [Medium] *VS* 470 Implement Rand10() Using Rand7() [Medium]
> Similarity distance: 0.5740
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding a majority element.
- Both questions require implementing a specific function.
##### Differences

- Question 229 involves finding the majority element(s) that appear more than ⌊n/3⌋ times in an array.
- Question 470 involves implementing a function Rand10() using another function Rand7().
- Question 229 requires a linear time complexity solution, while question 470 does not specify any specific time complexity requirement.
##### New Insights in 470 Implement Rand10() Using Rand7() [Medium]

- Question 229: The Boyer-Moore Voting Algorithm can be used to find the majority element(s) in linear time.
- Question 470: The rejection sampling technique can be used to implement Rand10() using Rand7().


---
# 3. From 470 Implement Rand10() Using Rand7() [Medium] to 386 Lexicographical Numbers [Medium]
> Similarity Distance: 0.4944

### >> Reminder: 470 Implement Rand10() Using Rand7() [Medium]
Implement the rand10() function using the rand7() function.
##### Optimal Python solution:
```python
class Solution:
    def rand10(self) -> int:
        while True:
            num = (rand7() - 1) * 7 + rand7()
            if num <= 40:
                return num % 10 + 1
```
Generating a random number in a specific range using a random number generator with a different range.
    
### >> 386 Lexicographical Numbers [Medium]
Given an integer n, return 1 - n in lexicographical order.
##### Sample input:
13
##### Sample output:
[1,10,11,12,13,2,3,4,5,6,7,8,9]

##### Questions to ask to clarify requirements:
What should be the output format? Can the input be negative?

##### Optimal Python solution:
```python
class Solution:
    def lexicalOrder(self, n: int) -> List[int]:
        res = []
        curr = 1
        for _ in range(n):
            res.append(curr)
            if curr * 10 <= n:
                curr *= 10
            elif curr % 10 != 9 and curr + 1 <= n:
                curr += 1
            else:
                while (curr // 10) % 10 == 9:
                    curr //= 10
                curr = curr // 10 + 1
        return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a list to store the lexicographically ordered numbers
2. Use a variable to keep track of the current number
3. Use a loop to generate the numbers in lexicographical order
Use a loop to generate the numbers in lexicographical order. Handle the special cases when the current number ends with 9.
Determining the next number in lexicographical order
Using recursion
    
### >> Comparison: 470 Implement Rand10() Using Rand7() [Medium] *VS* 386 Lexicographical Numbers [Medium]
> Similarity distance: 0.4944
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve generating random numbers.
- Both questions require implementing a function.
- Both questions have a specific input-output relationship.
##### Differences

- Question 470 involves implementing the Rand10() function using the Rand7() function.
- Question 386 involves generating lexicographically sorted numbers from 1 to n.
##### New Insights in 386 Lexicographical Numbers [Medium]

- Question 470 teaches us how to generate a random number between 1 and 10 using a random number generator that generates numbers between 1 and 7.
- Question 386 teaches us how to generate lexicographically sorted numbers using a specific algorithm.


---
# 4. From 386 Lexicographical Numbers [Medium] to 60 Permutation Sequence [Medium]
> Similarity Distance: 0.5097

### >> Reminder: 386 Lexicographical Numbers [Medium]
Given an integer n, return 1 - n in lexicographical order.
##### Optimal Python solution:
```python
class Solution:
    def lexicalOrder(self, n: int) -> List[int]:
        res = []
        curr = 1
        for _ in range(n):
            res.append(curr)
            if curr * 10 <= n:
                curr *= 10
            elif curr % 10 != 9 and curr + 1 <= n:
                curr += 1
            else:
                while (curr // 10) % 10 == 9:
                    curr //= 10
                curr = curr // 10 + 1
        return res
```
The essence of this problem is to generate the numbers from 1 to n in lexicographical order.
    
### >> 60 Permutation Sequence [Medium]
Given n and k, return the kth permutation sequence of the numbers from 1 to n.
##### Sample input:
3
3

##### Sample output:
213


##### Questions to ask to clarify requirements:
What should be the maximum value of n and k? Can the input be negative?

##### Optimal Python solution:
```python
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        nums = [str(i) for i in range(1, n + 1)]
        result = ''
        k -= 1
        while n > 0:
            n -= 1
            index, k = divmod(k, math.factorial(n))
            result += nums[index]
            nums.pop(index)
        return result

```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Generate all permutations of the numbers from 1 to n.
2. Find the kth permutation by dividing k by (n-1) factorial and using the quotient as the index to select the next number.
3. Remove the selected number from the list of available numbers and repeat the process until all numbers are used.
None
None
None
    
### >> Comparison: 386 Lexicographical Numbers [Medium] *VS* 60 Permutation Sequence [Medium]
> Similarity distance: 0.5097
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve permutations or combinations.
- Both questions require understanding of lexicographical order.
##### Differences

- Question 386 involves generating all lexicographical numbers up to a given integer n.
- Question 60 involves finding the kth permutation sequence of a given set of numbers.
##### New Insights in 60 Permutation Sequence [Medium]

- Question 386 teaches us how to generate lexicographical numbers using depth-first search (DFS).
- Question 60 teaches us how to find the kth permutation sequence using factorials and backtracking.


---
# 5. From 60 Permutation Sequence [Medium] to 31 Next Permutation [Medium]
> Similarity Distance: 0.4914

### >> Reminder: 60 Permutation Sequence [Medium]
Given n and k, return the kth permutation sequence of the numbers from 1 to n.
##### Optimal Python solution:
```python
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        nums = [str(i) for i in range(1, n + 1)]
        result = ''
        k -= 1
        while n > 0:
            n -= 1
            index, k = divmod(k, math.factorial(n))
            result += nums[index]
            nums.pop(index)
        return result

```
The essence of this problem is to generate all permutations and select the kth permutation.
    
### >> 31 Next Permutation [Medium]
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.
##### Sample input:
[1,2,3]
##### Sample output:
[1,3,2]

##### Questions to ask to clarify requirements:

- What is the definition of lexicographically next greater permutation?
- Can the input contain duplicate numbers?

##### Optimal Python solution:
```python
def nextPermutation(nums):
    i = j = len(nums)-1
    while i > 0 and nums[i-1] >= nums[i]:
        i -= 1
    if i == 0:
        nums.reverse()
        return
    k = i - 1
    while nums[j] <= nums[k]:
        j -= 1
    nums[k], nums[j] = nums[j], nums[k]
    l, r = k+1, len(nums)-1
    while l < r:
        nums[l], nums[r] = nums[r], nums[l]
        l += 1
        r -= 1
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- The next permutation is the smallest possible permutation that is greater than the current permutation.
- If no next permutation is possible, rearrange the numbers to the lowest possible order (sorted in ascending order).

- Use two pointers to find the first pair of adjacent numbers in descending order.
- Use another pointer to find the next larger number to the left of the smaller number.
- Use two pointers to reverse the numbers to the right of the smaller number.

- Finding the next permutation involves finding the first pair of adjacent numbers in descending order.
- To find the next permutation, we need to swap the smaller number with the next larger number to its right, and then reverse the numbers to the right of the smaller number.

- Avoid using additional space.
- Avoid using sorting algorithms.
    
### >> Comparison: 60 Permutation Sequence [Medium] *VS* 31 Next Permutation [Medium]
> Similarity distance: 0.4914
##### Similarities

- Both questions involve permutations of a given set of numbers.
- Both questions have a medium difficulty level.
##### Differences

- The '60 Permutation Sequence' question asks for the kth permutation of a given set of numbers, while the '31 Next Permutation' question asks for the next permutation in lexicographical order.
- The '60 Permutation Sequence' question requires the use of factorials and mathematical calculations to find the kth permutation, while the '31 Next Permutation' question requires rearranging the given set of numbers to find the next permutation.
- The '60 Permutation Sequence' question has a fixed set of numbers, while the '31 Next Permutation' question allows any permutation of a given set of numbers.
##### New Insights in 31 Next Permutation [Medium]

- The '60 Permutation Sequence' question introduces the concept of finding the kth permutation using factorials and mathematical calculations.
- The '31 Next Permutation' question introduces the concept of finding the next permutation in lexicographical order by rearranging the given set of numbers.


---
# 6. From 229 Majority Element II [Medium] to 262 Trips and Users [Hard]
> Similarity Distance: 0.6463

### >> Reminder: 229 Majority Element II [Medium]
Given an integer array of size n, find all elements that appear more than ⌊n/3⌋ times.
##### Optimal Python solution:
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        count1, count2, candidate1, candidate2 = 0, 0, 0, 1
        for num in nums:
            if num == candidate1:
                count1 += 1
            elif num == candidate2:
                count2 += 1
            elif count1 == 0:
                candidate1, count1 = num, 1
            elif count2 == 0:
                candidate2, count2 = num, 1
            else:
                count1, count2 = count1 - 1, count2 - 1
        return [n for n in (candidate1, candidate2) if nums.count(n) > len(nums) // 3]
```
The essence of this problem is to find the majority elements that appear more than ⌊n/3⌋ times in an array.
    
### >> 262 Trips and Users [Hard]
The Trips table holds all taxi trips. Each trip has a unique Id, while Client_Id and Driver_Id are both foreign keys to the Users_Id at the Users table. Status is an ENUM type of (‘completed’, ‘cancelled_by_driver’, ‘cancelled_by_client’).
##### Sample input:
Trips table:
+----+-----------+-----------+---------+--------------------+
| Id | Client_Id | Driver_Id | City_Id |        Status      |
+----+-----------+-----------+---------+--------------------+
| 1  |     1     |    10     |    1    |     completed      |
| 2  |     2     |    11     |    1    | cancelled_by_driver|
| 3  |     3     |    12     |    6    |     completed      |
| 4  |     4     |    13     |    6    | cancelled_by_client|
+----+-----------+-----------+---------+--------------------+
Users table:
+------+--------+
| Id   | Banned |
+------+--------+
| 1    | No     |
| 10   | No     |
| 11   | Yes    |
| 12   | No     |
| 13   | Yes    |
+------+--------+
##### Sample output:
BannedUsers table:
+----------+
|    Id    |
+----------+
|    11    |
|    13    |
+----------+

##### Questions to ask to clarify requirements:

- What is the expected output format?
- Can there be multiple trips with the same Driver_Id?
- Can there be multiple users with the same Id?

##### Optimal Python solution:
```python
SELECT DISTINCT t.Driver_Id AS Id
FROM Trips t
JOIN Users u ON t.Driver_Id = u.Id
WHERE u.Banned = 'Yes'
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a join operation to combine the Trips and Users tables.
- Use the DISTINCT keyword to remove duplicate entries.
- Filter the result based on the 'Banned' column in the Users table.

- Understand the syntax and usage of join operations in SQL.
- Use the DISTINCT keyword to remove duplicate entries from the result.

- Handling duplicate entries in the result.
- Understanding the join operation and its syntax.

- Using subqueries instead of joins.
- Using the GROUP BY clause instead of DISTINCT.
    
### >> Comparison: 229 Majority Element II [Medium] *VS* 262 Trips and Users [Hard]
> Similarity distance: 0.6463
##### Similarities

- Both questions are related to finding elements that appear more than a certain threshold in an array or dataset.
##### Differences

- Question 229 focuses on finding the majority elements that appear more than n/3 times in an array, while question 262 focuses on finding the users who have made more than n trips.
- Question 229 requires finding the majority elements in a single array, while question 262 involves analyzing multiple arrays and their relationships.
- Question 229 has a complexity requirement of O(1) space, while question 262 does not have a specific space complexity requirement.
##### New Insights in 262 Trips and Users [Hard]

- Question 229 introduces the concept of finding majority elements using the Boyer-Moore Voting Algorithm.
- Question 262 introduces the concept of analyzing user trips and their relationships using SQL queries.

