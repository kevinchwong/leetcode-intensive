
# Leetcode Intensive Tutorial Day 27 
> [Difficulty Score: 17]

> [Version: 20231225_200427]

## Courses overview of the day

- 160 Intersection of Two Linked Lists [Easy]
  - 21 Merge Two Sorted Lists [Easy]
  - 141 Linked List Cycle [Easy]
    - 142 Linked List Cycle II [Medium]
  - 19 Remove Nth Node From End of List [Medium]
  - 466 Count The Repetitions [Hard]
    - 11 Container With Most Water [Medium]
      - 42 Trapping Rain Water [Hard]

#### Steps by steps

 - [1. From 160 Intersection of Two Linked Lists [Easy] to 21 Merge Two Sorted Lists [Easy]](#1-from-160-intersection-of-two-linked-lists-easy-to-21-merge-two-sorted-lists-easy)

 - [2. From 160 Intersection of Two Linked Lists [Easy] to 141 Linked List Cycle [Easy]](#2-from-160-intersection-of-two-linked-lists-easy-to-141-linked-list-cycle-easy)

 - [3. From 141 Linked List Cycle [Easy] to 142 Linked List Cycle II [Medium]](#3-from-141-linked-list-cycle-easy-to-142-linked-list-cycle-ii-medium)

 - [4. From 160 Intersection of Two Linked Lists [Easy] to 19 Remove Nth Node From End of List [Medium]](#4-from-160-intersection-of-two-linked-lists-easy-to-19-remove-nth-node-from-end-of-list-medium)

 - [5. From 160 Intersection of Two Linked Lists [Easy] to 466 Count The Repetitions [Hard]](#5-from-160-intersection-of-two-linked-lists-easy-to-466-count-the-repetitions-hard)

 - [6. From 466 Count The Repetitions [Hard] to 11 Container With Most Water [Medium]](#6-from-466-count-the-repetitions-hard-to-11-container-with-most-water-medium)

 - [7. From 11 Container With Most Water [Medium] to 42 Trapping Rain Water [Hard]](#7-from-11-container-with-most-water-medium-to-42-trapping-rain-water-hard)

#### Summary


- 42 Trapping Rain Water : Using two pointers to track boundaries and variables to track maximum elevations.
- 160 Intersection of Two Linked Lists : The essence of this problem is to find the intersection node of two linked lists using two pointers.
- 11 Container With Most Water : The essence of this problem is to find the container with the most water by using the two pointers approach.
- 21 Merge Two Sorted Lists : Merge two sorted linked lists using a dummy node and two pointers.
- 466 Count The Repetitions : The essence of this problem is to find the maximum number of times one string can be obtained from another string.
- 142 Linked List Cycle II : Detecting the start of a cycle in a linked list using two pointers.
- 19 Remove Nth Node From End of List : Removing a node from a linked list by finding its position from the end.
- 141 Linked List Cycle : Detecting a cycle in a linked list using two pointers.
> Similarity Diameter of these problems: 0.7539


---
# 1. From 160 Intersection of Two Linked Lists [Easy] to 21 Merge Two Sorted Lists [Easy]
> Similarity Distance: 0.4337

### >> 160 Intersection of Two Linked Lists [Easy]
Write a program to find the node at which the intersection of two singly linked lists begins.
##### Sample input:
headA = [4,1,8,4,5], headB = [5,0,1,8,4,5]
##### Sample output:
8

##### Questions to ask to clarify requirements:
Can the linked lists have cycles? Can the intersection node be None?

##### Optimal Python solution:
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
##### Time complexity:
O(m + n)
##### Space complexity:
O(1)
##### Notes:
Use two pointers to traverse the linked lists. If one pointer reaches the end, move it to the head of the other linked list. Repeat until the two pointers meet at the intersection node.
Draw a diagram to visualize the movement of the pointers and understand how they converge at the intersection node.
Handling the case when the two linked lists have different lengths.
Using extra space to store the nodes of the linked lists.
    
### >> 21 Merge Two Sorted Lists [Easy]
Merge two sorted linked lists and return it as a sorted list.
##### Sample input:
[1,2,4]
[1,3,4]
##### Sample output:
[1,1,2,3,4,4]

##### Questions to ask to clarify requirements:
Are the linked lists singly linked or doubly linked?

##### Optimal Python solution:
```python
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
    dummy = ListNode(0)
    curr = dummy
    while l1 and l2:
        if l1.val < l2.val:
            curr.next = l1
            l1 = l1.next
        else:
            curr.next = l2
            l2 = l2.next
        curr = curr.next
    curr.next = l1 or l2
    return dummy.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a dummy node to simplify the code.
2. Use two pointers to iterate through the linked lists.
3. Connect the smaller node to the result list.
4. Handle the remaining nodes after one list is exhausted.
1. Use a dummy node to simplify the code.
2. Use two pointers to iterate through the linked lists.
3. Connect the smaller node to the result list.
4. Handle the remaining nodes after one list is exhausted.
None
None
    
### >> Comparison: 160 Intersection of Two Linked Lists [Easy] *VS* 21 Merge Two Sorted Lists [Easy]
> Similarity distance: 0.4337
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions have a time complexity of O(n).
##### Differences

- Question 160 involves finding the intersection of two linked lists, while question 21 involves merging two sorted lists.
- Question 160 requires finding the node where the two lists intersect, while question 21 requires merging the two lists in sorted order.
- Question 160 may have multiple intersections, while question 21 has only one possible merged list.
- Question 160 may have lists of different lengths, while question 21 assumes both lists have the same length.
##### New Insights in 21 Merge Two Sorted Lists [Easy]

- Question 160 can be solved using a two-pointer approach, where two pointers traverse the lists until they meet at the intersection.
- Question 21 can be solved using a recursive approach, where the smaller value is appended to the merged list, and the function is called recursively with the next nodes.


---
# 2. From 160 Intersection of Two Linked Lists [Easy] to 141 Linked List Cycle [Easy]
> Similarity Distance: 0.4358

### >> Reminder: 160 Intersection of Two Linked Lists [Easy]
Write a program to find the node at which the intersection of two singly linked lists begins.
##### Optimal Python solution:
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
The essence of this problem is to find the intersection node of two linked lists using two pointers.
    
### >> 141 Linked List Cycle [Easy]
Given a linked list, determine if it has a cycle in it.
##### Sample input:
head = [3,2,0,-4]
pos = 1
##### Sample output:
True

##### Questions to ask to clarify requirements:
What is the definition of a cycle in a linked list?

##### Optimal Python solution:
```python
def hasCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use two pointers, slow and fast, to traverse the linked list. If there is a cycle, the fast pointer will eventually catch up to the slow pointer.
Make sure to handle the case where the linked list is empty.
Handling the case where the linked list is empty.
Using additional data structures.
    
### >> Comparison: 160 Intersection of Two Linked Lists [Easy] *VS* 141 Linked List Cycle [Easy]
> Similarity distance: 0.4358
##### Similarities

- Both questions are related to linked lists.
- Both questions have an easy difficulty level.
##### Differences

- Question 160 involves finding the intersection of two linked lists, while question 141 involves detecting a cycle in a linked list.
- Question 160 requires comparing two linked lists, while question 141 requires detecting a cycle using a two-pointer approach.
- Question 160 has a time complexity of O(m+n), where m and n are the lengths of the linked lists, while question 141 has a time complexity of O(n), where n is the length of the linked list.
##### New Insights in 141 Linked List Cycle [Easy]

- Question 160: The intersection point of two linked lists can be found by comparing the lengths of the lists and adjusting the starting points.
- Question 141: The presence of a cycle in a linked list can be detected using the two-pointer approach, where one pointer moves one step at a time and the other pointer moves two steps at a time. If the two pointers meet, there is a cycle.


---
# 3. From 141 Linked List Cycle [Easy] to 142 Linked List Cycle II [Medium]
> Similarity Distance: 0.4750

### >> Reminder: 141 Linked List Cycle [Easy]
Given a linked list, determine if it has a cycle in it.
##### Optimal Python solution:
```python
def hasCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```
Detecting a cycle in a linked list using two pointers.
    
### >> 142 Linked List Cycle II [Medium]
Given a linked list, return the node where the cycle begins. If there is no cycle, return null.
##### Sample input:
head = [3,2,0,-4]
pos = 1
##### Sample output:
Node with value 2

##### Questions to ask to clarify requirements:
What is the definition of a cycle in a linked list?

##### Optimal Python solution:
```python
def detectCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            break
    else:
        return None
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next
    return slow
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use two pointers, slow and fast, to detect the cycle. Once the cycle is detected, reset the slow pointer to the head and move both pointers at the same pace until they meet at the start of the cycle.
Make sure to handle the case where the linked list is empty or has no cycle.
Handling the case where the linked list is empty or has no cycle.
Using additional data structures.
    
### >> Comparison: 141 Linked List Cycle [Easy] *VS* 142 Linked List Cycle II [Medium]
> Similarity distance: 0.4750
##### Similarities

- Both questions are related to detecting cycles in a linked list.
- Both questions have a time complexity of O(n).
##### Differences

- 141 Linked List Cycle is an easy level question, while 142 Linked List Cycle II is a medium level question.
- In 141 Linked List Cycle, we only need to determine if there is a cycle in the linked list, while in 142 Linked List Cycle II, we need to find the node where the cycle begins.
- 142 Linked List Cycle II requires additional space to solve the problem, while 141 Linked List Cycle does not.
##### New Insights in 142 Linked List Cycle II [Medium]

- In both questions, we can use the two-pointer technique to detect cycles in a linked list.
- In 142 Linked List Cycle II, we can use the Floyd's cycle-finding algorithm to find the node where the cycle begins.


---
# 4. From 160 Intersection of Two Linked Lists [Easy] to 19 Remove Nth Node From End of List [Medium]
> Similarity Distance: 0.4845

### >> Reminder: 160 Intersection of Two Linked Lists [Easy]
Write a program to find the node at which the intersection of two singly linked lists begins.
##### Optimal Python solution:
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
The essence of this problem is to find the intersection node of two linked lists using two pointers.
    
### >> 19 Remove Nth Node From End of List [Medium]
Given a linked list, remove the n-th node from the end of list and return its head.
##### Sample input:
head = [1,2,3,4,5], n = 2
##### Sample output:
[1,2,3,5]

##### Questions to ask to clarify requirements:
What is the range of n? Can we assume n is always valid?

##### Optimal Python solution:
```python
def removeNthFromEnd(head, n):
    dummy = ListNode(0)
    dummy.next = head
    slow = fast = dummy
    for _ in range(n):
        fast = fast.next
    while fast.next:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return dummy.next
```
##### Time complexity:
O(N)
##### Space complexity:
O(1)
##### Notes:
Use two pointers to find the n-th node from the end of the list. Maintain a gap of n between the two pointers.
Always handle edge cases and validate inputs before performing any operations on the linked list.
Handling the case where the node to be removed is the head of the list.
Modifying the linked list directly without using a dummy node.
    
### >> Comparison: 160 Intersection of Two Linked Lists [Easy] *VS* 19 Remove Nth Node From End of List [Medium]
> Similarity distance: 0.4845
##### Similarities

- Both questions involve linked lists.
- Both questions require traversing the linked list.
- Both questions involve finding a specific node in the linked list.
##### Differences

- Question 160 involves finding the intersection point of two linked lists, while question 19 involves removing the nth node from the end of a linked list.
- Question 160 requires comparing two linked lists, while question 19 only involves a single linked list.
- Question 160 has an easy difficulty level, while question 19 has a medium difficulty level.
##### New Insights in 19 Remove Nth Node From End of List [Medium]

- Question 160: To find the intersection point, we can use two pointers to traverse the linked lists and compare their lengths.
- Question 19: To remove the nth node from the end, we can use two pointers with a distance of n between them.


---
# 5. From 160 Intersection of Two Linked Lists [Easy] to 466 Count The Repetitions [Hard]
> Similarity Distance: 0.5322

### >> Reminder: 160 Intersection of Two Linked Lists [Easy]
Write a program to find the node at which the intersection of two singly linked lists begins.
##### Optimal Python solution:
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
The essence of this problem is to find the intersection node of two linked lists using two pointers.
    
### >> 466 Count The Repetitions [Hard]
Define S = [s,n] as the string S which consists of n connected strings s. For example, ['abc', 3] = 'abcabcabc'. On the other hand, we define that string s1 can be obtained from string s2 if we can remove some characters from s2 such that it becomes s1. For example, “abc” can be obtained from “abdbec” based on our definition, but it can not be obtained from “acbbe”. You are given two non-empty strings s1 and s2 (each at most 100 characters long) and two integers 0 ≤ n1 ≤ 106 and 1 ≤ n2 ≤ 106. Now consider the strings S1 and S2, where S1=[s1,n1] and S2=[s2,n2]. Find the maximum integer M such that [S2,M] can be obtained from S1.
##### Sample input:
s1 = 'acb', n1 = 4, s2 = 'ab', n2 = 2
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can the strings contain special characters?
- Can the strings be empty?
- Can the integers be negative?

##### Optimal Python solution:
```python
def getMaxRepetitions(s1, n1, s2, n2):
    count1, count2, i, j = 0, 0, 0, 0
    while count1 < n1:
        if s1[i] == s2[j]:
            j += 1
            if j == len(s2):
                j = 0
                count2 += 1
        i += 1
        if i == len(s1):
            i = 0
            count1 += 1
    return count2 // n2
```
##### Time complexity:
O(n1 * n2 * len(s1))
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to iterate through the strings
- Count the number of times s2 can be obtained from s1

- Use two pointers to iterate through the strings
- Count the number of times s2 can be obtained from s1

- The problem can be solved using two pointers and counting

- Avoid using brute force to check all possible combinations of strings
    
### >> Comparison: 160 Intersection of Two Linked Lists [Easy] *VS* 466 Count The Repetitions [Hard]
> Similarity distance: 0.5322
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions require finding intersections or repetitions.
- Both questions have a time complexity of O(n).
##### Differences

- 160 Intersection of Two Linked Lists is an easy question, while 466 Count The Repetitions is a hard question.
- 160 Intersection of Two Linked Lists requires finding the intersection point of two linked lists, while 466 Count The Repetitions requires counting the number of repetitions in a given string.
- 160 Intersection of Two Linked Lists has a space complexity of O(1), while 466 Count The Repetitions has a space complexity of O(n).
##### New Insights in 466 Count The Repetitions [Hard]

- 160 Intersection of Two Linked Lists teaches us how to find the intersection point of two linked lists using two pointers.
- 466 Count The Repetitions teaches us how to count the number of repetitions in a given string using dynamic programming.


---
# 6. From 466 Count The Repetitions [Hard] to 11 Container With Most Water [Medium]
> Similarity Distance: 0.5062

### >> Reminder: 466 Count The Repetitions [Hard]
Define S = [s,n] as the string S which consists of n connected strings s. For example, ['abc', 3] = 'abcabcabc'. On the other hand, we define that string s1 can be obtained from string s2 if we can remove some characters from s2 such that it becomes s1. For example, “abc” can be obtained from “abdbec” based on our definition, but it can not be obtained from “acbbe”. You are given two non-empty strings s1 and s2 (each at most 100 characters long) and two integers 0 ≤ n1 ≤ 106 and 1 ≤ n2 ≤ 106. Now consider the strings S1 and S2, where S1=[s1,n1] and S2=[s2,n2]. Find the maximum integer M such that [S2,M] can be obtained from S1.
##### Optimal Python solution:
```python
def getMaxRepetitions(s1, n1, s2, n2):
    count1, count2, i, j = 0, 0, 0, 0
    while count1 < n1:
        if s1[i] == s2[j]:
            j += 1
            if j == len(s2):
                j = 0
                count2 += 1
        i += 1
        if i == len(s1):
            i = 0
            count1 += 1
    return count2 // n2
```
The essence of this problem is to find the maximum number of times one string can be obtained from another string.
    
### >> 11 Container With Most Water [Medium]
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.
##### Sample input:
[1,8,6,2,5,4,8,3,7]
##### Sample output:
49

##### Questions to ask to clarify requirements:

- Can the input array be empty?
- Can the input array contain negative integers?

##### Optimal Python solution:
```python
def maxArea(height):
    max_area = 0
    left = 0
    right = len(height) - 1
    while left < right:
        area = min(height[left], height[right]) * (right - left)
        max_area = max(max_area, area)
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_area
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- The area of a container is determined by the shorter line and the distance between the lines.
- Using two pointers, start with the widest container and move the pointers towards each other to find a higher line.
- The time complexity of the solution is O(n) and the space complexity is O(1).

- Use meaningful variable names to improve code readability.
- Break down the problem into smaller subproblems to make it easier to solve.
- Test the solution with different inputs to ensure it handles all edge cases.

- The intuition behind the two pointers approach can be a bit tricky to understand at first.
- The solution requires careful handling of the pointers to ensure the correct area is calculated.

- Avoid using a brute force approach that checks all possible combinations of lines.
- Avoid using additional data structures to store intermediate results.
    
### >> Comparison: 466 Count The Repetitions [Hard] *VS* 11 Container With Most Water [Medium]
> Similarity distance: 0.5062
##### Similarities

- Both questions involve finding the maximum value based on certain conditions.
- Both questions require iterating through an array or a set of elements.
- Both questions have a time complexity of O(n).
##### Differences

- Question 466 involves counting the number of repetitions of a pattern in a string, while question 11 involves finding the maximum area between two vertical lines in a histogram.
- Question 466 requires considering the order of elements, while question 11 does not.
- Question 466 involves dynamic programming, while question 11 does not.
##### New Insights in 11 Container With Most Water [Medium]

- Question 466 introduces the concept of counting repetitions and using dynamic programming to optimize the solution.
- Question 11 introduces the concept of finding the maximum area between two vertical lines using two pointers.


---
# 7. From 11 Container With Most Water [Medium] to 42 Trapping Rain Water [Hard]
> Similarity Distance: 0.5821

### >> Reminder: 11 Container With Most Water [Medium]
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.
##### Optimal Python solution:
```python
def maxArea(height):
    max_area = 0
    left = 0
    right = len(height) - 1
    while left < right:
        area = min(height[left], height[right]) * (right - left)
        max_area = max(max_area, area)
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_area
```
The essence of this problem is to find the container with the most water by using the two pointers approach.
    
### >> 42 Trapping Rain Water [Hard]
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.
##### Sample input:
[0,1,0,2,1,0,1,3,2,1,2,1]
##### Sample output:
6

##### Questions to ask to clarify requirements:

- What should be the time complexity of the solution?
- What should be the space complexity of the solution?

##### Optimal Python solution:
```python
def trap(height):
    n = len(height)
    left = 0
    right = n - 1
    left_max = 0
    right_max = 0
    result = 0
    while left < right:
        if height[left] < height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                result += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                result += right_max - height[right]
            right -= 1
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to track the left and right boundaries.
- Use two variables to track the maximum elevation on the left and right.
- Calculate the amount of water trapped at each bar.

- Understand the two-pointer technique.
- Handle edge cases such as empty elevation maps and negative elevations.

- Tracking the maximum elevation on the left and right.
- Calculating the amount of water trapped at each bar.

- Using extra space.
- Sorting the array.
    
### >> Comparison: 11 Container With Most Water [Medium] *VS* 42 Trapping Rain Water [Hard]
> Similarity distance: 0.5821
##### Similarities

- Both questions involve finding the maximum amount of water that can be trapped between vertical lines.
- Both questions require calculating the area formed by the vertical lines and the water.
##### Differences

- Container With Most Water focuses on finding the two vertical lines that can hold the most water, while Trapping Rain Water focuses on finding the total amount of water that can be trapped.
- Container With Most Water has a time complexity of O(n), while Trapping Rain Water has a time complexity of O(n^2).
- Container With Most Water can be solved using a two-pointer approach, while Trapping Rain Water requires a stack or two-pointer approach.
##### New Insights in 42 Trapping Rain Water [Hard]

- Container With Most Water: The maximum amount of water that can be trapped is determined by the shorter vertical line.
- Trapping Rain Water: The amount of water that can be trapped at a specific index is determined by the minimum height of the tallest vertical lines on both sides.

