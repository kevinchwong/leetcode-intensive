
# Leetcode Intensive Tutorial Day 5 
> [Difficulty Score: 12]

> [Version: 20231226_040350]

> [Including this day, you had studied : 35 leetcode problems]


## Courses overview of the day

- 414 Third Maximum Number [Easy]
  - 217 Contains Duplicate [Easy]
    - 384 Shuffle an Array [Medium]
  - 82 Remove Duplicates from Sorted List II [Medium]
    - 83 Remove Duplicates from Sorted List [Easy]
    - 26 Remove Duplicates from Sorted Array [Easy]
    - 316 Remove Duplicate Letters [Hard]

#### Step by step

 - [1. From 414 Third Maximum Number [Easy] to 217 Contains Duplicate [Easy]](#1-from-414-third-maximum-number-easy-to-217-contains-duplicate-easy))

 - [2. From 217 Contains Duplicate [Easy] to 384 Shuffle an Array [Medium]](#2-from-217-contains-duplicate-easy-to-384-shuffle-an-array-medium))

 - [3. From 414 Third Maximum Number [Easy] to 82 Remove Duplicates from Sorted List II [Medium]](#3-from-414-third-maximum-number-easy-to-82-remove-duplicates-from-sorted-list-ii-medium))

 - [4. From 82 Remove Duplicates from Sorted List II [Medium] to 83 Remove Duplicates from Sorted List [Easy]](#4-from-82-remove-duplicates-from-sorted-list-ii-medium-to-83-remove-duplicates-from-sorted-list-easy))

 - [5. From 82 Remove Duplicates from Sorted List II [Medium] to 26 Remove Duplicates from Sorted Array [Easy]](#5-from-82-remove-duplicates-from-sorted-list-ii-medium-to-26-remove-duplicates-from-sorted-array-easy))

 - [6. From 82 Remove Duplicates from Sorted List II [Medium] to 316 Remove Duplicate Letters [Hard]](#6-from-82-remove-duplicates-from-sorted-list-ii-medium-to-316-remove-duplicate-letters-hard))

    

#### Summary


- 384 Shuffle an Array : Store the original array and a shuffled copy. Use the random.shuffle() function to shuffle the copy when needed.
- 316 Remove Duplicate Letters : Remove duplicate letters from a string and keep the result in lexicographical order.
- 82 Remove Duplicates from Sorted List II : Remove duplicates from sorted linked list.
- 414 Third Maximum Number : Return the third maximum number in an array, or the maximum number if it does not exist.
- 217 Contains Duplicate : Check for duplicate elements in an array using a set.
- 26 Remove Duplicates from Sorted Array : Removing duplicates from a sorted array in-place.
- 83 Remove Duplicates from Sorted List : The essence of this problem is to remove duplicates from a sorted linked list.
> Similarity Diameter of these problems: 0.5712


---
# 1. From 414 Third Maximum Number [Easy] to 217 Contains Duplicate [Easy]
> Similarity Distance: 0.4657

### >> 414 Third Maximum Number [Easy]
Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number.
##### Sample input:
[3, 2, 1]
##### Sample output:
1

##### Questions to ask to clarify requirements:

- What should be returned if the array contains less than three distinct numbers?
- Can the array contain negative numbers?
- Can the array be empty?

##### Optimal Python solution:
```python
def thirdMax(nums):
    nums = list(set(nums))
    if len(nums) < 3:
        return max(nums)
    else:
        nums.remove(max(nums))
        nums.remove(max(nums))
        return max(nums)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Remove duplicates from the array using a set.
- If the length of the array is less than 3, return the maximum number.
- Otherwise, remove the first and second maximum numbers and return the maximum number.

- Understand the definition of distinct numbers.
- Use a set to remove duplicates from the array.
- Handle edge cases such as arrays with less than three distinct numbers.

- Handling edge cases such as arrays with less than three distinct numbers.
- Removing the first and second maximum numbers from the array.

- Sorting the array and returning the third maximum number.
- Using extra space to store intermediate results.
    
### >> 217 Contains Duplicate [Easy]
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
##### Sample input:
[1,2,3,1]
##### Sample output:
true

##### Questions to ask to clarify requirements:
Are negative numbers allowed in the array?

##### Optimal Python solution:
```python
def containsDuplicate(nums):
    return len(nums) != len(set(nums))
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use a set to check for duplicate elements.
Use the set data structure to efficiently check for duplicate elements.
None
None
    
### >> Comparison: 414 Third Maximum Number [Easy] *VS* 217 Contains Duplicate [Easy]
> Similarity distance: 0.4657
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating arrays.
- Both questions require finding a specific value in an array.
##### Differences

- Question 414 involves finding the third maximum number in an array, while question 217 involves finding duplicate elements in an array.
- Question 414 requires returning the third maximum number, while question 217 requires returning whether there are any duplicate elements.
- Question 414 has a time complexity requirement of O(n), while question 217 does not have a specific time complexity requirement.
##### New Insights in 217 Contains Duplicate [Easy]

- Question 414: To find the third maximum number, we can use a set to keep track of the three maximum numbers encountered so far.
- Question 217: To check for duplicate elements, we can use a set to keep track of the unique elements encountered so far.


---
# 2. From 217 Contains Duplicate [Easy] to 384 Shuffle an Array [Medium]
> Similarity Distance: 0.5267

### >> Reminder: 217 Contains Duplicate [Easy]
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
##### Optimal Python solution:
```python
def containsDuplicate(nums):
    return len(nums) != len(set(nums))
```
Check for duplicate elements in an array using a set.
    
### >> 384 Shuffle an Array [Medium]
Design an algorithm to randomly shuffle an array of distinct numbers without using the Fisher-Yates shuffle algorithm.
##### Sample input:
[1, 2, 3]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
##### Sample output:
Random output
Random output

##### Questions to ask to clarify requirements:
Can we assume the input array always contains distinct numbers? Can we use the random.shuffle() function?

##### Optimal Python solution:
```python
import random

class Solution:

    def __init__(self, nums: List[int]):
        self.original = nums
        self.shuffled = nums.copy()

    def reset(self) -> List[int]:
        return self.original

    def shuffle(self) -> List[int]:
        random.shuffle(self.shuffled)
        return self.shuffled
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Store the original array and a shuffled copy. Use the random.shuffle() function to shuffle the copy when needed.
Use the copy() method to create a copy of the array.
None
None
    
### >> Comparison: 217 Contains Duplicate [Easy] *VS* 384 Shuffle an Array [Medium]
> Similarity distance: 0.5267
##### Similarities

- Both questions involve manipulating an array.
- Both questions require checking for duplicates in the array.
##### Differences

- Question 217 is classified as Easy, while question 384 is classified as Medium.
- Question 217 asks to determine if the array contains any duplicates, while question 384 asks to shuffle the array randomly.
- Question 217 can be solved using a hash set to check for duplicates, while question 384 requires implementing the Fisher-Yates shuffle algorithm.
##### New Insights in 384 Shuffle an Array [Medium]

- Question 217 teaches us how to efficiently check for duplicates in an array using a hash set.
- Question 384 introduces us to the Fisher-Yates shuffle algorithm, which is used to randomly shuffle an array.


---
# 3. From 414 Third Maximum Number [Easy] to 82 Remove Duplicates from Sorted List II [Medium]
> Similarity Distance: 0.4678

### >> Reminder: 414 Third Maximum Number [Easy]
Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number.
##### Optimal Python solution:
```python
def thirdMax(nums):
    nums = list(set(nums))
    if len(nums) < 3:
        return max(nums)
    else:
        nums.remove(max(nums))
        nums.remove(max(nums))
        return max(nums)
```
Return the third maximum number in an array, or the maximum number if it does not exist.
    
### >> 82 Remove Duplicates from Sorted List II [Medium]
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
##### Sample input:
[1,2,3,3,4,4,5]
##### Sample output:
[1,2,5]

##### Questions to ask to clarify requirements:

- Can the linked list be empty?
- Can the linked list contain negative numbers?
- Can the linked list contain cycles?

##### Optimal Python solution:
```python
def deleteDuplicates(head):
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    curr = head
    while curr:
        while curr.next and curr.val == curr.next.val:
            curr = curr.next
        if prev.next == curr:
            prev = prev.next
        else:
            prev.next = curr.next
        curr = curr.next
    return dummy.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use a dummy node to handle the case where the head of the linked list is a duplicate.
- Iterate through the linked list and skip duplicate nodes.
- Update the previous node's next pointer to skip duplicate nodes.

- Use a dummy node to handle the case where the head of the linked list is a duplicate.
- Iterate through the linked list and skip duplicate nodes.
- Update the previous node's next pointer to skip duplicate nodes.

- Handling the case where the head of the linked list is a duplicate.
- Updating the previous node's next pointer to skip duplicate nodes.

- Using extra space.
- Using recursion.
    
### >> Comparison: 414 Third Maximum Number [Easy] *VS* 82 Remove Duplicates from Sorted List II [Medium]
> Similarity distance: 0.4678
##### Similarities

- Both questions involve manipulating arrays or linked lists.
- Both questions require finding and removing duplicates.
- Both questions have a specific condition to determine the maximum or minimum value.
##### Differences

- 414 Third Maximum Number: Involves finding the third maximum number in an array.
- 82 Remove Duplicates from Sorted List II: Involves removing duplicates from a sorted linked list and keeping only distinct elements.
##### New Insights in 82 Remove Duplicates from Sorted List II [Medium]

- 414 Third Maximum Number: The solution requires keeping track of the three maximum numbers using three variables.
- 82 Remove Duplicates from Sorted List II: The solution requires using a dummy node and two pointers to remove duplicates.


---
# 4. From 82 Remove Duplicates from Sorted List II [Medium] to 83 Remove Duplicates from Sorted List [Easy]
> Similarity Distance: 0.3366

### >> Reminder: 82 Remove Duplicates from Sorted List II [Medium]
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
##### Optimal Python solution:
```python
def deleteDuplicates(head):
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    curr = head
    while curr:
        while curr.next and curr.val == curr.next.val:
            curr = curr.next
        if prev.next == curr:
            prev = prev.next
        else:
            prev.next = curr.next
        curr = curr.next
    return dummy.next
```
Remove duplicates from sorted linked list.
    
### >> 83 Remove Duplicates from Sorted List [Easy]
Given a sorted linked list, delete all duplicates such that each element appears only once.
##### Sample input:
1->1->2
1->1->2->3->3
##### Sample output:
1->2
1->2->3

##### Questions to ask to clarify requirements:
What is the format of the linked list? Can the input list be empty?

##### Optimal Python solution:
```python
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        if not head:
            return head
        curr = head
        while curr.next:
            if curr.val == curr.next.val:
                curr.next = curr.next.next
            else:
                curr = curr.next
        return head
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a pointer to iterate through the linked list
2. Compare the current node with the next node
3. If they are the same, skip the next node
4. If they are different, move to the next node
5. Return the head of the modified linked list
Make sure to handle edge cases such as an empty linked list.
None
None
    
### >> Comparison: 82 Remove Duplicates from Sorted List II [Medium] *VS* 83 Remove Duplicates from Sorted List [Easy]
> Similarity distance: 0.3366
##### Similarities

- Both questions involve removing duplicates from a sorted linked list.
- Both questions have a similar input and output format.
##### Differences

- Question 82 (Remove Duplicates from Sorted List II) removes all nodes that have duplicate values, while Question 83 (Remove Duplicates from Sorted List) removes only the duplicate nodes.
- Question 82 requires removing all duplicates, even if they occur more than twice, while Question 83 removes duplicates that occur more than once.
- Question 82 has a higher difficulty level (Medium) compared to Question 83 (Easy).
##### New Insights in 83 Remove Duplicates from Sorted List [Easy]

- Question 82 requires keeping track of the previous node to remove duplicates, while Question 83 does not require this additional step.
- Both questions can be solved using a similar approach of iterating through the linked list and removing duplicates.


---
# 5. From 82 Remove Duplicates from Sorted List II [Medium] to 26 Remove Duplicates from Sorted Array [Easy]
> Similarity Distance: 0.3591

### >> Reminder: 82 Remove Duplicates from Sorted List II [Medium]
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
##### Optimal Python solution:
```python
def deleteDuplicates(head):
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    curr = head
    while curr:
        while curr.next and curr.val == curr.next.val:
            curr = curr.next
        if prev.next == curr:
            prev = prev.next
        else:
            prev.next = curr.next
        curr = curr.next
    return dummy.next
```
Remove duplicates from sorted linked list.
    
### >> 26 Remove Duplicates from Sorted Array [Easy]
Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.
##### Sample input:
nums = [1,1,2]
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can we modify the original array?
- What should be returned if the array is empty?
- Can we assume the array is always sorted?

##### Optimal Python solution:
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if not nums:
            return 0
        i = 0
        for j in range(1, len(nums)):
            if nums[j] != nums[i]:
                i += 1
                nums[i] = nums[j]
        return i + 1
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Remove duplicates in-place
- Use two pointers to track the current and next non-duplicate elements

- Use two pointers to track the current and next non-duplicate elements
- Update the array in-place by replacing the duplicate elements

- Updating the array in-place while removing duplicates

- Using additional data structures to track duplicates
    
### >> Comparison: 82 Remove Duplicates from Sorted List II [Medium] *VS* 26 Remove Duplicates from Sorted Array [Easy]
> Similarity distance: 0.3591
##### Similarities

- Both questions involve removing duplicates from a sorted list or array.
- Both questions require modifying the original data structure.
##### Differences

- Question 82 deals with a linked list, while question 26 deals with an array.
- Question 82 allows duplicates to be present in the final list, while question 26 requires all elements to be unique.
- Question 82 has a time complexity of O(n), while question 26 has a time complexity of O(n^2) if using the naive approach.
- Question 82 requires the use of pointers to manipulate the linked list, while question 26 uses array manipulation techniques.
##### New Insights in 26 Remove Duplicates from Sorted Array [Easy]

- Question 82 introduces the concept of linked list manipulation and pointer operations.
- Question 26 highlights the importance of efficient array manipulation techniques to remove duplicates.


---
# 6. From 82 Remove Duplicates from Sorted List II [Medium] to 316 Remove Duplicate Letters [Hard]
> Similarity Distance: 0.3889

### >> Reminder: 82 Remove Duplicates from Sorted List II [Medium]
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
##### Optimal Python solution:
```python
def deleteDuplicates(head):
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    curr = head
    while curr:
        while curr.next and curr.val == curr.next.val:
            curr = curr.next
        if prev.next == curr:
            prev = prev.next
        else:
            prev.next = curr.next
        curr = curr.next
    return dummy.next
```
Remove duplicates from sorted linked list.
    
### >> 316 Remove Duplicate Letters [Hard]
Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is the smallest in lexicographical order among all possible results.
##### Sample input:
"bcabc"
##### Sample output:
"abc"

##### Questions to ask to clarify requirements:

- Can the input string contain spaces?
- Can the input string contain special characters?
- What is the maximum length of the input string?

##### Optimal Python solution:
```python
def removeDuplicateLetters(s):
    counter = Counter(s)
    stack = []
    visited = set()
    for char in s:
        counter[char] -= 1
        if char in visited:
            continue
        while stack and char < stack[-1] and counter[stack[-1]] > 0:
            visited.remove(stack.pop())
        stack.append(char)
        visited.add(char)
    return ''.join(stack)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a stack to keep track of the characters in the result.
- Remove characters from the stack if a smaller character is encountered later.
- Keep track of the characters visited to avoid duplicates.

- Keep track of the characters visited to avoid duplicates.
- Remove characters from the stack if a smaller character is encountered later.

- Removing characters from the stack if a smaller character is encountered later.
- Keeping track of the characters visited to avoid duplicates.

- Using a nested loop to compare each character with the characters visited and in the result.
    
### >> Comparison: 82 Remove Duplicates from Sorted List II [Medium] *VS* 316 Remove Duplicate Letters [Hard]
> Similarity distance: 0.3889
##### Similarities

- Both questions involve removing duplicates from a given list or string.
- Both questions require maintaining the order of the remaining elements.
- Both questions have a complexity requirement of O(n).
##### Differences

- Question 82 deals with removing duplicates from a sorted linked list, while question 316 deals with removing duplicates from a string.
- Question 82 allows removing all occurrences of a duplicate element, while question 316 requires keeping at least one occurrence of each duplicate element.
- Question 82 has a complexity requirement of O(n), while question 316 has a complexity requirement of O(n^2).
##### New Insights in 316 Remove Duplicate Letters [Hard]

- Question 82 can be solved using a two-pointer approach, where one pointer tracks the current element and the other pointer tracks the previous distinct element.
- Question 316 can be solved using a greedy approach, where we maintain a stack to store the final result and keep track of the last occurrence of each character.

