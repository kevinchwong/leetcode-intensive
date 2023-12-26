
# Leetcode Intensive Tutorial Day 37 
> [Difficulty Score: 20]

> [Version: 20231225_200427]

## Courses overview of the day

- 206 Reverse Linked List [Easy]
  - 61 Rotate List [Medium]
    - 86 Partition List [Medium]
      - 2 Add Two Numbers [Medium]
      - 138 Copy List with Random Pointer [Medium]
    - 203 Remove Linked List Elements [Easy]
    - 92 Reverse Linked List II [Medium]
      - 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]
      - 382 Linked List Random Node [Medium]
      - 80 Remove Duplicates from Sorted Array II [Medium]
  - 147 Insertion Sort List [Medium]

#### Steps by steps

 - [1. From 206 Reverse Linked List [Easy] to 61 Rotate List [Medium]](#1-from-206-reverse-linked-list-easy-to-61-rotate-list-medium)

 - [2. From 61 Rotate List [Medium] to 86 Partition List [Medium]](#2-from-61-rotate-list-medium-to-86-partition-list-medium)

 - [3. From 86 Partition List [Medium] to 2 Add Two Numbers [Medium]](#3-from-86-partition-list-medium-to-2-add-two-numbers-medium)

 - [4. From 86 Partition List [Medium] to 138 Copy List with Random Pointer [Medium]](#4-from-86-partition-list-medium-to-138-copy-list-with-random-pointer-medium)

 - [5. From 61 Rotate List [Medium] to 203 Remove Linked List Elements [Easy]](#5-from-61-rotate-list-medium-to-203-remove-linked-list-elements-easy)

 - [6. From 61 Rotate List [Medium] to 92 Reverse Linked List II [Medium]](#6-from-61-rotate-list-medium-to-92-reverse-linked-list-ii-medium)

 - [7. From 92 Reverse Linked List II [Medium] to 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]](#7-from-92-reverse-linked-list-ii-medium-to-426-convert-binary-search-tree-to-sorted-doubly-linked-list-medium)

 - [8. From 92 Reverse Linked List II [Medium] to 382 Linked List Random Node [Medium]](#8-from-92-reverse-linked-list-ii-medium-to-382-linked-list-random-node-medium)

 - [9. From 92 Reverse Linked List II [Medium] to 80 Remove Duplicates from Sorted Array II [Medium]](#9-from-92-reverse-linked-list-ii-medium-to-80-remove-duplicates-from-sorted-array-ii-medium)

 - [10. From 206 Reverse Linked List [Easy] to 147 Insertion Sort List [Medium]](#10-from-206-reverse-linked-list-easy-to-147-insertion-sort-list-medium)

#### Summary


- 147 Insertion Sort List : The essence of this problem is to correctly insert each node in the sorted portion of the linked list.
- 206 Reverse Linked List : The essence of this problem is to reverse the direction of the pointers in a linked list.
- 138 Copy List with Random Pointer : Creating a deep copy of a linked list using a hash table.
- 92 Reverse Linked List II : The essence of this problem is to reverse a sublist of a linked list in one pass.
- 80 Remove Duplicates from Sorted Array II : The problem requires removing duplicates from a sorted array in-place with at most two duplicates allowed.
- 61 Rotate List : The essence of this problem is to find the new head of the rotated linked list by moving k steps from the end.
- 426 Convert Binary Search Tree to Sorted Doubly Linked List : The essence of the problem is to convert a Binary Search Tree to a sorted doubly linked list in-place using inorder traversal and updating the links between nodes.
- 2 Add Two Numbers : Adding two numbers represented as linked lists.
- 86 Partition List : The essence of this problem is to partition a linked list such that all nodes with values less than x come before nodes with values greater than or equal to x, while preserving the original relative order of the nodes.
- 203 Remove Linked List Elements : Removing nodes with a specific value from a linked list.
- 382 Linked List Random Node : Select a random node from a linked list with each node having the same probability of being chosen.
> Similarity Diameter of these problems: 0.7887


---
# 1. From 206 Reverse Linked List [Easy] to 61 Rotate List [Medium]
> Similarity Distance: 0.5217

### >> 206 Reverse Linked List [Easy]
Reverse a singly linked list.
##### Sample input:
1->2->3->4->5
##### Sample output:
5->4->3->2->1

##### Questions to ask to clarify requirements:
Can we assume that the linked list is non-empty?

##### Optimal Python solution:
```python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        prev = None
        curr = head
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        return prev
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Initialize two pointers: prev and curr.
2. Iterate through the linked list, updating the next pointer of each node to point to the previous node.
3. Return the new head of the reversed linked list.
Use three pointers to keep track of the previous, current, and next nodes.
None
None
    
### >> 61 Rotate List [Medium]
Given the head of a linked list, rotate the list to the right by k places.
##### Sample input:
head = [1,2,3,4,5], k = 2
##### Sample output:
[4,5,1,2,3]

##### Questions to ask to clarify requirements:
1. Can the linked list be empty? 2. Can k be greater than the length of the linked list?

##### Optimal Python solution:
```python
def rotateRight(head, k):
    if not head or not head.next or k == 0:
        return head
    n = 1
    curr = head
    while curr.next:
        curr = curr.next
        n += 1
    curr.next = head
    k = k % n
    for _ in range(n - k):
        curr = curr.next
    new_head = curr.next
    curr.next = None
    return new_head
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Find the length of the linked list. 2. Connect the last node to the head to form a circular linked list. 3. Find the new head by moving k steps from the end. 4. Disconnect the new head from the rest of the linked list.
1. Use two pointers to solve linked list problems efficiently. 2. Consider edge cases when dealing with linked lists.
1. Handling the case when k is greater than the length of the linked list. 2. Handling the case when the linked list is empty.
1. Using extra space. 2. Using recursion.
    
### >> Comparison: 206 Reverse Linked List [Easy] *VS* 61 Rotate List [Medium]
> Similarity distance: 0.5217
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions require reversing or rotating the linked list.
- Both questions have a time complexity of O(n).
##### Differences

- 206 Reverse Linked List is an easy level question, while 61 Rotate List is a medium level question.
- 206 Reverse Linked List requires reversing the entire linked list, while 61 Rotate List requires rotating the list by a given number of places.
- 206 Reverse Linked List can be solved using iterative or recursive approaches, while 61 Rotate List requires finding the new head and tail of the rotated list.
##### New Insights in 61 Rotate List [Medium]

- 206 Reverse Linked List: Reversing a linked list can be done iteratively by maintaining three pointers: previous, current, and next.
- 206 Reverse Linked List: Reversing a linked list can also be done recursively by using a helper function that returns the new head of the reversed list.
- 61 Rotate List: To rotate a linked list, we need to find the length of the list and calculate the actual number of rotations needed.
- 61 Rotate List: We can optimize the solution by using the concept of cyclic linked lists.


---
# 2. From 61 Rotate List [Medium] to 86 Partition List [Medium]
> Similarity Distance: 0.4290

### >> Reminder: 61 Rotate List [Medium]
Given the head of a linked list, rotate the list to the right by k places.
##### Optimal Python solution:
```python
def rotateRight(head, k):
    if not head or not head.next or k == 0:
        return head
    n = 1
    curr = head
    while curr.next:
        curr = curr.next
        n += 1
    curr.next = head
    k = k % n
    for _ in range(n - k):
        curr = curr.next
    new_head = curr.next
    curr.next = None
    return new_head
```
The essence of this problem is to find the new head of the rotated linked list by moving k steps from the end.
    
### >> 86 Partition List [Medium]
Given the head of a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x. You should preserve the original relative order of the nodes in each of the two partitions.
##### Sample input:

- head = [1,4,3,2,5,2], x = 3
##### Sample output:

- [1,2,2,4,3,5]

##### Questions to ask to clarify requirements:

- Can the linked list be empty?
- Can the linked list contain duplicate values?
- Should the partition be done in-place or can a new linked list be created?

##### Optimal Python solution:
```python

- class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def partition(head, x):
    before_head = ListNode(0)
    before = before_head
    after_head = ListNode(0)
    after = after_head
    while head:
        if head.val < x:
            before.next = head
            before = before.next
        else:
            after.next = head
            after = after.next
        head = head.next
    after.next = None
    before.next = after_head.next
    return before_head.next

head = ListNode(1)
head.next = ListNode(4)
head.next.next = ListNode(3)
head.next.next.next = ListNode(2)
head.next.next.next.next = ListNode(5)
head.next.next.next.next.next = ListNode(2)
x = 3
result = partition(head, x)
while result:
    print(result.val)
    result = result.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Create two new linked lists to store the nodes with values less than x and greater than or equal to x
- Traverse the original linked list and append each node to the appropriate new linked list
- Join the two new linked lists together

- Create two new linked lists to store the nodes with values less than x and greater than or equal to x.
- Traverse the original linked list and append each node to the appropriate new linked list.
- Join the two new linked lists together.
- Handle edge cases and optimize the solution for long linked lists.

- Joining the two new linked lists together

- Creating a new linked list for each partition
- Sorting the linked list
    
### >> Comparison: 61 Rotate List [Medium] *VS* 86 Partition List [Medium]
> Similarity distance: 0.4290
##### Similarities

- Both questions are related to linked lists.
- Both questions have a medium difficulty level.
##### Differences

- Rotate List involves rotating a linked list by a given number of positions.
- Partition List involves partitioning a linked list based on a given value.
##### New Insights in 86 Partition List [Medium]

- Rotate List: The rotation can be done in-place by manipulating the pointers.
- Partition List: The order of the elements after partitioning does not matter.


---
# 3. From 86 Partition List [Medium] to 2 Add Two Numbers [Medium]
> Similarity Distance: 0.4845

### >> Reminder: 86 Partition List [Medium]
Given the head of a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x. You should preserve the original relative order of the nodes in each of the two partitions.
##### Optimal Python solution:
```python

- class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def partition(head, x):
    before_head = ListNode(0)
    before = before_head
    after_head = ListNode(0)
    after = after_head
    while head:
        if head.val < x:
            before.next = head
            before = before.next
        else:
            after.next = head
            after = after.next
        head = head.next
    after.next = None
    before.next = after_head.next
    return before_head.next

head = ListNode(1)
head.next = ListNode(4)
head.next.next = ListNode(3)
head.next.next.next = ListNode(2)
head.next.next.next.next = ListNode(5)
head.next.next.next.next.next = ListNode(2)
x = 3
result = partition(head, x)
while result:
    print(result.val)
    result = result.next
```
The essence of this problem is to partition a linked list such that all nodes with values less than x come before nodes with values greater than or equal to x, while preserving the original relative order of the nodes.
    
### >> 2 Add Two Numbers [Medium]
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
##### Sample input:
[2,4,3]
[5,6,4]
##### Sample output:
[7,0,8]

##### Questions to ask to clarify requirements:
Can the input linked lists have different lengths?

##### Optimal Python solution:
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def addTwoNumbers(l1, l2):
    dummy = ListNode()
    curr = dummy
    carry = 0
    while l1 or l2 or carry:
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0
        carry, digit = divmod(val1 + val2 + carry, 10)
        curr.next = ListNode(digit)
        curr = curr.next
        l1 = l1.next if l1 else None
        l2 = l2.next if l2 else None
    return dummy.next
```
##### Time complexity:
O(max(m, n))
##### Space complexity:
O(max(m, n))
##### Notes:

- Create a dummy node to store the head of the result linked list
- Iterate through the input linked lists and add the corresponding digits
- Handle carry and create new nodes for the result linked list
Use a dummy node to simplify the creation of the result linked list.
Handling the case when the sum has an additional digit
Converting the linked lists to integers and then back to linked lists
    
### >> Comparison: 86 Partition List [Medium] *VS* 2 Add Two Numbers [Medium]
> Similarity distance: 0.4845
##### Similarities

- Both questions are categorized as Medium difficulty level.
- Both questions involve linked lists as the main data structure.
- Both questions require manipulating the linked list nodes.
##### Differences

- 86 Partition List: In this question, we need to partition the given linked list such that all nodes with values less than x come before nodes with values greater than or equal to x.
- 2 Add Two Numbers: In this question, we need to add two numbers represented by linked lists, where each node contains a single digit.
##### New Insights in 2 Add Two Numbers [Medium]

- 86 Partition List: The insight we can learn from this question is how to rearrange the nodes of a linked list based on a given condition.
- 2 Add Two Numbers: The insight we can learn from this question is how to perform addition of two numbers represented by linked lists.


---
# 4. From 86 Partition List [Medium] to 138 Copy List with Random Pointer [Medium]
> Similarity Distance: 0.5468

### >> Reminder: 86 Partition List [Medium]
Given the head of a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x. You should preserve the original relative order of the nodes in each of the two partitions.
##### Optimal Python solution:
```python

- class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def partition(head, x):
    before_head = ListNode(0)
    before = before_head
    after_head = ListNode(0)
    after = after_head
    while head:
        if head.val < x:
            before.next = head
            before = before.next
        else:
            after.next = head
            after = after.next
        head = head.next
    after.next = None
    before.next = after_head.next
    return before_head.next

head = ListNode(1)
head.next = ListNode(4)
head.next.next = ListNode(3)
head.next.next.next = ListNode(2)
head.next.next.next.next = ListNode(5)
head.next.next.next.next.next = ListNode(2)
x = 3
result = partition(head, x)
while result:
    print(result.val)
    result = result.next
```
The essence of this problem is to partition a linked list such that all nodes with values less than x come before nodes with values greater than or equal to x, while preserving the original relative order of the nodes.
    
### >> 138 Copy List with Random Pointer [Medium]
A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null. Return a deep copy of the list.
##### Sample input:
[[7,null],[13,0],[11,4],[10,2],[1,0]]
##### Sample output:
[[7,null],[13,0],[11,4],[10,2],[1,0]]

##### Questions to ask to clarify requirements:
Can the linked list contain cycles? Can the random pointer point to any node in the list, including itself?

##### Optimal Python solution:
```python
class Solution:
    def copyRandomList(self, head: 'Node') -> 'Node':
        if not head:
            return None
        node_map = {}
        curr = head
        while curr:
            node_map[curr] = Node(curr.val)
            curr = curr.next
        curr = head
        while curr:
            node_map[curr].next = node_map.get(curr.next)
            node_map[curr].random = node_map.get(curr.random)
            curr = curr.next
        return node_map[head]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Create a hash table to store the mapping between original nodes and copied nodes
- Iterate through the original linked list and create a deep copy of each node
- Update the next and random pointers of the copied nodes using the hash table

- Understand how to create a deep copy of a linked list
- Be familiar with hash table usage

- Handling the random pointer
- Creating a deep copy of the linked list

- Modifying the original linked list
- Using recursion
    
### >> Comparison: 86 Partition List [Medium] *VS* 138 Copy List with Random Pointer [Medium]
> Similarity distance: 0.5468
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating linked lists.
- Both questions require creating new linked lists based on certain conditions.
##### Differences

- Question 86 involves partitioning a linked list based on a given value, while question 138 involves creating a deep copy of a linked list with random pointers.
- Question 86 requires rearranging the elements of the linked list, while question 138 requires creating a new linked list with the same values and random pointers.
- Question 86 has a linear time complexity, while question 138 has a linear time complexity with additional space complexity.
##### New Insights in 138 Copy List with Random Pointer [Medium]

- Question 86: Partitioning a linked list can be done by creating two separate linked lists for elements smaller and greater than a given value, and then combining them.
- Question 138: Creating a deep copy of a linked list with random pointers can be done by iterating through the original list and creating a new node for each node in the original list, while maintaining the random pointers.


---
# 5. From 61 Rotate List [Medium] to 203 Remove Linked List Elements [Easy]
> Similarity Distance: 0.4874

### >> Reminder: 61 Rotate List [Medium]
Given the head of a linked list, rotate the list to the right by k places.
##### Optimal Python solution:
```python
def rotateRight(head, k):
    if not head or not head.next or k == 0:
        return head
    n = 1
    curr = head
    while curr.next:
        curr = curr.next
        n += 1
    curr.next = head
    k = k % n
    for _ in range(n - k):
        curr = curr.next
    new_head = curr.next
    curr.next = None
    return new_head
```
The essence of this problem is to find the new head of the rotated linked list by moving k steps from the end.
    
### >> 203 Remove Linked List Elements [Easy]
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.
##### Sample input:
head = [1,2,6,3,4,5,6], val = 6
##### Sample output:
[1,2,3,4,5]

##### Questions to ask to clarify requirements:
Are the values in the linked list unique?

##### Optimal Python solution:
```python
def removeElements(head, val):
    dummy = ListNode(0)
    dummy.next = head
    curr = dummy
    while curr.next:
        if curr.next.val == val:
            curr.next = curr.next.next
        else:
            curr = curr.next
    return dummy.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a dummy node to simplify the removal process.
2. Iterate through the linked list and remove nodes with the given value.
3. Return the new head of the modified linked list.
1. Use a dummy node to handle the removal of the first node.
2. Update the current pointer after removal.
1. Handling the removal of the first node.
2. Updating the current pointer after removal.
1. Using recursion for removal.
2. Modifying the original linked list directly.
    
### >> Comparison: 61 Rotate List [Medium] *VS* 203 Remove Linked List Elements [Easy]
> Similarity distance: 0.4874
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions require traversing the linked list.
- Both questions involve removing elements from the linked list.
##### Differences

- Rotate List involves rotating the linked list by a given number of steps.
- Remove Linked List Elements involves removing all occurrences of a given value from the linked list.
##### New Insights in 203 Remove Linked List Elements [Easy]

- Rotate List: The rotation can be done in a single pass by finding the length of the linked list and adjusting the rotation steps.
- Remove Linked List Elements: To remove elements, we can use a dummy node to handle the edge case of removing the head node.


---
# 6. From 61 Rotate List [Medium] to 92 Reverse Linked List II [Medium]
> Similarity Distance: 0.5480

### >> Reminder: 61 Rotate List [Medium]
Given the head of a linked list, rotate the list to the right by k places.
##### Optimal Python solution:
```python
def rotateRight(head, k):
    if not head or not head.next or k == 0:
        return head
    n = 1
    curr = head
    while curr.next:
        curr = curr.next
        n += 1
    curr.next = head
    k = k % n
    for _ in range(n - k):
        curr = curr.next
    new_head = curr.next
    curr.next = None
    return new_head
```
The essence of this problem is to find the new head of the rotated linked list by moving k steps from the end.
    
### >> 92 Reverse Linked List II [Medium]
Reverse a linked list from position m to n. Do it in one-pass.
##### Sample input:
1->2->3->4->5, m = 2, n = 4
##### Sample output:
1->4->3->2->5

##### Questions to ask to clarify requirements:
Can the linked list be empty? What should be returned if m or n is out of range?

##### Optimal Python solution:
```python
def reverseBetween(head, m, n):
    if not head or not head.next or m == n:
        return head
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    for _ in range(m - 1):
        prev = prev.next
    curr = prev.next
    for _ in range(n - m):
        temp = curr.next
        curr.next = temp.next
        temp.next = prev.next
        prev.next = temp
    return dummy.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a dummy node to simplify the reversal process.
2. Traverse the linked list to the (m-1)th node.
3. Reverse the sublist from the mth to the nth node.
4. Connect the reversed sublist back to the original linked list.
1. Handle edge cases such as an empty linked list or m and n values that are out of range.
2. Use a dummy node to simplify the reversal process.
3. Optimize the time complexity of the solution by using a one-pass approach.
1. Keeping track of the previous node while reversing the sublist.
2. Handling edge cases such as an empty linked list or m and n values that are out of range.
1. Using recursion to reverse the sublist.
2. Reversing the entire linked list instead of the sublist.
    
### >> Comparison: 61 Rotate List [Medium] *VS* 92 Reverse Linked List II [Medium]
> Similarity distance: 0.5480
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions have a medium difficulty level.
##### Differences

- Rotate List involves rotating a linked list by a given number of positions, while Reverse Linked List II involves reversing a portion of a linked list.
- Rotate List requires finding the new head of the rotated list, while Reverse Linked List II requires reversing a specific portion of the list.
- Rotate List has a time complexity of O(n), while Reverse Linked List II has a time complexity of O(n).
##### New Insights in 92 Reverse Linked List II [Medium]

- Rotate List: The rotation can be performed in a single pass by finding the length of the list and using modular arithmetic.
- Reverse Linked List II: The portion of the list to be reversed can be identified using the given indices.


---
# 7. From 92 Reverse Linked List II [Medium] to 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]
> Similarity Distance: 0.4959

### >> Reminder: 92 Reverse Linked List II [Medium]
Reverse a linked list from position m to n. Do it in one-pass.
##### Optimal Python solution:
```python
def reverseBetween(head, m, n):
    if not head or not head.next or m == n:
        return head
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    for _ in range(m - 1):
        prev = prev.next
    curr = prev.next
    for _ in range(n - m):
        temp = curr.next
        curr.next = temp.next
        temp.next = prev.next
        prev.next = temp
    return dummy.next
```
The essence of this problem is to reverse a sublist of a linked list in one pass.
    
### >> 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]
Convert a Binary Search Tree to a sorted circular doubly-linked list in-place.
##### Sample input:

- 4,2,5,1,3
##### Sample output:

- 1,2,3,4,5

##### Questions to ask to clarify requirements:

- Can the input tree be empty?
- Can the input tree have duplicate values?
- What should be the order of the doubly linked list?

##### Optimal Python solution:
```python

- class Solution:
-     def treeToDoublyList(self, root: 'Node') -> 'Node':
-         if not root:
-             return None
-         def inorder(node):
-             nonlocal first, last
-             if node:
-                 inorder(node.left)
-                 if last:
-                     last.right = node
-                     node.left = last
-                 else:
-                     first = node
-                 last = node
-                 inorder(node.right)
-         first, last = None, None
-         inorder(root)
-         last.right = first
-         first.left = last
-         return first
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:

- Use inorder traversal to visit the nodes of the BST in ascending order
- Update the links between nodes to create the doubly linked list
- Handle the first and last nodes separately

- Use inorder traversal to visit the nodes of the BST in ascending order.
- Update the links between nodes to create the doubly linked list.

- Updating the links between nodes to create the doubly linked list
- Handling the first and last nodes separately

- Using a pre-order or post-order traversal instead of an inorder traversal
- Using additional data structures to store the nodes
    
### >> Comparison: 92 Reverse Linked List II [Medium] *VS* 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]
> Similarity distance: 0.4959
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve manipulating linked lists.
- Both questions require reversing a portion of the linked list.
##### Differences

- Question 92 involves reversing a portion of a linked list, while question 426 involves converting a binary search tree to a sorted doubly linked list.
- Question 92 requires specifying the start and end positions for the reversal, while question 426 does not have such requirements.
- Question 92 operates on a singly linked list, while question 426 operates on a binary search tree.
- Question 92 has a linear time complexity, while question 426 has a time complexity of O(n) where n is the number of nodes in the binary search tree.
##### New Insights in 426 Convert Binary Search Tree to Sorted Doubly Linked List [Medium]

- Question 92 teaches us how to reverse a portion of a linked list in a given range.
- Question 426 teaches us how to convert a binary search tree to a sorted doubly linked list using in-order traversal.


---
# 8. From 92 Reverse Linked List II [Medium] to 382 Linked List Random Node [Medium]
> Similarity Distance: 0.5950

### >> Reminder: 92 Reverse Linked List II [Medium]
Reverse a linked list from position m to n. Do it in one-pass.
##### Optimal Python solution:
```python
def reverseBetween(head, m, n):
    if not head or not head.next or m == n:
        return head
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    for _ in range(m - 1):
        prev = prev.next
    curr = prev.next
    for _ in range(n - m):
        temp = curr.next
        curr.next = temp.next
        temp.next = prev.next
        prev.next = temp
    return dummy.next
```
The essence of this problem is to reverse a sublist of a linked list in one pass.
    
### >> 382 Linked List Random Node [Medium]
Given a singly linked list, return a random node's value from the linked list. Each node must have the same probability of being chosen.
##### Sample input:

- ["LinkedListRandomNode","getRandom"]
- [[[1,2,3]],[]]
##### Sample output:

- [null,1]

##### Questions to ask to clarify requirements:

- Can the linked list be empty?
- Can the linked list contain duplicates?

##### Optimal Python solution:
```python

- class Solution:
-     def __init__(self, head: ListNode):
-         self.head = head
-     def getRandom(self) -> int:
-         count = 0
-         result = 0
-         curr = self.head
-         while curr:
-             count += 1
-             if random.randint(1, count) == count:
-                 result = curr.val
-             curr = curr.next
-         return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use reservoir sampling
- Iterate through the linked list and update the result with probability 1/count at each node

- Use random.randint(1, count) to update the result with probability 1/count
- Iterate through the linked list and update the result at each node

- Updating the result with probability 1/count

- Using additional data structures to store the linked list
    
### >> Comparison: 92 Reverse Linked List II [Medium] *VS* 382 Linked List Random Node [Medium]
> Similarity distance: 0.5950
##### Similarities

- Both questions are related to linked lists.
- Both questions have a medium difficulty level.
##### Differences

- Question 92 involves reversing a linked list from position m to n, while question 382 involves randomly selecting a node from a linked list.
- Question 92 requires modifying the linked list, while question 382 only requires reading from the linked list.
- Question 92 has a specific range (m to n) for reversing the linked list, while question 382 randomly selects any node from the linked list.
##### New Insights in 382 Linked List Random Node [Medium]

- Question 92 teaches us how to reverse a linked list within a given range.
- Question 382 introduces the concept of randomly selecting a node from a linked list.


---
# 9. From 92 Reverse Linked List II [Medium] to 80 Remove Duplicates from Sorted Array II [Medium]
> Similarity Distance: 0.6099

### >> Reminder: 92 Reverse Linked List II [Medium]
Reverse a linked list from position m to n. Do it in one-pass.
##### Optimal Python solution:
```python
def reverseBetween(head, m, n):
    if not head or not head.next or m == n:
        return head
    dummy = ListNode(0)
    dummy.next = head
    prev = dummy
    for _ in range(m - 1):
        prev = prev.next
    curr = prev.next
    for _ in range(n - m):
        temp = curr.next
        curr.next = temp.next
        temp.next = prev.next
        prev.next = temp
    return dummy.next
```
The essence of this problem is to reverse a sublist of a linked list in one pass.
    
### >> 80 Remove Duplicates from Sorted Array II [Medium]
Given a sorted array nums, remove the duplicates in-place such that duplicates appeared at most twice and return the new length. Do not allocate extra space for another array; you must do this by modifying the input array in-place with O(1) extra memory.
##### Sample input:

- [1,1,1,2,2,3]
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can the input array be empty?
- Can the input array contain negative numbers?
- What is the maximum size of the input array?

##### Optimal Python solution:
```python

- class Solution:
-     def removeDuplicates(self, nums: List[int]) -> int:
-         if len(nums) <= 2:
-             return len(nums)
-         i = 2
-         for j in range(2, len(nums)):
-             if nums[j] != nums[i - 2]:
-                 nums[i] = nums[j]
-                 i += 1
-         return i
```
##### Time complexity:
O(N)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to track the current and next valid positions
- Compare the current element with the element two positions before
- Move the elements to the next valid positions

- Use two pointers to track the current and next valid positions.
- Compare the current element with the element two positions before to check if it is a duplicate.
- Move the elements to the next valid positions.
- Handle the case when the input array is empty by adding a check at the beginning of the function.
- Optimize the solution by using a sliding window approach to reduce the number of element movements.

- Updating the array in-place
- Handling the case when the input array is empty

- Using extra space
- Sorting the array
    
### >> Comparison: 92 Reverse Linked List II [Medium] *VS* 80 Remove Duplicates from Sorted Array II [Medium]
> Similarity distance: 0.6099
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating linked lists or arrays.
- Both questions require modifying the input data structure in-place.
- Both questions have a time complexity of O(n).
##### Differences

- Question 92 involves reversing a linked list between two given positions.
- Question 80 involves removing duplicates from a sorted array, allowing at most two duplicates to remain.
- Question 92 requires traversing the linked list twice, while question 80 only requires a single pass through the array.
- Question 92 uses a dummy node to simplify the reversal process, while question 80 uses two pointers to track the unique elements.
##### New Insights in 80 Remove Duplicates from Sorted Array II [Medium]

- Question 92 teaches us how to reverse a linked list between two given positions.
- Question 80 teaches us how to remove duplicates from a sorted array, allowing at most two duplicates to remain.
- Question 92 introduces the concept of a dummy node to simplify linked list manipulation.
- Question 80 demonstrates the use of two pointers to track unique elements in an array.


---
# 10. From 206 Reverse Linked List [Easy] to 147 Insertion Sort List [Medium]
> Similarity Distance: 0.5221

### >> Reminder: 206 Reverse Linked List [Easy]
Reverse a singly linked list.
##### Optimal Python solution:
```python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        prev = None
        curr = head
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        return prev
```
The essence of this problem is to reverse the direction of the pointers in a linked list.
    
### >> 147 Insertion Sort List [Medium]
Sort a linked list using insertion sort.
##### Sample input:
4->2->1->3
##### Sample output:
1->2->3->4

##### Questions to ask to clarify requirements:
What is the maximum length of the linked list? Can the linked list contain duplicates?

##### Optimal Python solution:
```python
def insertionSortList(self, head: ListNode) -> ListNode:
    dummy = ListNode(0)
    curr = head
    while curr:
        prev = dummy
        while prev.next and prev.next.val < curr.val:
            prev = prev.next
        next_node = curr.next
        curr.next = prev.next
        prev.next = curr
        curr = next_node
    return dummy.next
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(1)
##### Notes:
1. Use a dummy node to simplify the insertion process.
2. Iterate through the linked list and insert each node in the correct position.
3. Time complexity: O(n^2) in the worst case.
4. Space complexity: O(1).
Use a dummy node to simplify the insertion process.
The main challenge is to correctly insert each node in the sorted portion of the linked list.
Avoid using additional data structures or sorting algorithms with higher time complexity.
    
### >> Comparison: 206 Reverse Linked List [Easy] *VS* 147 Insertion Sort List [Medium]
> Similarity distance: 0.5221
##### Similarities

- Both questions involve manipulating linked lists.
- Both questions require reversing the order of elements in a linked list.
##### Differences

- 206 Reverse Linked List is an easy level question, while 147 Insertion Sort List is a medium level question.
- 206 Reverse Linked List requires reversing the entire linked list, while 147 Insertion Sort List requires sorting the linked list in ascending order using the insertion sort algorithm.
- 206 Reverse Linked List can be solved using iterative or recursive approaches, while 147 Insertion Sort List can only be solved using the insertion sort algorithm.
- 206 Reverse Linked List has a time complexity of O(n), while 147 Insertion Sort List has a time complexity of O(n^2).
##### New Insights in 147 Insertion Sort List [Medium]

- 206 Reverse Linked List: Reversing a linked list can be done by changing the next pointers of each node to point to the previous node.
- 147 Insertion Sort List: Insertion sort is an efficient algorithm for sorting small linked lists.

