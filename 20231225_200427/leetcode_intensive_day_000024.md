
# Leetcode Intensive Tutorial Day 24 
> [Difficulty Score: 17]

> [Version: 20231225_200427]

## Courses overview of the day

- 234 Palindrome Linked List [Easy]
  - 143 Reorder List [Medium]
    - 148 Sort List [Medium]
    - 272 Closest Binary Search Tree Value II [Hard]
      - 99 Recover Binary Search Tree [Hard]
    - 24 Swap Nodes in Pairs [Medium]
    - 328 Odd Even Linked List [Medium]

#### Steps by steps

 - [1. From 234 Palindrome Linked List [Easy] to 143 Reorder List [Medium]](#1-from-234-palindrome-linked-list-easy-to-143-reorder-list-medium)

 - [2. From 143 Reorder List [Medium] to 148 Sort List [Medium]](#2-from-143-reorder-list-medium-to-148-sort-list-medium)

 - [3. From 143 Reorder List [Medium] to 272 Closest Binary Search Tree Value II [Hard]](#3-from-143-reorder-list-medium-to-272-closest-binary-search-tree-value-ii-hard)

 - [4. From 272 Closest Binary Search Tree Value II [Hard] to 99 Recover Binary Search Tree [Hard]](#4-from-272-closest-binary-search-tree-value-ii-hard-to-99-recover-binary-search-tree-hard)

 - [5. From 143 Reorder List [Medium] to 24 Swap Nodes in Pairs [Medium]](#5-from-143-reorder-list-medium-to-24-swap-nodes-in-pairs-medium)

 - [6. From 143 Reorder List [Medium] to 328 Odd Even Linked List [Medium]](#6-from-143-reorder-list-medium-to-328-odd-even-linked-list-medium)

#### Summary


- 234 Palindrome Linked List : Check if a linked list is a palindrome by comparing its values with their reverse.
- 24 Swap Nodes in Pairs : Swap every two adjacent nodes in a linked list.
- 99 Recover Binary Search Tree : Recover a binary search tree with two swapped elements without changing its structure.
- 272 Closest Binary Search Tree Value II : Find k values in a binary search tree that are closest to a target value using an inorder traversal and two lists.
- 328 Odd Even Linked List : The essence of the problem is to group all odd nodes together followed by the even nodes in the given linked list in place.
- 143 Reorder List : Reordering a linked list by finding the middle, reversing the second half, and merging the halves
- 148 Sort List : The essence of this problem is to divide the linked list into smaller sublists using merge sort and merge them in sorted order.
> Similarity Diameter of these problems: 0.5603


---
# 1. From 234 Palindrome Linked List [Easy] to 143 Reorder List [Medium]
> Similarity Distance: 0.4497

### >> 234 Palindrome Linked List [Easy]
Given a singly linked list, determine if it is a palindrome.
##### Sample input:
1->2

##### Sample output:
false


##### Questions to ask to clarify requirements:
What is the maximum length of the linked list? Can the linked list be empty?

##### Optimal Python solution:
```python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        values = []
        current = head
        while current:
            values.append(current.val)
            current = current.next
        return values == values[::-1]

```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Traverse the linked list and store the values in a list
2. Check if the list is equal to its reverse
3. Return True if it is a palindrome, False otherwise
Use the == operator to compare two lists for equality.
The space complexity of the optimal solution is O(n), which can be improved.
Avoid using extra space to store the values of the linked list.
    
### >> 143 Reorder List [Medium]
Given a singly linked list L: L0→L1→…→Ln-1→Ln, reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
##### Sample input:
1->2->3->4
##### Sample output:
1->4->2->3

##### Questions to ask to clarify requirements:
Can we modify the input linked list? What should we do if the length of the linked list is odd?

##### Optimal Python solution:
```python
def reorderList(self, head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, curr = None, slow
    while curr:
        curr.next, prev, curr = prev, curr, curr.next
    first, second = head, prev
    while second.next:
        first.next, first = second, first.next
        second.next, second = first, second.next
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Find the middle of the linked list using two pointers
2. Reverse the second half of the linked list
3. Merge the first and second halves of the linked list
Use two pointers to find the middle of the linked list
Reversing the second half of the linked list
Using extra space
    
### >> Comparison: 234 Palindrome Linked List [Easy] *VS* 143 Reorder List [Medium]
> Similarity distance: 0.4497
##### Similarities

- Both questions involve manipulating a linked list.
- Both questions require rearranging the elements of the linked list.
##### Differences

- Question 234 checks if a linked list is a palindrome, while question 143 reorders the elements of the linked list.
- Question 234 requires checking for symmetry in the linked list, while question 143 requires rearranging the elements in a specific order.
- Question 234 has a time complexity of O(n) and space complexity of O(1), while question 143 has a time complexity of O(n) and space complexity of O(1).
##### New Insights in 143 Reorder List [Medium]

- Question 234 introduces the concept of checking for palindromes in a linked list.
- Question 143 introduces the concept of reordering elements in a linked list.


---
# 2. From 143 Reorder List [Medium] to 148 Sort List [Medium]
> Similarity Distance: 0.3534

### >> Reminder: 143 Reorder List [Medium]
Given a singly linked list L: L0→L1→…→Ln-1→Ln, reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
##### Optimal Python solution:
```python
def reorderList(self, head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, curr = None, slow
    while curr:
        curr.next, prev, curr = prev, curr, curr.next
    first, second = head, prev
    while second.next:
        first.next, first = second, first.next
        second.next, second = first, second.next
```
Reordering a linked list by finding the middle, reversing the second half, and merging the halves
    
### >> 148 Sort List [Medium]
Sort a linked list in O(n log n) time using constant space complexity.
##### Sample input:
4->2->1->3
##### Sample output:
1->2->3->4

##### Questions to ask to clarify requirements:
What is the maximum length of the linked list? Can the linked list contain duplicates?

##### Optimal Python solution:
```python
def sortList(self, head: ListNode) -> ListNode:
    if not head or not head.next:
        return head
    slow = head
    fast = head.next
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    mid = slow.next
    slow.next = None
    left = self.sortList(head)
    right = self.sortList(mid)
    return self.merge(left, right)


def merge(self, l1: ListNode, l2: ListNode) -> ListNode:
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
    if l1:
        curr.next = l1
    if l2:
        curr.next = l2
    return dummy.next
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(1)
##### Notes:
1. Use merge sort to divide the linked list into smaller sublists.
2. Merge the sublists in sorted order.
3. Time complexity: O(n log n).
4. Space complexity: O(1).
Implement the merge sort algorithm with linked lists.
The main challenge is to correctly divide the linked list into smaller sublists and merge them in sorted order.
Avoid using sorting algorithms with higher time complexity or additional data structures.
    
### >> Comparison: 143 Reorder List [Medium] *VS* 148 Sort List [Medium]
> Similarity distance: 0.3534
##### Similarities

- Both questions involve manipulating a linked list.
- Both questions have a time complexity of O(n log n).
##### Differences

- 143 Reorder List involves reordering the list in a specific way, while 148 Sort List involves sorting the list in ascending order.
- 143 Reorder List requires rearranging the nodes in the list, while 148 Sort List requires rearranging the values within the nodes.
- 143 Reorder List has a space complexity of O(1), while 148 Sort List has a space complexity of O(log n).
##### New Insights in 148 Sort List [Medium]

- In 143 Reorder List, we can split the list into two halves, reverse the second half, and then merge the two halves alternately to achieve the desired reordering.
- In 148 Sort List, we can use the merge sort algorithm to sort the list in O(n log n) time complexity.


---
# 3. From 143 Reorder List [Medium] to 272 Closest Binary Search Tree Value II [Hard]
> Similarity Distance: 0.4029

### >> Reminder: 143 Reorder List [Medium]
Given a singly linked list L: L0→L1→…→Ln-1→Ln, reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
##### Optimal Python solution:
```python
def reorderList(self, head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, curr = None, slow
    while curr:
        curr.next, prev, curr = prev, curr, curr.next
    first, second = head, prev
    while second.next:
        first.next, first = second, first.next
        second.next, second = first, second.next
```
Reordering a linked list by finding the middle, reversing the second half, and merging the halves
    
### >> 272 Closest Binary Search Tree Value II [Hard]
Given a non-empty binary search tree and a target value, find k values in the BST that are closest to the target.
##### Sample input:

- root = [4,2,5,1,3], target = 3.714286, k = 2
##### Sample output:

- [3,4]

##### Questions to ask to clarify requirements:

- What should be returned if there are less than k values in the BST?
- Can the target value be outside the range of values in the BST?
- What is the expected time complexity of the solution?

##### Optimal Python solution:
```python

- class Solution:
-     def closestKValues(self, root: TreeNode, target: float, k: int) -> List[int]:
-         stack, pred, succ = [], [], []
-         while stack or root:
-             while root:
-                 stack.append(root)
-                 root = root.left
-             root = stack.pop()
-             if root.val <= target:
-                 pred.append(root.val)
-                 if len(pred) > k:
-                     pred.pop(0)
-                 else:
-                     succ.append(root.val)
-                     if len(succ) > k:
-                         succ.pop(0)
-             else:
-                 break
-             root = root.right
-         return pred if target - pred[0] < succ[-1] - target else succ
```
##### Time complexity:
O(n)
##### Space complexity:
O(k)
##### Notes:

- Use a stack to traverse the BST in inorder
- Maintain two lists: one for values less than or equal to the target, and one for values greater than the target
- Keep track of the k closest values by removing the first element if the list size exceeds k

- Use a stack to traverse the BST in inorder
- Use two lists to store values less than or equal to the target and values greater than the target

- Handling an empty BST
- Finding the k closest values

- Using a brute force approach to find all values in the BST
- Using a large amount of additional memory
    
### >> Comparison: 143 Reorder List [Medium] *VS* 272 Closest Binary Search Tree Value II [Hard]
> Similarity distance: 0.4029
##### Similarities

- Both questions involve manipulating a linked list or a binary search tree.
- Both questions require rearranging or reordering the elements in the data structure.
- Both questions have a time complexity of O(n).
##### Differences

- Question 143 involves reordering a linked list by modifying the pointers, while question 272 involves finding the closest values in a binary search tree.
- Question 143 requires rearranging the elements in-place, while question 272 requires finding the values and returning them in a specific order.
- Question 143 has a space complexity of O(1), while question 272 has a space complexity of O(k), where k is the number of closest values to be returned.
##### New Insights in 272 Closest Binary Search Tree Value II [Hard]

- Question 143 teaches us how to manipulate pointers in a linked list to reorder the elements efficiently.
- Question 272 teaches us how to traverse a binary search tree and find the closest values to a given target.


---
# 4. From 272 Closest Binary Search Tree Value II [Hard] to 99 Recover Binary Search Tree [Hard]
> Similarity Distance: 0.4415

### >> Reminder: 272 Closest Binary Search Tree Value II [Hard]
Given a non-empty binary search tree and a target value, find k values in the BST that are closest to the target.
##### Optimal Python solution:
```python

- class Solution:
-     def closestKValues(self, root: TreeNode, target: float, k: int) -> List[int]:
-         stack, pred, succ = [], [], []
-         while stack or root:
-             while root:
-                 stack.append(root)
-                 root = root.left
-             root = stack.pop()
-             if root.val <= target:
-                 pred.append(root.val)
-                 if len(pred) > k:
-                     pred.pop(0)
-                 else:
-                     succ.append(root.val)
-                     if len(succ) > k:
-                         succ.pop(0)
-             else:
-                 break
-             root = root.right
-         return pred if target - pred[0] < succ[-1] - target else succ
```
Find k values in a binary search tree that are closest to a target value using an inorder traversal and two lists.
    
### >> 99 Recover Binary Search Tree [Hard]
Two elements of a binary search tree (BST) are swapped by mistake. Recover the tree without changing its structure.
##### Sample input:

- [1,3,null,null,2]
##### Sample output:

- [3,1,null,null,2]

##### Questions to ask to clarify requirements:

- Can we assume that there are only two elements swapped?
- Can we modify the structure of the tree?
- Can we use extra space?

##### Optimal Python solution:
```python

- class Solution:
-     def recoverTree(self, root: TreeNode) -> None:
-         def inorder(node):
-             if not node:
-                 return
-             inorder(node.left)
-             if self.prev and self.prev.val > node.val:
-                 if not self.first:
-                     self.first = self.prev
-                 self.second = node
-             self.prev = node
-             inorder(node.right)
-         self.prev = self.first = self.second = None
-         inorder(root)
-         self.first.val, self.second.val = self.second.val, self.first.val
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use inorder traversal to find the swapped elements
- Swap the values of the two elements
- Do not change the structure of the tree

- Use a recursive function for inorder traversal
- Keep track of the previous node visited
- Swap the values of the two elements

- Identifying the swapped elements during inorder traversal

- Modifying the structure of the tree
- Using extra space
    
### >> Comparison: 272 Closest Binary Search Tree Value II [Hard] *VS* 99 Recover Binary Search Tree [Hard]
> Similarity distance: 0.4415
##### Similarities

- Both questions are related to binary search trees (BST).
- Both questions are classified as hard difficulty.
##### Differences

- 272 Closest Binary Search Tree Value II focuses on finding the k closest values to a target value in a BST.
- 99 Recover Binary Search Tree focuses on recovering a BST that has two nodes swapped.
##### New Insights in 99 Recover Binary Search Tree [Hard]

- From 272 Closest Binary Search Tree Value II, we can learn how to perform an inorder traversal of a BST and maintain a list of k closest values.
- From 99 Recover Binary Search Tree, we can learn how to identify and swap two incorrectly placed nodes in a BST.


---
# 5. From 143 Reorder List [Medium] to 24 Swap Nodes in Pairs [Medium]
> Similarity Distance: 0.4088

### >> Reminder: 143 Reorder List [Medium]
Given a singly linked list L: L0→L1→…→Ln-1→Ln, reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
##### Optimal Python solution:
```python
def reorderList(self, head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, curr = None, slow
    while curr:
        curr.next, prev, curr = prev, curr, curr.next
    first, second = head, prev
    while second.next:
        first.next, first = second, first.next
        second.next, second = first, second.next
```
Reordering a linked list by finding the middle, reversing the second half, and merging the halves
    
### >> 24 Swap Nodes in Pairs [Medium]
Given a linked list, swap every two adjacent nodes and return its head.
##### Sample input:
[1,2,3,4]
##### Sample output:
[2,1,4,3]

##### Questions to ask to clarify requirements:

- Can the input list be empty?
- Can the input list contain cycles?
- What is the maximum length of the input list?

##### Optimal Python solution:
```python
def swapPairs(self, head: ListNode) -> ListNode:
    dummy = ListNode()
    dummy.next = head
    prev = dummy
    while head and head.next:
        first = head
        second = head.next
        prev.next = second
        first.next = second.next
        second.next = first
        prev = first
        head = first.next
    return dummy.next
```
##### Time complexity:
O(N)
##### Space complexity:
O(1)
##### Notes:

- Use a dummy node to simplify the swapping process
- Iterate through the list and swap every two adjacent nodes

- Use a dummy node to simplify the swapping process.
- Iterate through the list and swap every two adjacent nodes.
- Update the previous node after each swap.

- Handling empty list as input
- Updating the previous node after swapping nodes

- Using recursion to swap nodes
- Using a quadratic time complexity solution
    
### >> Comparison: 143 Reorder List [Medium] *VS* 24 Swap Nodes in Pairs [Medium]
> Similarity distance: 0.4088
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating linked lists.
- Both questions require reordering or swapping elements in the linked list.
##### Differences

- In 'Reorder List', the linked list needs to be reordered in a specific way.
- In 'Swap Nodes in Pairs', adjacent nodes need to be swapped in pairs.
- The implementation details for reordering and swapping are different in each question.
##### New Insights in 24 Swap Nodes in Pairs [Medium]

- In 'Reorder List', we can use a combination of reversing and merging techniques to reorder the linked list.
- In 'Swap Nodes in Pairs', we can use a recursive approach to swap the nodes in pairs.


---
# 6. From 143 Reorder List [Medium] to 328 Odd Even Linked List [Medium]
> Similarity Distance: 0.4679

### >> Reminder: 143 Reorder List [Medium]
Given a singly linked list L: L0→L1→…→Ln-1→Ln, reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
##### Optimal Python solution:
```python
def reorderList(self, head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, curr = None, slow
    while curr:
        curr.next, prev, curr = prev, curr, curr.next
    first, second = head, prev
    while second.next:
        first.next, first = second, first.next
        second.next, second = first, second.next
```
Reordering a linked list by finding the middle, reversing the second half, and merging the halves
    
### >> 328 Odd Even Linked List [Medium]
Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.
You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.
##### Sample input:
1->2->3->4->5
##### Sample output:
1->3->5->2->4

##### Questions to ask to clarify requirements:
Can the linked list be empty? Can the linked list contain duplicate values?

##### Optimal Python solution:
```python
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head
        odd = head
        even = head.next
        even_head = even
        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = even_head
        return head
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use two pointers to track the odd and even nodes.
2. Use a separate variable to track the head of the even nodes.
3. Update the next pointers of the odd and even nodes.
1. Use two pointers to track the odd and even nodes.
2. Use a separate variable to track the head of the even nodes.
3. Update the next pointers of the odd and even nodes.
The solution should be done in place and should have O(1) space complexity.
Avoid using extra space to store the odd and even nodes separately.
    
### >> Comparison: 143 Reorder List [Medium] *VS* 328 Odd Even Linked List [Medium]
> Similarity distance: 0.4679
##### Similarities

- Both questions involve manipulating a linked list.
- Both questions require rearranging the elements of the linked list.
##### Differences

- 143 Reorder List reorders the list in a specific pattern, while 328 Odd Even Linked List separates odd and even nodes.
- 143 Reorder List modifies the original list, while 328 Odd Even Linked List creates a new list.
- 143 Reorder List has a time complexity of O(n), while 328 Odd Even Linked List has a time complexity of O(n/2).
##### New Insights in 328 Odd Even Linked List [Medium]

- In 143 Reorder List, we can use a two-pointer approach to find the middle of the list.
- In 328 Odd Even Linked List, we can use two separate pointers to keep track of odd and even nodes.

