
# Leetcode Intensive Tutorial Day 8 
> [Difficulty Score: 12]

> [Version: 20231225_200427]

## Courses overview of the day

- 506 Relative Ranks [Easy]
  - 544 Output Contest Matches [Medium]
    - 292 Nim Game [Easy]
    - 299 Bulls and Cows [Medium]
      - 277 Find the Celebrity [Medium]
      - 484 Find Permutation [Medium]
  - 406 Queue Reconstruction by Height [Medium]

#### Steps by steps

 - [1. From 506 Relative Ranks [Easy] to 544 Output Contest Matches [Medium]](#1-from-506-relative-ranks-easy-to-544-output-contest-matches-medium)

 - [2. From 544 Output Contest Matches [Medium] to 292 Nim Game [Easy]](#2-from-544-output-contest-matches-medium-to-292-nim-game-easy)

 - [3. From 544 Output Contest Matches [Medium] to 299 Bulls and Cows [Medium]](#3-from-544-output-contest-matches-medium-to-299-bulls-and-cows-medium)

 - [4. From 299 Bulls and Cows [Medium] to 277 Find the Celebrity [Medium]](#4-from-299-bulls-and-cows-medium-to-277-find-the-celebrity-medium)

 - [5. From 299 Bulls and Cows [Medium] to 484 Find Permutation [Medium]](#5-from-299-bulls-and-cows-medium-to-484-find-permutation-medium)

 - [6. From 506 Relative Ranks [Easy] to 406 Queue Reconstruction by Height [Medium]](#6-from-506-relative-ranks-easy-to-406-queue-reconstruction-by-height-medium)

#### Summary


- 506 Relative Ranks : The essence of this problem is to assign ranks to athletes based on their scores.
- 292 Nim Game : The essence of this problem is to find a winning strategy based on the number of stones in the heap.
- 406 Queue Reconstruction by Height : N/A
- 299 Bulls and Cows : Count the number of bulls and cows in the Bulls and Cows game.
- 277 Find the Celebrity : The essence of this problem is to find the celebrity in a party by checking the indegree and outdegree of each person.
- 544 Output Contest Matches : The essence of this problem is to arrange the contest matches in a binary tree structure.
- 484 Find Permutation : The essence of this problem is to reconstruct the secret signature by reversing subarrays based on the input string.
> Similarity Diameter of these problems: 0.8431


---
# 1. From 506 Relative Ranks [Easy] to 544 Output Contest Matches [Medium]
> Similarity Distance: 0.5962

### >> 506 Relative Ranks [Easy]
Given scores of athletes, return their relative ranks.
##### Sample input:

- [5, 4, 3, 2, 1]
##### Sample output:

- ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]

##### Questions to ask to clarify requirements:

- Can the scores be negative?
- Can there be ties in the scores?

##### Optimal Python solution:
```python

- from typing import List
- 
- def findRelativeRanks(nums: List[int]) -> List[str]:
-     sorted_nums = sorted(nums, reverse=True)
-     ranks = {}
-     for i, num in enumerate(sorted_nums):
-         if i == 0:
-             ranks[num] = "Gold Medal"
-         elif i == 1:
-             ranks[num] = "Silver Medal"
-         elif i == 2:
-             ranks[num] = "Bronze Medal"
-         else:
-             ranks[num] = str(i + 1)
-     return [ranks[num] for num in nums]
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:

- Sort the scores in descending order
- Assign ranks based on the sorted scores

- Sort the scores in descending order.
- Assign ranks based on the sorted scores.
- Handle ties in the scores.
- Optimize for many athletes using a priority queue or counting sort.

- Assigning ranks based on the sorted scores

- Using a nested loop to compare scores
- Using a recursive approach
    
### >> 544 Output Contest Matches [Medium]
During the NBA playoffs, we always arrange the rather strong team to play with the rather weak team, like make the rank 1 team play with the rank nth team, which is a good strategy to make the contest more interesting. Now, you're given n teams, you need to output their final contest matches in the form of a string.
##### Sample input:

- 4
##### Sample output:
"((1,4),(2,3))"

##### Questions to ask to clarify requirements:

- Can the number of teams be odd?
- Can the number of teams be zero?
- Can the number of teams be negative?

##### Optimal Python solution:
```python

- class Solution:
-     def findContestMatch(self, n: int) -> str:
-         teams = [str(i) for i in range(1, n + 1)]
-         while n > 1:
-             for i in range(n // 2):
-                 teams[i] = '(' + teams[i] + ',' + teams[n - i - 1] + ')'
-             n //= 2
-         return teams[0]
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:

- The contest matches are arranged in a binary tree structure.
- Each match consists of two teams enclosed in brackets.
- The teams are initially represented as strings.
- The solution iteratively combines the teams to form the matches.

- Use a binary tree structure to represent the contest matches.
- Iteratively combine the teams to form the matches.

- The number of teams may be odd.
- The teams are initially represented as strings.

- Using a brute force approach to generate all possible matches.
    
### >> Comparison: 506 Relative Ranks [Easy] *VS* 544 Output Contest Matches [Medium]
> Similarity distance: 0.5962
##### Similarities

- Both questions involve ranking and sorting of elements.
- Both questions require the use of arrays or lists to store and manipulate data.
- Both questions have a specific output format that needs to be followed.
##### Differences

- Question 506 involves ranking athletes based on their scores, while question 544 involves pairing teams in a contest.
- Question 506 requires assigning ranks to the athletes, while question 544 requires pairing teams in a specific order.
- Question 506 has a fixed number of athletes, while question 544 can have a variable number of teams.
##### New Insights in 544 Output Contest Matches [Medium]

- Question 506: We can use a sorting algorithm to sort the athletes' scores and assign ranks based on the sorted order.
- Question 544: We can use a recursive approach to pair the teams in a contest by dividing them into two halves and pairing the corresponding teams.


---
# 2. From 544 Output Contest Matches [Medium] to 292 Nim Game [Easy]
> Similarity Distance: 0.5430

### >> Reminder: 544 Output Contest Matches [Medium]
During the NBA playoffs, we always arrange the rather strong team to play with the rather weak team, like make the rank 1 team play with the rank nth team, which is a good strategy to make the contest more interesting. Now, you're given n teams, you need to output their final contest matches in the form of a string.
##### Optimal Python solution:
```python

- class Solution:
-     def findContestMatch(self, n: int) -> str:
-         teams = [str(i) for i in range(1, n + 1)]
-         while n > 1:
-             for i in range(n // 2):
-                 teams[i] = '(' + teams[i] + ',' + teams[n - i - 1] + ')'
-             n //= 2
-         return teams[0]
```
The essence of this problem is to arrange the contest matches in a binary tree structure.
    
### >> 292 Nim Game [Easy]
You are playing the following Nim Game with your friend:

Initially, there is a heap of stones on the table.

You and your friend will alternate taking turns, and you go first.

On each turn, the person whose turn it is will remove 1 to 3 stones from the heap.

The one who removes the last stone is the winner.

Given n, the number of stones in the heap, return true if you can win the game assuming both you and your friend play optimally, otherwise return false.


Example 1:

Input: n = 4
Output: false
Explanation: If you remove 1 stone, your friend removes 3 stones, and you remove the last stone. Your friend wins.

Example 2:

Input: n = 1
Output: true

Example 3:

Input: n = 2
Output: true


Constraints:

1 <= n <= 231 - 1

##### Sample input:
n = 4
##### Sample output:
false

##### Questions to ask to clarify requirements:
What is the maximum value of n?
Can n be negative?


##### Optimal Python solution:
```python
class Solution:
    def canWinNim(self, n: int) -> bool:
        return n % 4 != 0
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. The game is played optimally, meaning both players will make the best move.
2. The player who removes the last stone wins.
3. The player can remove 1 to 3 stones on each turn.
4. The winning strategy is to leave the opponent with a multiple of 4 stones.

1. Look for patterns and formulas in the problem to optimize the solution.
2. Use mathematical reasoning to analyze the problem.
3. Consider edge cases and constraints to ensure the solution is valid for all inputs.

The main challenge is to find the winning strategy based on the number of stones.

Avoid using a brute force approach to check all possible moves.

    
### >> Comparison: 544 Output Contest Matches [Medium] *VS* 292 Nim Game [Easy]
> Similarity distance: 0.5430
##### Similarities

- Both questions involve a game-like scenario.
- Both questions require logical thinking and strategy.
- Both questions have a clear winning condition.
##### Differences

- 544 Output Contest Matches involves arranging teams in a tournament format, while 292 Nim Game involves a simple game of removing stones.
- 544 Output Contest Matches requires arranging teams in a specific order, while 292 Nim Game requires finding a winning strategy.
- 544 Output Contest Matches has a time complexity of O(nlogn), while 292 Nim Game has a time complexity of O(1).
##### New Insights in 292 Nim Game [Easy]

- 544 Output Contest Matches teaches us how to arrange teams in a tournament format efficiently.
- 292 Nim Game teaches us how to find a winning strategy in a game scenario.
- Both questions teach us how to approach game-like scenarios with logical thinking and strategy.


---
# 3. From 544 Output Contest Matches [Medium] to 299 Bulls and Cows [Medium]
> Similarity Distance: 0.6933

### >> Reminder: 544 Output Contest Matches [Medium]
During the NBA playoffs, we always arrange the rather strong team to play with the rather weak team, like make the rank 1 team play with the rank nth team, which is a good strategy to make the contest more interesting. Now, you're given n teams, you need to output their final contest matches in the form of a string.
##### Optimal Python solution:
```python

- class Solution:
-     def findContestMatch(self, n: int) -> str:
-         teams = [str(i) for i in range(1, n + 1)]
-         while n > 1:
-             for i in range(n // 2):
-                 teams[i] = '(' + teams[i] + ',' + teams[n - i - 1] + ')'
-             n //= 2
-         return teams[0]
```
The essence of this problem is to arrange the contest matches in a binary tree structure.
    
### >> 299 Bulls and Cows [Medium]
You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.
##### Sample input:
"1807"
"7810"
##### Sample output:
"1A3B"

##### Questions to ask to clarify requirements:
Can the secret and guess have duplicate digits? Can the secret and guess have different lengths?

##### Optimal Python solution:
```python
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls = 0
        cows = 0
        secret_count = [0] * 10
        guess_count = [0] * 10
        for i in range(len(secret)):
            s = int(secret[i])
            g = int(guess[i])
            if s == g:
                bulls += 1
            else:
                secret_count[s] += 1
                guess_count[g] += 1
        for i in range(10):
            cows += min(secret_count[i], guess_count[i])
        return str(bulls) + 'A' + str(cows) + 'B'
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use two arrays to count the occurrences of each digit in secret and guess.
Count the number of bulls by comparing the digits in the same position.
Count the number of cows by comparing the total occurrences of each digit.
Use arrays to count occurrences of each digit.
Iterate through the arrays to count the number of bulls and cows.
Handle the case when the secret and guess have different lengths.
None
None
    
### >> Comparison: 544 Output Contest Matches [Medium] *VS* 299 Bulls and Cows [Medium]
> Similarity distance: 0.6933
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve string manipulation and comparison.
- Both questions require the use of loops and conditional statements.
- Both questions have a specific output format.
##### Differences

- 544 Output Contest Matches involves arranging and merging strings in a specific pattern, while 299 Bulls and Cows involves counting and comparing characters in a string.
- 544 Output Contest Matches requires the use of recursion, while 299 Bulls and Cows does not.
- 544 Output Contest Matches has a time complexity of O(nlogn), while 299 Bulls and Cows has a time complexity of O(n).
- 544 Output Contest Matches has a space complexity of O(n), while 299 Bulls and Cows has a space complexity of O(1).
##### New Insights in 299 Bulls and Cows [Medium]

- 544 Output Contest Matches teaches the concept of recursive string manipulation.
- 299 Bulls and Cows teaches the concept of character counting and comparison.
- Both questions provide practice in implementing efficient algorithms for string manipulation and comparison.


---
# 4. From 299 Bulls and Cows [Medium] to 277 Find the Celebrity [Medium]
> Similarity Distance: 0.6758

### >> Reminder: 299 Bulls and Cows [Medium]
You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.
##### Optimal Python solution:
```python
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls = 0
        cows = 0
        secret_count = [0] * 10
        guess_count = [0] * 10
        for i in range(len(secret)):
            s = int(secret[i])
            g = int(guess[i])
            if s == g:
                bulls += 1
            else:
                secret_count[s] += 1
                guess_count[g] += 1
        for i in range(10):
            cows += min(secret_count[i], guess_count[i])
        return str(bulls) + 'A' + str(cows) + 'B'
```
Count the number of bulls and cows in the Bulls and Cows game.
    
### >> 277 Find the Celebrity [Medium]
In a party of N people, only one person is known to everyone. Such a person may be present in the party, if yes, (s)he doesn’t know anyone in the party. We can only ask questions like “does A know B?”. Find the stranger (celebrity) in minimum number of questions.
##### Sample input:
4
[[1, 0], [1, 2], [3, 0], [3, 2]]
##### Sample output:
Celebrity ID is: 0

##### Questions to ask to clarify requirements:
1. Can we assume that there is only one celebrity in the party?
2. Can we assume that the input is always valid?
3. Can we assume that the knows() function is provided?
4. What should be the output if there is no celebrity in the party?

##### Optimal Python solution:
```python
def findCelebrity(n):
    indegree = [0] * n
    outdegree = [0] * n
    for i in range(n):
        for j in range(n):
            if knows(i, j):
                outdegree[i] += 1
                indegree[j] += 1
    for i in range(n):
        if indegree[i] == n - 1 and outdegree[i] == 0:
            return i
    return -1
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. A celebrity is a person who is known to everyone, but doesn't know anyone.
2. We can find the celebrity by checking the indegree and outdegree of each person.
3. If a person has indegree n-1 and outdegree 0, then (s)he is the celebrity.
4. If there is no celebrity, return -1.
1. Use a stack to optimize the solution.
2. Use a two-pointer approach to optimize the solution.
3. Handle the case when there is no celebrity in the party.
1. We can optimize the solution by using a stack.
2. We can optimize the solution by using a two-pointer approach.
1. Avoid using a brute-force approach to check all pairs of people.
2. Avoid using a graph traversal algorithm without optimizing it.
    
### >> Comparison: 299 Bulls and Cows [Medium] *VS* 277 Find the Celebrity [Medium]
> Similarity distance: 0.6758
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding a specific element in a given set of elements.
- Both questions require logical thinking and problem-solving skills.
##### Differences

- 299 Bulls and Cows: In this question, the player tries to guess a secret number based on hints provided by the game. The hints include the number of bulls (correct digits in the correct position) and cows (correct digits in the wrong position). The goal is to find the secret number within a limited number of attempts.
- 277 Find the Celebrity: In this question, there is a group of people, and each person knows a list of other people. However, there is one person who is known by everyone else but does not know anyone. The task is to find this celebrity using the minimum number of API calls that can determine if one person knows another.
##### New Insights in 277 Find the Celebrity [Medium]

- 299 Bulls and Cows: This question introduces the concept of using hints to narrow down the possibilities and find the correct answer efficiently. It also requires understanding and implementing the game logic.
- 277 Find the Celebrity: This question introduces the concept of finding a specific element (the celebrity) in a given set of elements using a limited number of API calls. It requires understanding the relationships between the people and optimizing the number of calls made.


---
# 5. From 299 Bulls and Cows [Medium] to 484 Find Permutation [Medium]
> Similarity Distance: 0.6935

### >> Reminder: 299 Bulls and Cows [Medium]
You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.
##### Optimal Python solution:
```python
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls = 0
        cows = 0
        secret_count = [0] * 10
        guess_count = [0] * 10
        for i in range(len(secret)):
            s = int(secret[i])
            g = int(guess[i])
            if s == g:
                bulls += 1
            else:
                secret_count[s] += 1
                guess_count[g] += 1
        for i in range(10):
            cows += min(secret_count[i], guess_count[i])
        return str(bulls) + 'A' + str(cows) + 'B'
```
Count the number of bulls and cows in the Bulls and Cows game.
    
### >> 484 Find Permutation [Medium]
By now, you are given a secret signature consisting of character 'D' and 'I'. 'D' represents a decreasing relationship between two numbers, 'I' represents an increasing relationship between two numbers. And our secret signature was constructed by a special integer array, which contains uniquely all the different number from 1 to n (n is the length of the secret signature plus 1). Your job is to reconstruct the secret signature by reading from the secret input array.
##### Sample input:
["DIDIDIDID"]
##### Sample output:
[4, 3, 2, 1, 6, 5, 8, 7, 9]

##### Questions to ask to clarify requirements:
Can the input string be empty? Can the input string contain characters other than 'D' and 'I'?

##### Optimal Python solution:
```python
def findPermutation(s: str) -> List[int]:
    n = len(s) + 1
    result = list(range(1, n + 1))
    i = 0
    while i < n - 1:
        if s[i] == 'D':
            j = i
            while i < n - 1 and s[i] == 'D':
                i += 1
            result[j:i+1] = reversed(result[j:i+1])
        else:
            i += 1
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. The secret signature is constructed by a special integer array.
2. The length of the secret signature is n-1, where n is the length of the input string plus 1.
3. The secret signature can be reconstructed by iterating through the input string and reversing the subarrays when encountering 'D'.
Use the reversed() function to reverse subarrays.
Use list slicing to update subarrays.
Reversing subarrays when encountering 'D'.
Avoid using additional data structures.
    
### >> Comparison: 299 Bulls and Cows [Medium] *VS* 484 Find Permutation [Medium]
> Similarity distance: 0.6935
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve string manipulation.
- Both questions require finding patterns or permutations.
- Both questions involve guessing and checking.
##### Differences

- Bulls and Cows focuses on guessing a secret number based on hints.
- Find Permutation focuses on finding a permutation based on a given string.
##### New Insights in 484 Find Permutation [Medium]

- Bulls and Cows teaches logical deduction and elimination.
- Find Permutation teaches the concept of lexicographical order.


---
# 6. From 506 Relative Ranks [Easy] to 406 Queue Reconstruction by Height [Medium]
> Similarity Distance: 0.6213

### >> Reminder: 506 Relative Ranks [Easy]
Given scores of athletes, return their relative ranks.
##### Optimal Python solution:
```python

- from typing import List
- 
- def findRelativeRanks(nums: List[int]) -> List[str]:
-     sorted_nums = sorted(nums, reverse=True)
-     ranks = {}
-     for i, num in enumerate(sorted_nums):
-         if i == 0:
-             ranks[num] = "Gold Medal"
-         elif i == 1:
-             ranks[num] = "Silver Medal"
-         elif i == 2:
-             ranks[num] = "Bronze Medal"
-         else:
-             ranks[num] = str(i + 1)
-     return [ranks[num] for num in nums]
```
The essence of this problem is to assign ranks to athletes based on their scores.
    
### >> 406 Queue Reconstruction by Height [Medium]
Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers (h, k), where h is the height of the person and k is the number of people in front of this person who have a height greater than or equal to h. Write an algorithm to reconstruct the queue.
##### Sample input:
[[7,0],[4,4],[7,1],[5,0],[6,1],[5,2]]
##### Sample output:
[[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]]

##### Questions to ask to clarify requirements:
Should the output be sorted in any specific order? Can there be duplicate heights?

##### Optimal Python solution:
```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        people.sort(key=lambda x: (-x[0], x[1]))
        queue = []
        for p in people:
            queue.insert(p[1], p)
        return queue
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Sort the people in descending order of height and ascending order of k
2. Insert each person into the queue at the index specified by k
Use sorting to order the elements. Avoid nested loops for insertion.
Sorting the people based on height and k
Using nested loops for insertion
    
### >> Comparison: 506 Relative Ranks [Easy] *VS* 406 Queue Reconstruction by Height [Medium]
> Similarity distance: 0.6213
##### Similarities

- Both questions involve sorting and rearranging elements based on certain criteria.
##### Differences

- 506 Relative Ranks is an easy level question, while 406 Queue Reconstruction by Height is a medium level question.
- In 506 Relative Ranks, the elements are integers representing scores, while in 406 Queue Reconstruction by Height, the elements are pairs of integers representing people's heights and the number of people in front of them.
- In 506 Relative Ranks, the output should be the ranking of each score, while in 406 Queue Reconstruction by Height, the output should be the reconstructed queue based on the given heights and number of people in front of each person.
##### New Insights in 406 Queue Reconstruction by Height [Medium]

- From 506 Relative Ranks, we can learn how to use sorting algorithms to rank elements and assign appropriate labels to them.
- From 406 Queue Reconstruction by Height, we can learn how to use sorting algorithms to rearrange elements based on multiple criteria and reconstruct a specific order.

