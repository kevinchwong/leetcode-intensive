
# Leetcode Intensive Tutorial Day 53 
> [Difficulty Score: 24]

> [Version: 20231225_200427]

## Courses overview of the day

- 542 01 Matrix [Medium]
  - 286 Walls and Gates [Medium]
    - 126 Word Ladder II [Hard]
      - 127 Word Ladder [Medium]
      - 582 Kill Process [Medium]
      - 323 Number of Connected Components in an Undirected Graph [Medium]
        - 305 Number of Islands II [Hard]
        - 444 Sequence Reconstruction [Medium]
    - 317 Shortest Distance from All Buildings [Hard]

#### Steps by steps

 - [1. From 542 01 Matrix [Medium] to 286 Walls and Gates [Medium]](#1-from-542-01-matrix-medium-to-286-walls-and-gates-medium)

 - [2. From 286 Walls and Gates [Medium] to 126 Word Ladder II [Hard]](#2-from-286-walls-and-gates-medium-to-126-word-ladder-ii-hard)

 - [3. From 126 Word Ladder II [Hard] to 127 Word Ladder [Medium]](#3-from-126-word-ladder-ii-hard-to-127-word-ladder-medium)

 - [4. From 126 Word Ladder II [Hard] to 582 Kill Process [Medium]](#4-from-126-word-ladder-ii-hard-to-582-kill-process-medium)

 - [5. From 126 Word Ladder II [Hard] to 323 Number of Connected Components in an Undirected Graph [Medium]](#5-from-126-word-ladder-ii-hard-to-323-number-of-connected-components-in-an-undirected-graph-medium)

 - [6. From 323 Number of Connected Components in an Undirected Graph [Medium] to 305 Number of Islands II [Hard]](#6-from-323-number-of-connected-components-in-an-undirected-graph-medium-to-305-number-of-islands-ii-hard)

 - [7. From 323 Number of Connected Components in an Undirected Graph [Medium] to 444 Sequence Reconstruction [Medium]](#7-from-323-number-of-connected-components-in-an-undirected-graph-medium-to-444-sequence-reconstruction-medium)

 - [8. From 286 Walls and Gates [Medium] to 317 Shortest Distance from All Buildings [Hard]](#8-from-286-walls-and-gates-medium-to-317-shortest-distance-from-all-buildings-hard)

#### Summary


- 542 01 Matrix : Find the distance of the nearest 0 for each cell in a matrix using breadth-first search (BFS).
- 323 Number of Connected Components in an Undirected Graph : The essence of this problem is to find the number of connected components in an undirected graph using the union find algorithm.
- 305 Number of Islands II : The essence of this problem is to efficiently keep track of connected islands and count the number of islands after each expansion.
- 286 Walls and Gates : The essence of the problem is to find the distance from each empty room to the nearest gate using breadth-first search (BFS).
- 126 Word Ladder II : Find all shortest transformation sequences from beginWord to endWord.
- 582 Kill Process : Find the list of PIDs of all the processes that would be killed in the end.
- 444 Sequence Reconstruction : Check whether the original sequence org can be uniquely reconstructed from the sequences in seqs.
- 317 Shortest Distance from All Buildings : The essence of the problem is to find the shortest distance from each building to each empty land in a grid.
- 127 Word Ladder : The essence of this problem is to find the shortest transformation sequence from beginWord to endWord using BFS and generate all possible words by changing one character at a time.
> Similarity Diameter of these problems: 0.7718


---
# 1. From 542 01 Matrix [Medium] to 286 Walls and Gates [Medium]
> Similarity Distance: 0.4749

### >> 542 01 Matrix [Medium]
Given a matrix consisting of 0s and 1s, find the distance of the nearest 0 for each cell.
##### Sample input:
[[0,0,0],[0,1,0],[0,0,0]]
##### Sample output:
[[0,0,0],[0,1,0],[0,0,0]]

##### Questions to ask to clarify requirements:
What should be the output if there is no 0 in the matrix?

##### Optimal Python solution:
```python
def updateMatrix(matrix: List[List[int]]) -> List[List[int]]:
    m, n = len(matrix), len(matrix[0])
    queue = deque()
    for i in range(m):
        for j in range(n):
            if matrix[i][j] == 0:
                queue.append((i, j))
            else:
                matrix[i][j] = float('inf')
    while queue:
        x, y = queue.popleft()
        for dx, dy in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
            nx, ny = x + dx, y + dy
            if 0 <= nx < m and 0 <= ny < n and matrix[nx][ny] > matrix[x][y] + 1:
                matrix[nx][ny] = matrix[x][y] + 1
                queue.append((nx, ny))
    return matrix
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use a queue to perform breadth-first search (BFS).
2. Initialize the distance of each cell to infinity.
3. If a cell contains 0, enqueue it and set its distance to 0.
4. For each cell in the queue, update the distances of its neighboring cells if they are greater than the current distance plus 1.
Initialize the distance of each cell to infinity and update the distances of neighboring cells if they are greater than the current distance plus 1.
None
None
    
### >> 286 Walls and Gates [Medium]
You are given a m x n 2D grid initialized with these three possible values.

-1 - A wall or an obstacle.
0 - A gate.
INF - Infinity means an empty room. We use the value 231 - 1 = 2147483647 to represent INF as you may assume that the distance to a gate is less than 2147483647.
Fill each empty room with the distance to its nearest gate. If it is impossible to reach a gate, it should be filled with INF.
##### Sample input:
rooms = [[INF, -1, 0, INF],
         [INF, INF, INF, -1],
         [INF, -1, INF, -1],
         [0, -1, INF, INF]]
##### Sample output:
rooms = [[3, -1, 0, 1],
         [2, 2, 1, -1],
         [1, -1, 2, -1],
         [0, -1, 3, 4]]

##### Questions to ask to clarify requirements:
What is the definition of a gate in the grid?

##### Optimal Python solution:
```python
class Solution:
    def wallsAndGates(self, rooms: List[List[int]]) -> None:
        if not rooms:
            return
        m, n = len(rooms), len(rooms[0])
        queue = [(i, j) for i in range(m) for j in range(n) if rooms[i][j] == 0]
        for i, j in queue:
            for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                x, y = i + dx, j + dy
                if 0 <= x < m and 0 <= y < n and rooms[x][y] == INF:
                    rooms[x][y] = rooms[i][j] + 1
                    queue.append((x, y))
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use a breadth-first search (BFS) to find the distance from each empty room to the nearest gate.
2. Start the BFS from each gate and update the distance of each empty room as you traverse the grid.
3. Use a queue to keep track of the rooms to visit next.
Use a queue to implement breadth-first search (BFS) for graph traversal.
The distance to a room is the minimum number of steps required to reach a gate.
Avoid using a depth-first search (DFS) for this problem.
    
### >> Comparison: 542 01 Matrix [Medium] *VS* 286 Walls and Gates [Medium]
> Similarity distance: 0.4749
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve matrix manipulation.
- Both questions require finding the shortest distance from a source to a destination.
##### Differences

- 542 01 Matrix involves finding the distance of each cell from the nearest 0, while 286 Walls and Gates involves finding the distance of each gate from the nearest empty room.
- 542 01 Matrix uses 0 to represent empty cells and 1 to represent walls, while 286 Walls and Gates uses INF to represent walls and 0 to represent empty rooms.
- 542 01 Matrix uses breadth-first search (BFS) algorithm to find the shortest distance, while 286 Walls and Gates uses depth-first search (DFS) algorithm.
##### New Insights in 286 Walls and Gates [Medium]

- 542 01 Matrix: We can use dynamic programming to optimize the BFS algorithm by starting from the top-left corner and iterating through the matrix twice, first from top-left to bottom-right, and then from bottom-right to top-left.
- 286 Walls and Gates: We can use a recursive DFS algorithm to find the shortest distance from each gate to an empty room.


---
# 2. From 286 Walls and Gates [Medium] to 126 Word Ladder II [Hard]
> Similarity Distance: 0.4952

### >> Reminder: 286 Walls and Gates [Medium]
You are given a m x n 2D grid initialized with these three possible values.

-1 - A wall or an obstacle.
0 - A gate.
INF - Infinity means an empty room. We use the value 231 - 1 = 2147483647 to represent INF as you may assume that the distance to a gate is less than 2147483647.
Fill each empty room with the distance to its nearest gate. If it is impossible to reach a gate, it should be filled with INF.
##### Optimal Python solution:
```python
class Solution:
    def wallsAndGates(self, rooms: List[List[int]]) -> None:
        if not rooms:
            return
        m, n = len(rooms), len(rooms[0])
        queue = [(i, j) for i in range(m) for j in range(n) if rooms[i][j] == 0]
        for i, j in queue:
            for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                x, y = i + dx, j + dy
                if 0 <= x < m and 0 <= y < n and rooms[x][y] == INF:
                    rooms[x][y] = rooms[i][j] + 1
                    queue.append((x, y))
```
The essence of the problem is to find the distance from each empty room to the nearest gate using breadth-first search (BFS).
    
### >> 126 Word Ladder II [Hard]
Given two words (beginWord and endWord), and a dictionary's word list, find all shortest transformation sequence(s) from beginWord to endWord, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

Note:

- Return an empty list if there is no such transformation sequence.
- All words have the same length.
- All words contain only lowercase alphabetic characters.
- You may assume no duplicates in the word list.
- You may assume beginWord and endWord are non-empty and are not the same.
##### Sample input:
"hit", "cog", ["hot","dot","dog","lot","log","cog"]
##### Sample output:
[
  ["hit","hot","dot","dog","cog"],
  ["hit","hot","lot","log","cog"]
]

##### Questions to ask to clarify requirements:
Should the solution find all possible transformation sequences? Should it consider only lowercase alphabetic characters?

##### Optimal Python solution:
```python
from collections import defaultdict, deque

def findLadders(beginWord, endWord, wordList):
    wordSet = set(wordList)
    if endWord not in wordSet:
        return []
    layer = {}  # word: [path]
    layer[beginWord] = [[beginWord]]
    while layer:
        newlayer = defaultdict(list)
        for word in layer:
            if word == endWord:
                return layer[word]
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    newWord = word[:i] + c + word[i + 1:]
                    if newWord in wordSet:
                        newlayer[newWord] += [j + [newWord] for j in layer[word]]
        wordSet -= set(newlayer.keys())
        layer = newlayer
    return []
```
##### Time complexity:
O(M^2 * N)
##### Space complexity:
O(M^2 * N)
##### Notes:
1. Use breadth-first search to find the shortest path
2. Use backtracking to find all possible transformation sequences
Use a queue to implement breadth-first search. Use a dictionary to store the transformation sequences.
Finding all possible transformation sequences
None
    
### >> Comparison: 286 Walls and Gates [Medium] *VS* 126 Word Ladder II [Hard]
> Similarity distance: 0.4952
##### Similarities

- Both questions involve finding the shortest path between two points in a graph.
- Both questions require a breadth-first search (BFS) approach.
- Both questions involve manipulating a grid or graph structure.
##### Differences

- Question 286 involves finding the shortest path from each empty room to the nearest gate.
- Question 126 involves finding all the shortest paths from the start word to the end word.
- Question 286 uses a single queue for BFS, while question 126 uses multiple queues for BFS.
- Question 286 uses a distance matrix to track the shortest distance, while question 126 uses a map to track the shortest distance.
##### New Insights in 126 Word Ladder II [Hard]

- Question 286 introduces the concept of using a distance matrix to track the shortest distance.
- Question 126 introduces the concept of using multiple queues for BFS.
- Both questions provide practice in implementing BFS algorithms.


---
# 3. From 126 Word Ladder II [Hard] to 127 Word Ladder [Medium]
> Similarity Distance: 0.4535

### >> Reminder: 126 Word Ladder II [Hard]
Given two words (beginWord and endWord), and a dictionary's word list, find all shortest transformation sequence(s) from beginWord to endWord, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

Note:

- Return an empty list if there is no such transformation sequence.
- All words have the same length.
- All words contain only lowercase alphabetic characters.
- You may assume no duplicates in the word list.
- You may assume beginWord and endWord are non-empty and are not the same.
##### Optimal Python solution:
```python
from collections import defaultdict, deque

def findLadders(beginWord, endWord, wordList):
    wordSet = set(wordList)
    if endWord not in wordSet:
        return []
    layer = {}  # word: [path]
    layer[beginWord] = [[beginWord]]
    while layer:
        newlayer = defaultdict(list)
        for word in layer:
            if word == endWord:
                return layer[word]
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    newWord = word[:i] + c + word[i + 1:]
                    if newWord in wordSet:
                        newlayer[newWord] += [j + [newWord] for j in layer[word]]
        wordSet -= set(newlayer.keys())
        layer = newlayer
    return []
```
Find all shortest transformation sequences from beginWord to endWord.
    
### >> 127 Word Ladder [Medium]
Given two words, beginWord and endWord, and a dictionary wordList, return the length of the shortest transformation sequence from beginWord to endWord, or 0 if no such sequence exists.
##### Sample input:
"hit"
"cog"
["hot","dot","dog","lot","log","cog"]
##### Sample output:
5

##### Questions to ask to clarify requirements:
Are the words in the wordList guaranteed to be of the same length? Can we assume that beginWord and endWord are different and are of the same length? Can we modify the wordList?

##### Optimal Python solution:
```python
def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
    wordSet = set(wordList)
    if endWord not in wordSet:
        return 0
    queue = collections.deque([(beginWord, 1)])
    while queue:
        word, length = queue.popleft()
        if word == endWord:
            return length
        for i in range(len(word)):
            for c in 'abcdefghijklmnopqrstuvwxyz':
                newWord = word[:i] + c + word[i+1:]
                if newWord in wordSet:
                    wordSet.remove(newWord)
                    queue.append((newWord, length + 1))
    return 0
```
##### Time complexity:
O(M^2 * N)
##### Space complexity:
O(M^2 * N)
##### Notes:
1. Use BFS to find the shortest transformation sequence.
2. Use a set to store the words in the wordList for efficient lookup.
3. Generate all possible words by changing one character at a time.
4. Remove the visited words from the wordSet to avoid revisiting them.
5. Return 0 if the endWord is not in the wordSet.
1. Use a set for efficient lookup of words.
2. Use a queue for BFS traversal.
3. Generate all possible words by changing one character at a time.
4. Remove visited words from the wordSet to avoid revisiting them.
The trickiest part of this problem is generating all possible words by changing one character at a time. This can be done by iterating over each character of the word and replacing it with all possible characters.
Avoid using a recursive approach as it may lead to stack overflow for large wordLists.
    
### >> Comparison: 126 Word Ladder II [Hard] *VS* 127 Word Ladder [Medium]
> Similarity distance: 0.4535
##### Similarities

- Both 126 Word Ladder II and 127 Word Ladder are problems related to finding the shortest path between two words in a given word list.
- Both problems involve transforming one word into another by changing only one letter at a time, and each intermediate word must be a valid word in the given word list.
##### Differences

- 126 Word Ladder II requires finding all the shortest transformation sequences from the start word to the end word, while 127 Word Ladder only requires finding the length of the shortest transformation sequence.
- 126 Word Ladder II has a higher level of difficulty compared to 127 Word Ladder.
##### New Insights in 127 Word Ladder [Medium]

- Both problems can be solved using a breadth-first search (BFS) algorithm.
- In 126 Word Ladder II, we need to use a modified BFS algorithm to keep track of all the transformation sequences.
- In 127 Word Ladder, we can use a standard BFS algorithm to find the shortest transformation sequence length.


---
# 4. From 126 Word Ladder II [Hard] to 582 Kill Process [Medium]
> Similarity Distance: 0.6130

### >> Reminder: 126 Word Ladder II [Hard]
Given two words (beginWord and endWord), and a dictionary's word list, find all shortest transformation sequence(s) from beginWord to endWord, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

Note:

- Return an empty list if there is no such transformation sequence.
- All words have the same length.
- All words contain only lowercase alphabetic characters.
- You may assume no duplicates in the word list.
- You may assume beginWord and endWord are non-empty and are not the same.
##### Optimal Python solution:
```python
from collections import defaultdict, deque

def findLadders(beginWord, endWord, wordList):
    wordSet = set(wordList)
    if endWord not in wordSet:
        return []
    layer = {}  # word: [path]
    layer[beginWord] = [[beginWord]]
    while layer:
        newlayer = defaultdict(list)
        for word in layer:
            if word == endWord:
                return layer[word]
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    newWord = word[:i] + c + word[i + 1:]
                    if newWord in wordSet:
                        newlayer[newWord] += [j + [newWord] for j in layer[word]]
        wordSet -= set(newlayer.keys())
        layer = newlayer
    return []
```
Find all shortest transformation sequences from beginWord to endWord.
    
### >> 582 Kill Process [Medium]
Given n processes, each process has a unique PID (process id) and its PPID (parent process id).

Each process only has one parent process, but may have one or more children processes. This is just like a tree structure. Only one process has PPID that is 0, which means this process has no parent process. All the PIDs will be distinct positive integers.

We use two list of integers to represent two sequences of processes.

In the sequence list1, and every odd index is the PID of a process and every even index represents the corresponding PPID.

For example, the sequence [1,3,10,5] represents the process with PID = 1, PPID = 3, the process with PID = 10, PPID = 5 and so on.

We need to find the list of PIDs of all the processes that would be killed in the end. You should return the PIDs in any order.
##### Sample input:
[1,3,10,5]
[3,0,5,3]
##### Sample output:
[5,10]

##### Questions to ask to clarify requirements:
Can the input sequences be empty? Can there be cycles in the process tree?

##### Optimal Python solution:
```python
def killProcess(pid, ppid, kill):
    graph = {}
    for i in range(len(pid)):
        if ppid[i] not in graph:
            graph[ppid[i]] = []
        graph[ppid[i]].append(pid[i])
    killed = []
    stack = [kill]
    while stack:
        process = stack.pop()
        killed.append(process)
        if process in graph:
            stack.extend(graph[process])
    return killed
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Create a graph representation of the process tree using a dictionary.
2. Use a stack to perform a depth-first search starting from the kill process.
3. Append each visited process to the 'killed' list.
Use a dictionary to represent the graph.
None
None
    
### >> Comparison: 126 Word Ladder II [Hard] *VS* 582 Kill Process [Medium]
> Similarity distance: 0.6130
##### Similarities

- Both questions are related to graph traversal.
- Both questions require finding a path from one node to another.
- Both questions have a time complexity of O(N^2 * M), where N is the number of nodes and M is the average number of neighbors for each node.
##### Differences

- Word Ladder II is a harder problem compared to Kill Process.
- Word Ladder II involves finding all possible shortest paths, while Kill Process involves killing processes in a tree-like structure.
- Word Ladder II requires constructing the entire ladder, while Kill Process only requires killing processes.
- Word Ladder II uses a breadth-first search algorithm, while Kill Process uses a depth-first search algorithm.
##### New Insights in 582 Kill Process [Medium]

- Word Ladder II can be solved using a bidirectional breadth-first search to improve efficiency.
- Kill Process can be solved using a depth-first search with a hashmap to store the parent-child relationship.


---
# 5. From 126 Word Ladder II [Hard] to 323 Number of Connected Components in an Undirected Graph [Medium]
> Similarity Distance: 0.6326

### >> Reminder: 126 Word Ladder II [Hard]
Given two words (beginWord and endWord), and a dictionary's word list, find all shortest transformation sequence(s) from beginWord to endWord, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

Note:

- Return an empty list if there is no such transformation sequence.
- All words have the same length.
- All words contain only lowercase alphabetic characters.
- You may assume no duplicates in the word list.
- You may assume beginWord and endWord are non-empty and are not the same.
##### Optimal Python solution:
```python
from collections import defaultdict, deque

def findLadders(beginWord, endWord, wordList):
    wordSet = set(wordList)
    if endWord not in wordSet:
        return []
    layer = {}  # word: [path]
    layer[beginWord] = [[beginWord]]
    while layer:
        newlayer = defaultdict(list)
        for word in layer:
            if word == endWord:
                return layer[word]
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    newWord = word[:i] + c + word[i + 1:]
                    if newWord in wordSet:
                        newlayer[newWord] += [j + [newWord] for j in layer[word]]
        wordSet -= set(newlayer.keys())
        layer = newlayer
    return []
```
Find all shortest transformation sequences from beginWord to endWord.
    
### >> 323 Number of Connected Components in an Undirected Graph [Medium]
Given n nodes labeled from 0 to n - 1 and a list of undirected edges (each edge is a pair of nodes), write a function to find the number of connected components in an undirected graph.
##### Sample input:
n = 5, edges = [[0, 1], [1, 2], [3, 4]]
n = 5, edges = [[0, 1], [1, 2], [2, 3], [3, 4]]
##### Sample output:
2
1

##### Questions to ask to clarify requirements:
What is the range of n? Can there be duplicate edges? Can there be self loops?

##### Optimal Python solution:
```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        parent = [i for i in range(n)]
        def find(x):
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]
        def union(x, y):
            parent[find(x)] = find(y)
        for u, v in edges:
            union(u, v)
        return len(set(find(x) for x in range(n)))
```
##### Time complexity:
O(n + m * α(n))
##### Space complexity:
O(n)
##### Notes:
Use union find algorithm to find connected components in the graph.
Use path compression to optimize the find operation.
Use set to count the number of unique connected components.
Understand the union find algorithm and how it can be used to find connected components in a graph.
Optimize the find operation using path compression.
Use set to count the number of unique connected components.
Using path compression in the find operation to optimize the time complexity.
Using a brute force approach to find connected components by traversing the graph.
    
### >> Comparison: 126 Word Ladder II [Hard] *VS* 323 Number of Connected Components in an Undirected Graph [Medium]
> Similarity distance: 0.6326
##### Similarities

- Both questions involve finding connections between elements in a graph.
- Both questions require a graph traversal algorithm to solve.
- Both questions have a time complexity of O(V + E), where V is the number of vertices and E is the number of edges in the graph.
##### Differences

- Word Ladder II involves finding the shortest transformation sequence from a starting word to an ending word, where only one letter can be changed at a time.
- Number of Connected Components in an Undirected Graph involves finding the number of connected components in a graph.
- Word Ladder II requires the use of a breadth-first search (BFS) algorithm to find the shortest transformation sequence.
- Number of Connected Components in an Undirected Graph requires the use of a depth-first search (DFS) algorithm to find the number of connected components.
##### New Insights in 323 Number of Connected Components in an Undirected Graph [Medium]

- Word Ladder II introduces the concept of transforming one word into another by changing one letter at a time.
- Number of Connected Components in an Undirected Graph introduces the concept of connected components in a graph.


---
# 6. From 323 Number of Connected Components in an Undirected Graph [Medium] to 305 Number of Islands II [Hard]
> Similarity Distance: 0.5465

### >> Reminder: 323 Number of Connected Components in an Undirected Graph [Medium]
Given n nodes labeled from 0 to n - 1 and a list of undirected edges (each edge is a pair of nodes), write a function to find the number of connected components in an undirected graph.
##### Optimal Python solution:
```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        parent = [i for i in range(n)]
        def find(x):
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]
        def union(x, y):
            parent[find(x)] = find(y)
        for u, v in edges:
            union(u, v)
        return len(set(find(x) for x in range(n)))
```
The essence of this problem is to find the number of connected components in an undirected graph using the union find algorithm.
    
### >> 305 Number of Islands II [Hard]
Given a 2D grid of size m x n and an integer k, you need to find the number of islands in the grid after each island was expanded by k units horizontally and vertically.
##### Sample input:

- [[0,0],[0,1],[1,2],[2,1]]
- 3
- 3
- [[0,0],[0,1],[1,2],[2,1],[1,1],[0,2],[1,0],[0,3],[3,3],[2,2]]
##### Sample output:

- 1
- 1
- 2
- 3
- 4
- 3
- 3
- 3
- 2
- 1

##### Questions to ask to clarify requirements:

- What is the range of m and n?
- Can the grid be empty?
- Can the grid contain negative values?
- What is the maximum value of k?
- Can k be negative?

##### Optimal Python solution:
```python

- class Solution:
-     def numIslands2(self, m: int, n: int, positions: List[List[int]]) -> List[int]:
-         def find(x):
-             if x != parent[x]:
-                 parent[x] = find(parent[x])
-             return parent[x]
-         def union(x, y):
-             rootX, rootY = find(x), find(y)
-             if rootX != rootY:
-                 parent[rootX] = rootY
-                 self.count -= 1
-         directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
-         grid = [[0] * n for _ in range(m)]
-         parent = [i for i in range(m * n)]
-         self.count = 0
-         res = []
-         for position in positions:
-             x, y = position
-             if grid[x][y] == 1:
-                 res.append(self.count)
-                 continue
-             grid[x][y] = 1
-             self.count += 1
-             for dx, dy in directions:
-                 nx, ny = x + dx, y + dy
-                 if 0 <= nx < m and 0 <= ny < n and grid[nx][ny] == 1:
-                     union(x * n + y, nx * n + ny)
-             res.append(self.count)
-         return res
```
##### Time complexity:
O(k)
##### Space complexity:
O(m * n)
##### Notes:

- Use union find to keep track of connected islands
- Expand each island by k units horizontally and vertically
- Count the number of islands after each expansion

- Understand the union find data structure and its operations.
- Optimize the solution by avoiding unnecessary operations.
- Handle edge cases for large grids.

- Using union find to keep track of connected islands
- Expanding each island by k units horizontally and vertically

- Brute force approach of checking each cell for each expansion
    
### >> Comparison: 323 Number of Connected Components in an Undirected Graph [Medium] *VS* 305 Number of Islands II [Hard]
> Similarity distance: 0.5465
##### Similarities

- Both questions involve counting the number of connected components in a graph.
- Both questions require determining the connectivity between nodes or cells.
- Both questions can be solved using graph traversal algorithms.
##### Differences

- Question 323 deals with an undirected graph, while question 305 deals with a grid of cells.
- Question 323 uses an adjacency list representation of the graph, while question 305 uses a union-find data structure.
- Question 323 requires counting the number of connected components, while question 305 requires counting the number of islands.
- Question 323 has a medium difficulty level, while question 305 has a hard difficulty level.
##### New Insights in 305 Number of Islands II [Hard]

- Question 323: The graph can be represented using an adjacency matrix instead of an adjacency list for faster lookups.
- Question 305: The union-find data structure can be optimized using path compression and union by rank.


---
# 7. From 323 Number of Connected Components in an Undirected Graph [Medium] to 444 Sequence Reconstruction [Medium]
> Similarity Distance: 0.6493

### >> Reminder: 323 Number of Connected Components in an Undirected Graph [Medium]
Given n nodes labeled from 0 to n - 1 and a list of undirected edges (each edge is a pair of nodes), write a function to find the number of connected components in an undirected graph.
##### Optimal Python solution:
```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        parent = [i for i in range(n)]
        def find(x):
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]
        def union(x, y):
            parent[find(x)] = find(y)
        for u, v in edges:
            union(u, v)
        return len(set(find(x) for x in range(n)))
```
The essence of this problem is to find the number of connected components in an undirected graph using the union find algorithm.
    
### >> 444 Sequence Reconstruction [Medium]
Check whether the original sequence org can be uniquely reconstructed from the sequences in seqs.
##### Sample input:
[1,2,3],[[1,2],[1,3]]
##### Sample output:
false

##### Questions to ask to clarify requirements:

- What should be the output if the sequences in seqs contain duplicate elements?
- Can we assume that the sequences in seqs are valid and do not contain cycles?

##### Optimal Python solution:
```python
def sequenceReconstruction(org, seqs):
    if not seqs:
        return False
    n = len(org)
    indegree = [0] * (n + 1)
    graph = collections.defaultdict(set)
    for seq in seqs:
        if any(s > n or s < 1 for s in seq):
            return False
        for i in range(1, len(seq)):
            if seq[i] not in graph[seq[i - 1]]:
                indegree[seq[i]] += 1
                graph[seq[i - 1]].add(seq[i])
    queue = collections.deque([i for i in org if indegree[i] == 0])
    while queue:
        if len(queue) > 1:
            return False
        node = queue.popleft()
        n -= 1
        for neighbor in graph[node]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)
    return n == 0
```
##### Time complexity:
O(n + m)
##### Space complexity:
O(n + m)
##### Notes:

- Create a graph representation of the sequences using a dictionary of sets.
- Count the indegree of each node in the graph.
- Use a queue to perform a topological sort of the graph.
- Check if the resulting order matches the original sequence.

- Use a dictionary of sets to represent the graph.
- Perform a topological sort using a queue.
- Handle duplicate elements in the sequences.

- Handling duplicate elements in the sequences.
- Performing a topological sort of the graph using a queue.

- Assuming the sequences in seqs are valid and do not contain cycles.
- Modifying the input sequences in seqs without creating a copy.
    
### >> Comparison: 323 Number of Connected Components in an Undirected Graph [Medium] *VS* 444 Sequence Reconstruction [Medium]
> Similarity distance: 0.6493
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve graphs and connectivity.
- Both questions require understanding of graph traversal algorithms.
##### Differences

- Question 323 involves counting the number of connected components in an undirected graph.
- Question 444 involves reconstructing a sequence based on a set of sequences.
- Question 323 requires finding the number of connected components using graph traversal algorithms.
- Question 444 requires determining if a given sequence can be reconstructed based on a set of sequences.
##### New Insights in 444 Sequence Reconstruction [Medium]

- Question 323 teaches how to identify and count connected components in an undirected graph.
- Question 444 teaches how to reconstruct a sequence based on a set of sequences.
- Both questions provide insights into graph algorithms and their applications.


---
# 8. From 286 Walls and Gates [Medium] to 317 Shortest Distance from All Buildings [Hard]
> Similarity Distance: 0.5047

### >> Reminder: 286 Walls and Gates [Medium]
You are given a m x n 2D grid initialized with these three possible values.

-1 - A wall or an obstacle.
0 - A gate.
INF - Infinity means an empty room. We use the value 231 - 1 = 2147483647 to represent INF as you may assume that the distance to a gate is less than 2147483647.
Fill each empty room with the distance to its nearest gate. If it is impossible to reach a gate, it should be filled with INF.
##### Optimal Python solution:
```python
class Solution:
    def wallsAndGates(self, rooms: List[List[int]]) -> None:
        if not rooms:
            return
        m, n = len(rooms), len(rooms[0])
        queue = [(i, j) for i in range(m) for j in range(n) if rooms[i][j] == 0]
        for i, j in queue:
            for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                x, y = i + dx, j + dy
                if 0 <= x < m and 0 <= y < n and rooms[x][y] == INF:
                    rooms[x][y] = rooms[i][j] + 1
                    queue.append((x, y))
```
The essence of the problem is to find the distance from each empty room to the nearest gate using breadth-first search (BFS).
    
### >> 317 Shortest Distance from All Buildings [Hard]
You want to build a house on an empty land which reaches all buildings in the shortest amount of distance. You can only move up, down, left and right. You are given a 2D grid of values 0, 1 or 2, where:

- Each 0 marks an empty land which you can pass by freely.
- Each 1 marks a building which you cannot pass through.
- Each 2 marks an obstacle which you cannot pass through.

For example, given three buildings at (0,0), (0,4), (2,2), and an obstacle at (0,2):

```
1 - 0 - 2 - 0 - 1
|   |   |   |   |
0 - 0 - 0 - 0 - 0
|   |   |   |   |
0 - 0 - 1 - 0 - 0
```

The point `(1,2)` is an ideal empty land to build a house, as the total travel distance of `3 + 3 + 1 = 7` is minimal. So return `7`.
##### Sample input:
grid = [
  [1,0,2,0,1],
  [0,0,0,0,0],
  [0,0,1,0,0]
]
##### Sample output:
7

##### Questions to ask to clarify requirements:
1. Can the grid be empty?
2. Can there be no buildings?
3. Can there be no empty land?
4. Can there be no obstacles?
5. Can there be multiple optimal solutions?
6. Can the grid have irregular dimensions?

##### Optimal Python solution:
```python
def shortestDistance(self, grid):
    if not grid or not grid[0]:
        return -1
    m, n = len(grid), len(grid[0])
    buildings = sum(val for line in grid for val in line if val == 1)
    hit, distSum = [[0] * n for _ in range(m)], [[0] * n for _ in range(m)]

    def BFS(start_x, start_y):
        visited = [[False] * n for _ in range(m)]
        visited[start_x][start_y], count1, queue = True, 1, [(start_x, start_y, 0)]
        while queue:
            x, y, dist = queue.pop(0)
            for dx, dy in zip((1, 0, -1, 0), (0, 1, 0, -1)):
                if 0 <= x + dx < m and 0 <= y + dy < n and not visited[x + dx][y + dy]:
                    visited[x + dx][y + dy] = True
                    if not grid[x + dx][y + dy]:
                        queue.append((x + dx, y + dy, dist + 1))
                        hit[x + dx][y + dy] += 1
                        distSum[x + dx][y + dy] += dist + 1
                    elif grid[x + dx][y + dy] == 1:
                        count1 += 1
        return count1 == buildings

    for i in range(m):
        for j in range(n):
            if grid[i][j] == 1:
                if not BFS(i, j):
                    return -1
    return min([distSum[i][j] for i in range(m) for j in range(n) if not grid[i][j] and hit[i][j] == buildings] or [-1])
```
##### Time complexity:
O(m^2 * n^2)
##### Space complexity:
O(m * n)
##### Notes:
1. Use BFS to find the shortest distance from each building to each empty land.
2. Keep track of the number of buildings reached and the sum of distances.
3. Return the minimum sum of distances from all buildings.
1. Use a queue to implement BFS.
2. Use matrices to keep track of visited nodes and distances.
3. Handle edge cases such as empty grid or no buildings.
1. Using two matrices to keep track of the number of buildings reached and the sum of distances.
2. Checking if all buildings are reached after BFS.
1. Using a brute force approach to calculate the distance from each building to each empty land.
2. Not considering obstacles in the grid.
    
### >> Comparison: 286 Walls and Gates [Medium] *VS* 317 Shortest Distance from All Buildings [Hard]
> Similarity distance: 0.5047
##### Similarities

- Both questions involve finding the shortest distance from a source to multiple destinations.
- Both questions require traversing a grid or graph to calculate the distances.
- Both questions involve using breadth-first search (BFS) algorithm.
##### Differences

- Question 286 focuses on finding the shortest distance from each empty room (represented as '0') to the nearest gate (represented as 'INF').
- Question 317 focuses on finding the shortest distance from each building (represented as '1') to all other empty rooms (represented as '0').
- Question 286 has a single source (gate) and multiple destinations (empty rooms), while question 317 has multiple sources (buildings) and multiple destinations (empty rooms).
- Question 286 requires updating the distance of each empty room based on the distance from the nearest gate, while question 317 requires updating the distance of each empty room based on the sum of distances from all buildings.
##### New Insights in 317 Shortest Distance from All Buildings [Hard]

- Question 286 teaches us how to use BFS to find the shortest distance from a single source to multiple destinations.
- Question 317 teaches us how to use BFS to find the shortest distance from multiple sources to multiple destinations.
- Both questions provide insights into optimizing BFS by using a queue and visited set to avoid redundant calculations.

