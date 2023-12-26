
# Leetcode Intensive Tutorial Day 14 
> [Difficulty Score: 14]

> [Version: 20231226_040350]

> [Including this day, you had studied : 104 leetcode problems]


## Courses overview of the day

- 35 Search Insert Position [Easy]
  - 374 Guess Number Higher or Lower [Easy]
    - 103 Binary Tree Zigzag Level Order Traversal [Medium]
      - 107 Binary Tree Level Order Traversal II [Medium]
        - 429 N-ary Tree Level Order Traversal [Medium]
        - 430 Flatten a Multilevel Doubly Linked List [Medium]
    - 456 132 Pattern [Medium]
  - 208 Implement Trie (Prefix Tree) [Medium]

#### Step by step

 - [1. From 35 Search Insert Position [Easy] to 374 Guess Number Higher or Lower [Easy]](#1-from-35-search-insert-position-easy-to-374-guess-number-higher-or-lower-easy))

 - [2. From 374 Guess Number Higher or Lower [Easy] to 103 Binary Tree Zigzag Level Order Traversal [Medium]](#2-from-374-guess-number-higher-or-lower-easy-to-103-binary-tree-zigzag-level-order-traversal-medium))

 - [3. From 103 Binary Tree Zigzag Level Order Traversal [Medium] to 107 Binary Tree Level Order Traversal II [Medium]](#3-from-103-binary-tree-zigzag-level-order-traversal-medium-to-107-binary-tree-level-order-traversal-ii-medium))

 - [4. From 107 Binary Tree Level Order Traversal II [Medium] to 429 N-ary Tree Level Order Traversal [Medium]](#4-from-107-binary-tree-level-order-traversal-ii-medium-to-429-n-ary-tree-level-order-traversal-medium))

 - [5. From 107 Binary Tree Level Order Traversal II [Medium] to 430 Flatten a Multilevel Doubly Linked List [Medium]](#5-from-107-binary-tree-level-order-traversal-ii-medium-to-430-flatten-a-multilevel-doubly-linked-list-medium))

 - [6. From 374 Guess Number Higher or Lower [Easy] to 456 132 Pattern [Medium]](#6-from-374-guess-number-higher-or-lower-easy-to-456-132-pattern-medium))

 - [7. From 35 Search Insert Position [Easy] to 208 Implement Trie (Prefix Tree) [Medium]](#7-from-35-search-insert-position-easy-to-208-implement-trie-prefix-tree-medium))

    

#### Summary


- 456 132 Pattern : The essence of this problem is to find a 132 pattern in an array by using a stack to keep track of the potential pattern.
- 430 Flatten a Multilevel Doubly Linked List : Perform depth-first search on a multilevel doubly linked list and flatten it.
- 35 Search Insert Position : Binary search to find target or insertion position in a sorted array.
- 429 N-ary Tree Level Order Traversal : Perform breadth-first search on an n-ary tree and return the level order traversal.
- 107 Binary Tree Level Order Traversal II : Perform a breadth-first search on a binary tree and return the level order traversal from bottom to top.
- 208 Implement Trie (Prefix Tree) : The essence of this problem is to efficiently store and search for strings using a trie data structure.
- 103 Binary Tree Zigzag Level Order Traversal : Performing breadth-first search on a binary tree and reversing level values if necessary.
- 374 Guess Number Higher or Lower : Guess the number picked by the game using binary search.
> Similarity Diameter of these problems: 0.5798


---
# 1. From 35 Search Insert Position [Easy] to 374 Guess Number Higher or Lower [Easy]
> Similarity Distance: 0.3996

### >> 35 Search Insert Position [Easy]
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
##### Sample input:
[1,3,5,6], 5
##### Sample output:
2

##### Questions to ask to clarify requirements:

- What should be returned if the target is not found in the array?
- Can the array contain duplicate elements?
- Can the target be negative?
- Can the array be empty?

##### Optimal Python solution:
```python
def searchInsert(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return left
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:

- The array is sorted and contains distinct integers.
- The target may or may not be present in the array.
- If the target is not found, return the index where it would be if it were inserted in order.

- Understand the concept of binary search.
- Handle edge cases such as an empty array or a negative target.
- Use the left pointer to represent the insertion position if the target is not found.

- Using binary search to find the target or the insertion position.
- Handling the case when the target is not found in the array.

- Using linear search to find the target or the insertion position.
- Sorting the array before finding the target or the insertion position.
    
### >> 374 Guess Number Higher or Lower [Easy]
We are playing the Guess Game. The game is as follows: I pick a number from 1 to n. You have to guess which number I picked. Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess. You call a pre-defined API int guess(int num), which returns 3 possible results (-1, 1, or 0): -1 if my number is lower, 1 if my number is higher, or 0 if your guess is correct. Return the number that I picked.
##### Sample input:
10
6
##### Sample output:
6

##### Questions to ask to clarify requirements:

- Can n be negative?
- Can the guess function return any other values?
- Can the guess function be called multiple times for the same number?

##### Optimal Python solution:
```python
def guessNumber(n):
    left = 1
    right = n
    while left <= right:
        mid = (left + right) // 2
        result = guess(mid)
        if result == 0:
            return mid
        elif result == -1:
            right = mid - 1
        else:
            left = mid + 1
```
##### Time complexity:
O(logn)
##### Space complexity:
O(1)
##### Notes:

- Use binary search to find the number
- Keep updating the left and right boundaries based on the guess result

- Make sure to handle the guess result correctly and update the boundaries accordingly

- Handling the guess result and updating the boundaries

- Brute force guessing each number
    
### >> Comparison: 35 Search Insert Position [Easy] *VS* 374 Guess Number Higher or Lower [Easy]
> Similarity distance: 0.3996
##### Similarities

- Both questions are classified as Easy level.
- Both questions involve searching for a target number.
- Both questions require determining the correct position for the target number.
##### Differences

- Question 35 involves searching for the target number in a sorted array and returning its index if found, or the index where it should be inserted if not found.
- Question 374 involves guessing a target number and receiving feedback on whether the guess is higher or lower than the target.
##### New Insights in 374 Guess Number Higher or Lower [Easy]

- Question 35 teaches us how to perform binary search on a sorted array to find the correct position for a target number efficiently.
- Question 374 introduces the concept of guessing a target number and using feedback to narrow down the search space.


---
# 2. From 374 Guess Number Higher or Lower [Easy] to 103 Binary Tree Zigzag Level Order Traversal [Medium]
> Similarity Distance: 0.4547

### >> Reminder: 374 Guess Number Higher or Lower [Easy]
We are playing the Guess Game. The game is as follows: I pick a number from 1 to n. You have to guess which number I picked. Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess. You call a pre-defined API int guess(int num), which returns 3 possible results (-1, 1, or 0): -1 if my number is lower, 1 if my number is higher, or 0 if your guess is correct. Return the number that I picked.
##### Optimal Python solution:
```python
def guessNumber(n):
    left = 1
    right = n
    while left <= right:
        mid = (left + right) // 2
        result = guess(mid)
        if result == 0:
            return mid
        elif result == -1:
            right = mid - 1
        else:
            left = mid + 1
```
Guess the number picked by the game using binary search.
    
### >> 103 Binary Tree Zigzag Level Order Traversal [Medium]
Given a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
[[3],[20,9],[15,7]]

##### Questions to ask to clarify requirements:

- Can the tree be empty?
- Can the tree have duplicate values?

##### Optimal Python solution:
```python
class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        res = []
        queue = collections.deque([root])
        level = 0
        while queue:
            level_vals = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level_vals.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            if level % 2 == 1:
                level_vals.reverse()
            res.append(level_vals)
            level += 1
        return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a queue to perform breadth-first search
- Reverse the level values if the level is odd

- Use a deque for efficient popping from both ends

- Reversing the level values

- Using recursion
    
### >> Comparison: 374 Guess Number Higher or Lower [Easy] *VS* 103 Binary Tree Zigzag Level Order Traversal [Medium]
> Similarity distance: 0.4547
##### Similarities

- Both questions involve searching for a target value.
- Both questions require traversing a data structure.
##### Differences

- Question 374 involves guessing a number within a given range.
- Question 103 involves traversing a binary tree in a zigzag pattern.
- Question 374 is classified as an Easy level question, while question 103 is classified as a Medium level question.
##### New Insights in 103 Binary Tree Zigzag Level Order Traversal [Medium]

- Question 374 introduces the concept of binary search to efficiently guess the number.
- Question 103 introduces the concept of zigzag level order traversal to traverse a binary tree in a different pattern.


---
# 3. From 103 Binary Tree Zigzag Level Order Traversal [Medium] to 107 Binary Tree Level Order Traversal II [Medium]
> Similarity Distance: 0.2505

### >> Reminder: 103 Binary Tree Zigzag Level Order Traversal [Medium]
Given a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).
##### Optimal Python solution:
```python
class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        res = []
        queue = collections.deque([root])
        level = 0
        while queue:
            level_vals = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level_vals.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            if level % 2 == 1:
                level_vals.reverse()
            res.append(level_vals)
            level += 1
        return res
```
Performing breadth-first search on a binary tree and reversing level values if necessary.
    
### >> 107 Binary Tree Level Order Traversal II [Medium]
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (i.e., from left to right, level by level from leaf to root).
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
[[15,7],[9,20],[3]]

##### Questions to ask to clarify requirements:
What should be returned if the tree is empty?

##### Optimal Python solution:
```python
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result[::-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a queue to perform a breadth-first search
2. Append each level to the result list
3. Reverse the result list before returning
Remember to check if the tree is empty before starting the traversal.
None
None
    
### >> Comparison: 103 Binary Tree Zigzag Level Order Traversal [Medium] *VS* 107 Binary Tree Level Order Traversal II [Medium]
> Similarity distance: 0.2505
##### Similarities

- Both questions involve traversing a binary tree in a specific order.
- Both questions require level order traversal of the binary tree.
##### Differences

- Question 103 performs a zigzag level order traversal, while question 107 performs a regular level order traversal.
- In question 103, the order of traversal alternates between left to right and right to left at each level, while in question 107, the order is from left to right at each level.
- The output format is different: question 103 returns a list of lists, where each inner list represents a level of the tree, while question 107 returns a list of lists in reverse order.
- Question 103 requires additional logic to alternate the traversal direction at each level, while question 107 does not have this requirement.
##### New Insights in 107 Binary Tree Level Order Traversal II [Medium]

- Both questions provide insights into different ways of traversing a binary tree.
- Question 103 introduces the concept of zigzag level order traversal, which can be useful in certain scenarios.
- Question 107 demonstrates a different approach to level order traversal by reversing the order of the output.


---
# 4. From 107 Binary Tree Level Order Traversal II [Medium] to 429 N-ary Tree Level Order Traversal [Medium]
> Similarity Distance: 0.1696

### >> Reminder: 107 Binary Tree Level Order Traversal II [Medium]
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (i.e., from left to right, level by level from leaf to root).
##### Optimal Python solution:
```python
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result[::-1]
```
Perform a breadth-first search on a binary tree and return the level order traversal from bottom to top.
    
### >> 429 N-ary Tree Level Order Traversal [Medium]
Given an n-ary tree, return the level order traversal of its nodes' values.
##### Sample input:
[1,null,3,2,4,null,5,6]
##### Sample output:
[[1],[3,2,4],[5,6]]

##### Questions to ask to clarify requirements:

- What is the definition of an n-ary tree?
- What is the expected output format?

##### Optimal Python solution:
```python
class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root:
            return []
        queue = deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                queue.extend(node.children)
            result.append(level)
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a queue to perform breadth-first search
- Append each level to the result list

- Use a deque as the queue for efficient popping from both ends

- Handling an empty tree

- Using recursion
    
### >> Comparison: 107 Binary Tree Level Order Traversal II [Medium] *VS* 429 N-ary Tree Level Order Traversal [Medium]
> Similarity distance: 0.1696
##### Similarities

- Both questions involve traversing a tree in level order
- Both questions require returning the level order traversal in reverse order
##### Differences

- 107 Binary Tree Level Order Traversal II is for binary trees, while 429 N-ary Tree Level Order Traversal is for N-ary trees
- 107 Binary Tree Level Order Traversal II uses a queue for level order traversal, while 429 N-ary Tree Level Order Traversal uses a queue or stack depending on the implementation
- 107 Binary Tree Level Order Traversal II uses a list to store the level order traversal in reverse order, while 429 N-ary Tree Level Order Traversal uses a list of lists to store the level order traversal
##### New Insights in 429 N-ary Tree Level Order Traversal [Medium]

- In both questions, we can use a queue or stack to perform level order traversal
- In both questions, we can use a list or list of lists to store the level order traversal
- In both questions, we need to reverse the level order traversal before returning the result


---
# 5. From 107 Binary Tree Level Order Traversal II [Medium] to 430 Flatten a Multilevel Doubly Linked List [Medium]
> Similarity Distance: 0.4635

### >> Reminder: 107 Binary Tree Level Order Traversal II [Medium]
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (i.e., from left to right, level by level from leaf to root).
##### Optimal Python solution:
```python
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result[::-1]
```
Perform a breadth-first search on a binary tree and return the level order traversal from bottom to top.
    
### >> 430 Flatten a Multilevel Doubly Linked List [Medium]
Flatten a multilevel doubly linked list.
##### Sample input:
[1,2,3,4,5,6,null,null,null,7,8,9,10,null,null,11,12]
##### Sample output:
[1,2,3,7,8,11,12,9,10,4,5,6]

##### Questions to ask to clarify requirements:

- What is the definition of a multilevel doubly linked list?
- What is the expected output format?

##### Optimal Python solution:
```python
class Solution:
    def flatten(self, head: 'Node') -> 'Node':
        if not head:
            return None
        stack = [head]
        prev = None
        while stack:
            node = stack.pop()
            if prev:
                prev.next = node
                node.prev = prev
            if node.next:
                stack.append(node.next)
            if node.child:
                stack.append(node.child)
                node.child = None
            prev = node
        return head
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a stack to perform depth-first search
- Update the next and prev pointers

- Use a stack to keep track of the nodes to be processed

- Handling an empty list

- Using recursion
    
### >> Comparison: 107 Binary Tree Level Order Traversal II [Medium] *VS* 430 Flatten a Multilevel Doubly Linked List [Medium]
> Similarity distance: 0.4635
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating a data structure.
- Both questions require traversing the data structure in a specific order.
##### Differences

- 107 Binary Tree Level Order Traversal II involves a binary tree, while 430 Flatten a Multilevel Doubly Linked List involves a doubly linked list.
- 107 Binary Tree Level Order Traversal II requires traversing the tree in a level order, while 430 Flatten a Multilevel Doubly Linked List requires flattening the list.
- 107 Binary Tree Level Order Traversal II outputs the traversal in reverse order, while 430 Flatten a Multilevel Doubly Linked List modifies the original list structure.
##### New Insights in 430 Flatten a Multilevel Doubly Linked List [Medium]

- In 107 Binary Tree Level Order Traversal II, we can use a queue to perform the level order traversal.
- In 430 Flatten a Multilevel Doubly Linked List, we can use a stack to keep track of the next node to visit.


---
# 6. From 374 Guess Number Higher or Lower [Easy] to 456 132 Pattern [Medium]
> Similarity Distance: 0.4961

### >> Reminder: 374 Guess Number Higher or Lower [Easy]
We are playing the Guess Game. The game is as follows: I pick a number from 1 to n. You have to guess which number I picked. Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess. You call a pre-defined API int guess(int num), which returns 3 possible results (-1, 1, or 0): -1 if my number is lower, 1 if my number is higher, or 0 if your guess is correct. Return the number that I picked.
##### Optimal Python solution:
```python
def guessNumber(n):
    left = 1
    right = n
    while left <= right:
        mid = (left + right) // 2
        result = guess(mid)
        if result == 0:
            return mid
        elif result == -1:
            right = mid - 1
        else:
            left = mid + 1
```
Guess the number picked by the game using binary search.
    
### >> 456 132 Pattern [Medium]
Given an array of n integers nums, a 132 pattern is a subsequence of three integers nums[i], nums[j] and nums[k] such that i < j < k and nums[i] < nums[k] < nums[j]. Return true if there is a 132 pattern in nums, otherwise, return false. Follow up: The O(n^2) is trivial, could you come up with the O(n logn) or the O(n) solution?
##### Sample input:
[1,2,3,4]
##### Sample output:
false

##### Questions to ask to clarify requirements:
What is the maximum length of the input array?

##### Optimal Python solution:
```python
def find132pattern(nums):
    stack = []
    s3 = float('-inf')
    for i in range(len(nums)-1, -1, -1):
        if nums[i] < s3:
            return True
        while stack and nums[i] > stack[-1]:
            s3 = stack.pop()
        stack.append(nums[i])
    return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to keep track of the potential 132 pattern
2. Iterate through the array from right to left
3. If a number is smaller than the top of the stack, update the s3 variable
4. If a number is larger than the top of the stack, pop the stack until finding a smaller number
5. Return True if a 132 pattern is found, otherwise return False
Use a stack to keep track of the potential 132 pattern.
None
None
    
### >> Comparison: 374 Guess Number Higher or Lower [Easy] *VS* 456 132 Pattern [Medium]
> Similarity distance: 0.4961
##### Similarities

- Both questions are related to guessing a number or pattern.
- Both questions have a specific target to guess.
- Both questions involve a process of elimination.
##### Differences

- 374 Guess Number Higher or Lower is an easy level question, while 456 132 Pattern is a medium level question.
- 374 Guess Number Higher or Lower involves guessing a number within a given range, while 456 132 Pattern involves finding a specific pattern in an array.
- 374 Guess Number Higher or Lower uses a binary search algorithm, while 456 132 Pattern uses a stack.
- 374 Guess Number Higher or Lower has a time complexity of O(log n), while 456 132 Pattern has a time complexity of O(n).
##### New Insights in 456 132 Pattern [Medium]

- From 374 Guess Number Higher or Lower, we can learn how to implement a binary search algorithm to efficiently guess a number within a given range.
- From 456 132 Pattern, we can learn how to use a stack to find a specific pattern in an array.


---
# 7. From 35 Search Insert Position [Easy] to 208 Implement Trie (Prefix Tree) [Medium]
> Similarity Distance: 0.4711

### >> Reminder: 35 Search Insert Position [Easy]
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
##### Optimal Python solution:
```python
def searchInsert(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return left
```
Binary search to find target or insertion position in a sorted array.
    
### >> 208 Implement Trie (Prefix Tree) [Medium]
Implement a trie with insert, search, and startsWith methods.
##### Sample input:
None
##### Sample output:
None

##### Questions to ask to clarify requirements:

- Can the trie contain duplicate words?
- Can the trie contain words with special characters?
- Can the trie contain words with spaces?

##### Optimal Python solution:
```python
class TrieNode:
    def __init__(self):
        self.children = [None] * 26
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            index = ord(char) - ord('a')
            if not node.children[index]:
                node.children[index] = TrieNode()
            node = node.children[index]
        node.is_end_of_word = True

    def search(self, word):
        node = self.root
        for char in word:
            index = ord(char) - ord('a')
            if not node.children[index]:
                return False
            node = node.children[index]
        return node.is_end_of_word

    def startsWith(self, prefix):
        node = self.root
        for char in prefix:
            index = ord(char) - ord('a')
            if not node.children[index]:
                return False
            node = node.children[index]
        return True
```
##### Time complexity:
O(L)
##### Space complexity:
O(L)
##### Notes:

- The problem can be solved using a trie data structure.
- A trie is a tree-like data structure that stores a collection of strings.
- Each node in the trie represents a character, and the edges represent the next characters in the string.

- Use a trie data structure to efficiently store and search for strings.
- Represent each character in the trie as a node, and the edges as the next characters in the string.
- Use a boolean attribute to mark the end of a word in the trie.

- Handling case-insensitive search efficiently.
- Handling deletion of words from the trie efficiently.

- Using a brute force approach to search for words in the trie.
- Using a brute force approach to insert words into the trie.
    
### >> Comparison: 35 Search Insert Position [Easy] *VS* 208 Implement Trie (Prefix Tree) [Medium]
> Similarity distance: 0.4711
##### Similarities

- Both questions involve searching for a target element in a data structure.
- Both questions require implementing efficient search algorithms.
##### Differences

- Search Insert Position is an easy level question, while Implement Trie is a medium level question.
- Search Insert Position involves searching for a target element in a sorted array, while Implement Trie involves searching for a prefix in a trie data structure.
- Search Insert Position can be solved using binary search, while Implement Trie requires implementing a trie data structure from scratch.
- Search Insert Position has a time complexity of O(log n), while Implement Trie has a time complexity of O(m), where n is the size of the array and m is the length of the prefix.
##### New Insights in 208 Implement Trie (Prefix Tree) [Medium]

- Search Insert Position teaches us how to efficiently search for an element in a sorted array using binary search.
- Implement Trie teaches us how to implement a trie data structure, which is useful for efficient prefix search operations.

