
# Leetcode Intensive Tutorial Day 49 
> [Difficulty Score: 24]

> [Version: 20231225_200427]

## Courses overview of the day

- 373 Find K Pairs with Smallest Sums [Medium]
  - 23 Merge k Sorted Lists [Hard]
    - 358 Rearrange String k Distance Apart [Hard]
      - 218 The Skyline Problem [Hard]
        - 546 Remove Boxes [Hard]
        - 502 IPO [Hard]
  - 146 LRU Cache [Medium]

#### Steps by steps

 - [1. From 373 Find K Pairs with Smallest Sums [Medium] to 23 Merge k Sorted Lists [Hard]](#1-from-373-find-k-pairs-with-smallest-sums-medium-to-23-merge-k-sorted-lists-hard)

 - [2. From 23 Merge k Sorted Lists [Hard] to 358 Rearrange String k Distance Apart [Hard]](#2-from-23-merge-k-sorted-lists-hard-to-358-rearrange-string-k-distance-apart-hard)

 - [3. From 358 Rearrange String k Distance Apart [Hard] to 218 The Skyline Problem [Hard]](#3-from-358-rearrange-string-k-distance-apart-hard-to-218-the-skyline-problem-hard)

 - [4. From 218 The Skyline Problem [Hard] to 546 Remove Boxes [Hard]](#4-from-218-the-skyline-problem-hard-to-546-remove-boxes-hard)

 - [5. From 218 The Skyline Problem [Hard] to 502 IPO [Hard]](#5-from-218-the-skyline-problem-hard-to-502-ipo-hard)

 - [6. From 373 Find K Pairs with Smallest Sums [Medium] to 146 LRU Cache [Medium]](#6-from-373-find-k-pairs-with-smallest-sums-medium-to-146-lru-cache-medium)

#### Summary


- 218 The Skyline Problem : Find the skyline formed by a set of buildings using a divide and conquer approach and a heap.
- 502 IPO : The essence of this problem is to select the projects with the maximum profit and the available capital using two heaps.
- 358 Rearrange String k Distance Apart : Rearranging the string with the same characters at least k distance apart using a max heap.
- 373 Find K Pairs with Smallest Sums : Find the k pairs with the smallest sums from two sorted arrays.
- 546 Remove Boxes : The essence of the problem is to find the maximum points that can be obtained by removing boxes in each round.
- 23 Merge k Sorted Lists : Merge k sorted linked lists using a min heap.
- 146 LRU Cache : The essence of this problem is to design a data structure that can efficiently store key-value pairs and remove the least recently used pair when the cache is full.
> Similarity Diameter of these problems: 0.6334


---
# 1. From 373 Find K Pairs with Smallest Sums [Medium] to 23 Merge k Sorted Lists [Hard]
> Similarity Distance: 0.4047

### >> 373 Find K Pairs with Smallest Sums [Medium]
Given two integer arrays nums1 and nums2 sorted in ascending order and an integer k, return the k pairs with the smallest sums.
##### Sample input:
[1,7,11]
[2,4,6]
3
##### Sample output:
[[1,2],[1,4],[1,6]]

##### Questions to ask to clarify requirements:

- Are the arrays always sorted in ascending order?
- Can the arrays contain duplicate elements?
- Can the arrays be empty?
- Can k be greater than the total number of pairs?

##### Optimal Python solution:
```python
def kSmallestPairs(nums1, nums2, k):
    import heapq
    heap = []
    for i in range(len(nums1)):
        for j in range(len(nums2)):
            heapq.heappush(heap, (nums1[i] + nums2[j], [nums1[i], nums2[j]]))
    res = []
    for _ in range(min(k, len(heap))):
        res.append(heapq.heappop(heap)[1])
    return res
```
##### Time complexity:
O(n*m*log(n*m))
##### Space complexity:
O(n*m)
##### Notes:

- Use a min heap to store the pairs with their sums
- Iterate through the arrays and add all possible pairs to the heap
- Pop the smallest k pairs from the heap

- Use the heapq module in Python to implement the min heap
- Consider using the two pointers technique to optimize the solution

- Handling duplicate pairs with the same sum

- Sorting the entire array
    
### >> 23 Merge k Sorted Lists [Hard]
Merge k sorted linked lists and return it as one sorted list.
##### Sample input:
[[1,4,5],[1,3,4],[2,6]]
##### Sample output:
[1,1,2,3,4,4,5,6]

##### Questions to ask to clarify requirements:

- Can the input lists be empty?
- Can the input lists contain cycles?
- What is the maximum length of the input lists?

##### Optimal Python solution:
```python
def mergeKLists(self, lists: List[ListNode]) -> ListNode:
    heap = []
    for i, l in enumerate(lists):
        if l:
            heap.append((l.val, i))
            l = l.next
    heapq.heapify(heap)
    dummy = ListNode()
    curr = dummy
    while heap:
        val, i = heapq.heappop(heap)
        curr.next = ListNode(val)
        curr = curr.next
        if lists[i]:
            heapq.heappush(heap, (lists[i].val, i))
            lists[i] = lists[i].next
    return dummy.next
```
##### Time complexity:
O(N log k)
##### Space complexity:
O(k)
##### Notes:

- Use a min heap to keep track of the smallest element from each list
- Pop the smallest element from the heap and append it to the result list
- If the popped element has a next node, push the next node into the heap

- Use the heapq module in Python to implement the min heap.
- Initialize the heap with the first element from each list.
- Pop the smallest element from the heap and append it to the result list.
- If the popped element has a next node, push the next node into the heap.

- Handling empty lists in the input
- Updating the heap after popping an element

- Using a brute force approach to merge the lists
- Using a quadratic time complexity solution
    
### >> Comparison: 373 Find K Pairs with Smallest Sums [Medium] *VS* 23 Merge k Sorted Lists [Hard]
> Similarity distance: 0.4047
##### Similarities

- Both questions involve finding the k smallest elements from a set of pairs or lists.
- Both questions require sorting the pairs or lists based on their sums or values.
- Both questions have a time complexity of O(nlogn) or higher.
##### Differences

- Question 373 involves finding the k smallest sums from two sorted arrays, while question 23 involves merging k sorted lists.
- Question 373 requires maintaining a heap of size k to track the smallest sums, while question 23 requires merging the k lists using a priority queue.
- Question 373 has a space complexity of O(k), while question 23 has a space complexity of O(k) or O(n) depending on the approach.
- Question 373 can be solved using a two-pointer approach, while question 23 requires merging the lists iteratively or recursively.
##### New Insights in 23 Merge k Sorted Lists [Hard]

- Question 373 introduces the concept of maintaining a heap to track the k smallest elements efficiently.
- Question 23 introduces the concept of merging k sorted lists using a priority queue or a divide-and-conquer approach.


---
# 2. From 23 Merge k Sorted Lists [Hard] to 358 Rearrange String k Distance Apart [Hard]
> Similarity Distance: 0.5024

### >> Reminder: 23 Merge k Sorted Lists [Hard]
Merge k sorted linked lists and return it as one sorted list.
##### Optimal Python solution:
```python
def mergeKLists(self, lists: List[ListNode]) -> ListNode:
    heap = []
    for i, l in enumerate(lists):
        if l:
            heap.append((l.val, i))
            l = l.next
    heapq.heapify(heap)
    dummy = ListNode()
    curr = dummy
    while heap:
        val, i = heapq.heappop(heap)
        curr.next = ListNode(val)
        curr = curr.next
        if lists[i]:
            heapq.heappush(heap, (lists[i].val, i))
            lists[i] = lists[i].next
    return dummy.next
```
Merge k sorted linked lists using a min heap.
    
### >> 358 Rearrange String k Distance Apart [Hard]
Given a non-empty string s and an integer k, rearrange the string such that the same characters are at least distance k from each other.
##### Sample input:
"aabbcc", 3

##### Sample output:
"abcabc"


##### Questions to ask to clarify requirements:
What should be returned if it is impossible to rearrange the string?

##### Optimal Python solution:
```python
class Solution:
    def rearrangeString(self, s: str, k: int) -> str:
        if k == 0:
            return s
        counter = collections.Counter(s)
        heap = []
        for char, count in counter.items():
            heapq.heappush(heap, (-count, char))
        result = []
        while heap:
            temp = []
            for _ in range(k):
                if not heap:
                    if len(result) < len(s):
                        return ""
                    break
                count, char = heapq.heappop(heap)
                result.append(char)
                if count + 1 < 0:
                    temp.append((count + 1, char))
            for item in temp:
                heapq.heappush(heap, item)
        return ''.join(result)

```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:
1. If k is 0, return s.
2. Count the frequency of each character in s.
3. Create a max heap of tuples (-count, char) using the Counter.
4. Initialize an empty list result.
5. Iterate while heap is not empty:
    - Create a temporary list temp.
    - Iterate k times:
        - If heap is empty:
            - If the length of result is less than the length of s, return an empty string.
            - Break the loop.
        - Pop the top element from the heap (count, char).
        - Append char to result.
        - If count + 1 < 0, append (count + 1, char) to temp.
    - Iterate over temp and push each item to the heap.
6. Return the concatenation of all characters in result.
None
None
None
    
### >> Comparison: 23 Merge k Sorted Lists [Hard] *VS* 358 Rearrange String k Distance Apart [Hard]
> Similarity distance: 0.5024
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve manipulating and merging multiple lists.
- Both questions require careful consideration of the order and distance of elements.
##### Differences

- Question 23 involves merging k sorted lists into a single sorted list.
- Question 358 involves rearranging a string such that the same characters are at least k distance apart.
- Question 23 focuses on lists and sorting, while question 358 focuses on string manipulation.
- Question 23 has a straightforward solution using a priority queue, while question 358 requires more complex algorithms.
##### New Insights in 358 Rearrange String k Distance Apart [Hard]

- Question 23 teaches us how to merge multiple sorted lists efficiently.
- Question 358 teaches us how to rearrange a string with specific constraints.
- Both questions provide insights into algorithm design and optimization.


---
# 3. From 358 Rearrange String k Distance Apart [Hard] to 218 The Skyline Problem [Hard]
> Similarity Distance: 0.4633

### >> Reminder: 358 Rearrange String k Distance Apart [Hard]
Given a non-empty string s and an integer k, rearrange the string such that the same characters are at least distance k from each other.
##### Optimal Python solution:
```python
class Solution:
    def rearrangeString(self, s: str, k: int) -> str:
        if k == 0:
            return s
        counter = collections.Counter(s)
        heap = []
        for char, count in counter.items():
            heapq.heappush(heap, (-count, char))
        result = []
        while heap:
            temp = []
            for _ in range(k):
                if not heap:
                    if len(result) < len(s):
                        return ""
                    break
                count, char = heapq.heappop(heap)
                result.append(char)
                if count + 1 < 0:
                    temp.append((count + 1, char))
            for item in temp:
                heapq.heappush(heap, item)
        return ''.join(result)

```
Rearranging the string with the same characters at least k distance apart using a max heap.
    
### >> 218 The Skyline Problem [Hard]
A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return the skyline formed by these buildings collectively.
##### Sample input:
[[2,9,10],[3,7,15],[5,12,12],[15,20,10],[19,24,8]]
##### Sample output:
[[2,10],[3,15],[7,12],[12,0],[15,10],[20,8],[24,0]]

##### Questions to ask to clarify requirements:
What is the format of the input? Are the buildings represented as tuples?

##### Optimal Python solution:
```python
def getSkyline(buildings):
    if not buildings:
        return []
    points = []
    for l, r, h in buildings:
        points.append((l, -h))
        points.append((r, h))
    points.sort()
    result = []
    heap = [(0, float('inf'))]
    prev_height = 0
    for x, h in points:
        if h < 0:
            heapq.heappush(heap, (h, x))
        else:
            heap.remove((-h, x))
            heapq.heapify(heap)
        curr_height = -heap[0][0]
        if curr_height != prev_height:
            result.append([x, curr_height])
            prev_height = curr_height
    return result
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:
Use a heap to keep track of the current maximum height.
Use a heap to efficiently keep track of the current maximum height.
None
None
    
### >> Comparison: 358 Rearrange String k Distance Apart [Hard] *VS* 218 The Skyline Problem [Hard]
> Similarity distance: 0.4633
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve rearranging elements in a specific order.
- Both questions require efficient algorithms to solve.
##### Differences

- Question 358 Rearrange String k Distance Apart focuses on rearranging characters in a string, while question 218 The Skyline Problem focuses on rearranging building heights.
- Question 358 Rearrange String k Distance Apart has a constraint of maintaining a minimum distance of k between the same characters, while question 218 The Skyline Problem does not have such a constraint.
- Question 358 Rearrange String k Distance Apart requires rearranging characters in a specific order, while question 218 The Skyline Problem requires finding the skyline of a city.
##### New Insights in 218 The Skyline Problem [Hard]

- Question 358 Rearrange String k Distance Apart introduces the concept of rearranging characters in a string while maintaining a minimum distance between the same characters.
- Question 218 The Skyline Problem introduces the concept of finding the skyline of a city by analyzing the heights of buildings.


---
# 4. From 218 The Skyline Problem [Hard] to 546 Remove Boxes [Hard]
> Similarity Distance: 0.4175

### >> Reminder: 218 The Skyline Problem [Hard]
A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return the skyline formed by these buildings collectively.
##### Optimal Python solution:
```python
def getSkyline(buildings):
    if not buildings:
        return []
    points = []
    for l, r, h in buildings:
        points.append((l, -h))
        points.append((r, h))
    points.sort()
    result = []
    heap = [(0, float('inf'))]
    prev_height = 0
    for x, h in points:
        if h < 0:
            heapq.heappush(heap, (h, x))
        else:
            heap.remove((-h, x))
            heapq.heapify(heap)
        curr_height = -heap[0][0]
        if curr_height != prev_height:
            result.append([x, curr_height])
            prev_height = curr_height
    return result
```
Find the skyline formed by a set of buildings using a divide and conquer approach and a heap.
    
### >> 546 Remove Boxes [Hard]
Given several boxes with different colors represented by different positive numbers. You may experience several rounds to remove boxes until there is no box left. Each time you can choose some continuous boxes with the same color (composed of k boxes, k >= 1), remove them and get k*k points. Find the maximum points you can get.
##### Sample input:
[1,3,2,2,2,3,4,3,1]
##### Sample output:
23

##### Questions to ask to clarify requirements:
What is the maximum number of boxes that can be removed in each round? Can the boxes be rearranged after each round?

##### Optimal Python solution:
```python
class Solution:
    def removeBoxes(self, boxes: List[int]) -> int:
        n = len(boxes)
        dp = [[[0] * n for _ in range(n)] for _ in range(n)]

        def calculatePoints(boxes, dp, i, j, k):
            if i > j:
                return 0
            if dp[i][j][k] != 0:
                return dp[i][j][k]
            while i + 1 <= j and boxes[i] == boxes[i + 1]:
                i += 1
                k += 1
            result = (k + 1) * (k + 1) + calculatePoints(boxes, dp, i + 1, j, 0)
            for m in range(i + 1, j + 1):
                if boxes[i] == boxes[m]:
                    result = max(result, calculatePoints(boxes, dp, i + 1, m - 1, 0) + calculatePoints(boxes, dp, m, j, k + 1))
            dp[i][j][k] = result
            return result

        return calculatePoints(boxes, dp, 0, n - 1, 0)
```
##### Time complexity:
O(n^4)
##### Space complexity:
O(n^3)
##### Notes:
1. Each round, you can choose some continuous boxes with the same color and remove them to get points.
2. The points obtained are equal to the square of the number of boxes removed.
3. The goal is to find the maximum points that can be obtained by removing boxes.
4. The boxes cannot be rearranged after each round.
5. The boxes are represented by positive numbers.
1. Use a dynamic programming approach to solve the problem.
2. Use memoization to avoid duplicate calculations.
3. Break down the problem into smaller subproblems.
1. Handling the case when there are no boxes left.
2. Avoiding duplicate calculations by using memoization.
3. Optimizing the solution to reduce the time complexity.
1. Avoid using a brute force approach to calculate the points for all possible combinations of boxes.
2. Avoid using a recursive approach without memoization.
3. Avoid using a solution that rearranges the boxes after each round.
    
### >> Comparison: 218 The Skyline Problem [Hard] *VS* 546 Remove Boxes [Hard]
> Similarity distance: 0.4175
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve solving a problem using algorithms and data structures.
- Both questions require a deep understanding of dynamic programming.
- Both questions have multiple possible approaches to solve them.
##### Differences

- The Skyline Problem involves finding the skyline of a city given the coordinates of buildings, while Remove Boxes involves removing boxes from a list based on certain rules.
- The Skyline Problem requires finding the critical points where the height of the skyline changes, while Remove Boxes requires finding the maximum points that can be obtained by removing boxes.
- The Skyline Problem can be solved using a divide and conquer approach, while Remove Boxes can be solved using dynamic programming.
- The Skyline Problem has a time complexity of O(n log n), while Remove Boxes has a time complexity of O(n^4).
##### New Insights in 546 Remove Boxes [Hard]

- The Skyline Problem introduces the concept of skyline and how to find it efficiently.
- Remove Boxes introduces the concept of removing boxes based on certain rules and maximizing the points obtained.
- Both questions provide insights into how to approach complex algorithmic problems and optimize their solutions.


---
# 5. From 218 The Skyline Problem [Hard] to 502 IPO [Hard]
> Similarity Distance: 0.5321

### >> Reminder: 218 The Skyline Problem [Hard]
A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return the skyline formed by these buildings collectively.
##### Optimal Python solution:
```python
def getSkyline(buildings):
    if not buildings:
        return []
    points = []
    for l, r, h in buildings:
        points.append((l, -h))
        points.append((r, h))
    points.sort()
    result = []
    heap = [(0, float('inf'))]
    prev_height = 0
    for x, h in points:
        if h < 0:
            heapq.heappush(heap, (h, x))
        else:
            heap.remove((-h, x))
            heapq.heapify(heap)
        curr_height = -heap[0][0]
        if curr_height != prev_height:
            result.append([x, curr_height])
            prev_height = curr_height
    return result
```
Find the skyline formed by a set of buildings using a divide and conquer approach and a heap.
    
### >> 502 IPO [Hard]
Suppose LeetCode will start its IPO soon. In order to sell a good price of its shares to Venture Capital, LeetCode would like to work on some projects to increase its capital.
##### Sample input:
2, 0, [1, 2, 3], [0, 1, 1]
##### Sample output:
4

##### Questions to ask to clarify requirements:
What is the maximum number of projects that can be selected? Can a project be selected multiple times?

##### Optimal Python solution:
```python
import heapq
class Solution:
    def findMaximizedCapital(self, k: int, w: int, profits: List[int], capital: List[int]) -> int:
        projects = []
        for i in range(len(profits)):
            heapq.heappush(projects, (capital[i], profits[i]))
        available = []
        for _ in range(k):
            while projects and projects[0][0] <= w:
                heapq.heappush(available, -heapq.heappop(projects)[1])
            if available:
                w -= heapq.heappop(available)
            else:
                break
        return w
```
##### Time complexity:
O(nlogn + klogn)
##### Space complexity:
O(n)
##### Notes:
1. Use a min-heap to store the projects sorted by their capital.
2. Use a max-heap to store the available projects sorted by their profits.
3. Iterate k times to select the projects with the maximum profit and the available capital.
4. Update the available capital and the maximum profit after each selection.
5. Return the final available capital.
Use the heapq module to implement the min-heap and the max-heap.
The tricky part is to use two heaps to store the projects and the available projects, respectively.
Avoid using a linear search to find the projects with the available capital.
    
### >> Comparison: 218 The Skyline Problem [Hard] *VS* 502 IPO [Hard]
> Similarity distance: 0.5321
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve solving optimization problems.
- Both questions require a combination of programming and problem-solving skills.
##### Differences

- 218 The Skyline Problem focuses on finding the skyline of a city given a set of buildings, while 502 IPO focuses on maximizing the total capital by selecting projects.
- 218 The Skyline Problem involves manipulating a list of buildings and determining the skyline, while 502 IPO involves selecting projects based on available capital.
- 218 The Skyline Problem requires understanding of data structures like heaps and priority queues, while 502 IPO requires understanding of concepts like initial public offerings and capital allocation.
##### New Insights in 502 IPO [Hard]

- From 218 The Skyline Problem, we can learn how to efficiently find the skyline of a city using data structures like heaps and priority queues.
- From 502 IPO, we can learn how to maximize the total capital by selecting projects based on available capital and expected profits.


---
# 6. From 373 Find K Pairs with Smallest Sums [Medium] to 146 LRU Cache [Medium]
> Similarity Distance: 0.5425

### >> Reminder: 373 Find K Pairs with Smallest Sums [Medium]
Given two integer arrays nums1 and nums2 sorted in ascending order and an integer k, return the k pairs with the smallest sums.
##### Optimal Python solution:
```python
def kSmallestPairs(nums1, nums2, k):
    import heapq
    heap = []
    for i in range(len(nums1)):
        for j in range(len(nums2)):
            heapq.heappush(heap, (nums1[i] + nums2[j], [nums1[i], nums2[j]]))
    res = []
    for _ in range(min(k, len(heap))):
        res.append(heapq.heappop(heap)[1])
    return res
```
Find the k pairs with the smallest sums from two sorted arrays.
    
### >> 146 LRU Cache [Medium]
Design a data structure that follows the constraints of a Least Recently Used (LRU) cache.
##### Sample input:
cache = LRUCache(2)
cache.put(1, 1)
cache.put(2, 2)
cache.get(1)
cache.put(3, 3)
cache.get(2)
cache.put(4, 4)
cache.get(1)
cache.get(3)
cache.get(4)
##### Sample output:
[1,-1,-1,3,4]

##### Questions to ask to clarify requirements:
What is the maximum capacity of the cache? What happens when the cache is full and a new key-value pair is added?

##### Optimal Python solution:
```python
class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = {}
        self.order = []

    def get(self, key: int) -> int:
        if key in self.cache:
            self.order.remove(key)
            self.order.append(key)
            return self.cache[key]
        return -1

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.order.remove(key)
        elif len(self.cache) == self.capacity:
            del self.cache[self.order[0]]
            self.order = self.order[1:]
        self.cache[key] = value
        self.order.append(key)
```
##### Time complexity:
O(1) for get and put operations
##### Space complexity:
O(capacity)
##### Notes:
1. Use a dictionary to store key-value pairs
2. Use a list to maintain the order of keys
3. When a key is accessed, remove it from the list and append it to the end
4. When the cache is full, remove the least recently used key-value pair
Understand the concept of an LRU cache and the use of a dictionary and list
Maintaining the order of keys in the list
Using a linked list to maintain the order of keys
    
### >> Comparison: 373 Find K Pairs with Smallest Sums [Medium] *VS* 146 LRU Cache [Medium]
> Similarity distance: 0.5425
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding the smallest or least frequent elements.
- Both questions require some form of data structure manipulation.
##### Differences

- Question 373 involves finding the k pairs with the smallest sums, while question 146 involves implementing an LRU cache.
- Question 373 requires comparing the sums of pairs, while question 146 requires managing a cache with limited capacity.
- Question 373 has a time complexity of O(k log k), while question 146 has a time complexity of O(1) for cache operations.
##### New Insights in 146 LRU Cache [Medium]

- Question 373 teaches us how to use a priority queue to efficiently find the k smallest sums.
- Question 146 teaches us how to implement an LRU cache using a combination of a doubly linked list and a hash map.

