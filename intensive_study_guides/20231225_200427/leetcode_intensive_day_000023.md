
# Leetcode Intensive Tutorial Day 23 
> [Difficulty Score: 16]

> [Version: 20231225_200427]

## Courses overview of the day

- 290 Word Pattern [Easy]
  - 205 Isomorphic Strings [Easy]
  - 524 Longest Word in Dictionary through Deleting [Medium]
    - 30 Substring with Concatenation of All Words [Hard]
      - 438 Find All Anagrams in a String [Medium]
        - 76 Minimum Window Substring [Hard]
        - 28 Implement strStr() [Easy]
  - 246 Strobogrammatic Number [Easy]

#### Steps by steps

 - [1. From 290 Word Pattern [Easy] to 205 Isomorphic Strings [Easy]](#1-from-290-word-pattern-easy-to-205-isomorphic-strings-easy)

 - [2. From 290 Word Pattern [Easy] to 524 Longest Word in Dictionary through Deleting [Medium]](#2-from-290-word-pattern-easy-to-524-longest-word-in-dictionary-through-deleting-medium)

 - [3. From 524 Longest Word in Dictionary through Deleting [Medium] to 30 Substring with Concatenation of All Words [Hard]](#3-from-524-longest-word-in-dictionary-through-deleting-medium-to-30-substring-with-concatenation-of-all-words-hard)

 - [4. From 30 Substring with Concatenation of All Words [Hard] to 438 Find All Anagrams in a String [Medium]](#4-from-30-substring-with-concatenation-of-all-words-hard-to-438-find-all-anagrams-in-a-string-medium)

 - [5. From 438 Find All Anagrams in a String [Medium] to 76 Minimum Window Substring [Hard]](#5-from-438-find-all-anagrams-in-a-string-medium-to-76-minimum-window-substring-hard)

 - [6. From 438 Find All Anagrams in a String [Medium] to 28 Implement strStr() [Easy]](#6-from-438-find-all-anagrams-in-a-string-medium-to-28-implement-strstr-easy)

 - [7. From 290 Word Pattern [Easy] to 246 Strobogrammatic Number [Easy]](#7-from-290-word-pattern-easy-to-246-strobogrammatic-number-easy)

#### Summary


- 290 Word Pattern : The essence of this problem is to check if there is a consistent mapping between the pattern and words. This can be achieved by splitting the string into words and using dictionaries to store the mapping.
- 76 Minimum Window Substring : Find the minimum window substring in the input string s that contains all the characters in the target string t.
- 28 Implement strStr() : Find the index of the first occurrence of a substring in a string.
- 438 Find All Anagrams in a String : The essence of this problem is to find anagrams in a string using a sliding window approach.
- 30 Substring with Concatenation of All Words : Find all starting indices of substrings that are a concatenation of each word in the array.
- 246 Strobogrammatic Number : Determining if a number is strobogrammatic
- 205 Isomorphic Strings : The essence of this problem is to check if two strings are isomorphic, i.e., if the characters in one string can be replaced by characters in the other string while preserving the order.
- 524 Longest Word in Dictionary through Deleting : The essence of the problem is to find the longest word in the dictionary that is a subsequence of the given string and has the smallest lexicographical order.
> Similarity Diameter of these problems: 0.6825


---
# 1. From 290 Word Pattern [Easy] to 205 Isomorphic Strings [Easy]
> Similarity Distance: 0.4340

### >> 290 Word Pattern [Easy]
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Example 1:

Input: pattern = "abba", str = "dog cat cat dog"
Output: true

Example 2:

Input:pattern = "abba", str = "dog cat cat fish"
Output: false

Example 3:

Input: pattern = "aaaa", str = "dog cat cat dog"
Output: false

Example 4:

Input: pattern = "abba", str = "dog dog dog dog"
Output: false

Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters that may be separated by a single space.
##### Sample input:
"abba", "dog cat cat dog"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the pattern and string contain special characters or numbers? Can the string contain multiple spaces between words?

##### Optimal Python solution:
```python
def wordPattern(pattern, str):
    words = str.split()
    if len(pattern) != len(words):
        return False
    pattern_to_word = {}
    word_to_pattern = {}
    for p, w in zip(pattern, words):
        if p in pattern_to_word and pattern_to_word[p] != w:
            return False
        if w in word_to_pattern and word_to_pattern[w] != p:
            return False
        pattern_to_word[p] = w
        word_to_pattern[w] = p
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Split the string into words.
2. Check if the lengths of the pattern and words are equal.
3. Use two dictionaries to store the mapping between the pattern and words.
4. Check if the mapping is consistent.
1. Split the string into words.
2. Use dictionaries to store the mapping between the pattern and words.
3. Check if the mapping is consistent by comparing the values in the dictionaries.
The tricky part of this problem is checking if the mapping between the pattern and words is consistent. We can use two dictionaries to store the mapping and check if the mapping is consistent.
Avoid using nested loops to check the consistency of the mapping between the pattern and words.
    
### >> 205 Isomorphic Strings [Easy]
Given two strings s and t, determine if they are isomorphic.
##### Sample input:
"egg", "add"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Are the strings case-sensitive? Can we assume that the input strings only contain ASCII characters?

##### Optimal Python solution:
```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        mapping_s = {}
        mapping_t = {}
        for i in range(len(s)):
            if s[i] in mapping_s:
                if mapping_s[s[i]] != t[i]:
                    return False
            else:
                mapping_s[s[i]] = t[i]
            if t[i] in mapping_t:
                if mapping_t[t[i]] != s[i]:
                    return False
            else:
                mapping_t[t[i]] = s[i]
        return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Check if the lengths of the two strings are equal.
2. Create two dictionaries to map characters from s to t and from t to s.
3. Iterate through the strings and check if the mappings are consistent.
4. Return True if all characters are mapped correctly, False otherwise.
Use dictionaries to efficiently map characters between the two strings.
None
None
    
### >> Comparison: 290 Word Pattern [Easy] *VS* 205 Isomorphic Strings [Easy]
> Similarity distance: 0.4340
##### Similarities

- Both questions involve pattern matching between a string and a pattern.
- Both questions have a similar approach to solving the problem.
##### Differences

- In Word Pattern, the pattern is a string of characters, while in Isomorphic Strings, the pattern is a mapping between characters.
- Word Pattern requires the pattern to be unique, while Isomorphic Strings allows multiple characters to be mapped to the same character.
- Word Pattern requires the pattern to be consistent, while Isomorphic Strings allows the pattern to be non-consistent.
##### New Insights in 205 Isomorphic Strings [Easy]

- Word Pattern can be solved by using a hashmap to store the mapping between characters and words.
- Isomorphic Strings can be solved by using two hashmaps to store the mapping between characters in both strings.


---
# 2. From 290 Word Pattern [Easy] to 524 Longest Word in Dictionary through Deleting [Medium]
> Similarity Distance: 0.4618

### >> Reminder: 290 Word Pattern [Easy]
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Example 1:

Input: pattern = "abba", str = "dog cat cat dog"
Output: true

Example 2:

Input:pattern = "abba", str = "dog cat cat fish"
Output: false

Example 3:

Input: pattern = "aaaa", str = "dog cat cat dog"
Output: false

Example 4:

Input: pattern = "abba", str = "dog dog dog dog"
Output: false

Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters that may be separated by a single space.
##### Optimal Python solution:
```python
def wordPattern(pattern, str):
    words = str.split()
    if len(pattern) != len(words):
        return False
    pattern_to_word = {}
    word_to_pattern = {}
    for p, w in zip(pattern, words):
        if p in pattern_to_word and pattern_to_word[p] != w:
            return False
        if w in word_to_pattern and word_to_pattern[w] != p:
            return False
        pattern_to_word[p] = w
        word_to_pattern[w] = p
    return True
```
The essence of this problem is to check if there is a consistent mapping between the pattern and words. This can be achieved by splitting the string into words and using dictionaries to store the mapping.
    
### >> 524 Longest Word in Dictionary through Deleting [Medium]
Given a string and a string dictionary, find the longest string in the dictionary that can be formed by deleting some characters of the given string. If there are multiple possible results, return the longest word with the smallest lexicographical order.
##### Sample input:
"abpcleat", ["ale","apple","monkey","plea"]
##### Sample output:
"apple"

##### Questions to ask to clarify requirements:

- Can the given string and the strings in the dictionary contain special characters?
- Can the given string and the strings in the dictionary be empty?
- Can the dictionary contain duplicate words?

##### Optimal Python solution:
```python
def findLongestWord(s, d):
    longest_word = ""
    for word in d:
        if len(word) < len(longest_word) or (len(word) == len(longest_word) and word > longest_word):
            continue
        if is_subsequence(word, s):
            longest_word = word
    return longest_word

def is_subsequence(word, s):
    i = 0
    j = 0
    while i < len(word) and j < len(s):
        if word[i] == s[j]:
            i += 1
        j += 1
    return i == len(word)
```
##### Time complexity:
O(n * m)
##### Space complexity:
O(1)
##### Notes:

- Iterate through the dictionary and check if each word is a subsequence of the given string.
- Keep track of the longest word found so far.
- If two words have the same length, choose the lexicographically smaller one.

- Use two pointers to match the characters of the word and the given string.
- Keep track of the longest word found so far and choose the lexicographically smaller one if two words have the same length.

- Handling the case when the given string or the dictionary is empty.
- Handling duplicate words in the dictionary.

- Sorting the dictionary to find the lexicographically smallest word.
    
### >> Comparison: 290 Word Pattern [Easy] *VS* 524 Longest Word in Dictionary through Deleting [Medium]
> Similarity distance: 0.4618
##### Similarities

- Both questions involve pattern matching.
- Both questions require comparing strings.
- Both questions have a target string to match against.
##### Differences

- Word Pattern involves matching a pattern to a string, while Longest Word in Dictionary through Deleting involves finding the longest word in a dictionary that can be formed by deleting characters from a string.
- Word Pattern has a fixed pattern and a variable string, while Longest Word in Dictionary through Deleting has a fixed string and a variable dictionary.
- Word Pattern requires matching individual characters, while Longest Word in Dictionary through Deleting requires matching substrings.
##### New Insights in 524 Longest Word in Dictionary through Deleting [Medium]

- Word Pattern teaches us how to match a pattern to a string using a hashmap.
- Longest Word in Dictionary through Deleting teaches us how to find the longest word in a dictionary that can be formed by deleting characters from a string using two pointers.


---
# 3. From 524 Longest Word in Dictionary through Deleting [Medium] to 30 Substring with Concatenation of All Words [Hard]
> Similarity Distance: 0.5048

### >> Reminder: 524 Longest Word in Dictionary through Deleting [Medium]
Given a string and a string dictionary, find the longest string in the dictionary that can be formed by deleting some characters of the given string. If there are multiple possible results, return the longest word with the smallest lexicographical order.
##### Optimal Python solution:
```python
def findLongestWord(s, d):
    longest_word = ""
    for word in d:
        if len(word) < len(longest_word) or (len(word) == len(longest_word) and word > longest_word):
            continue
        if is_subsequence(word, s):
            longest_word = word
    return longest_word

def is_subsequence(word, s):
    i = 0
    j = 0
    while i < len(word) and j < len(s):
        if word[i] == s[j]:
            i += 1
        j += 1
    return i == len(word)
```
The essence of the problem is to find the longest word in the dictionary that is a subsequence of the given string and has the smallest lexicographical order.
    
### >> 30 Substring with Concatenation of All Words [Hard]
You are given a string s and an array of strings words of the same length. Return all starting indices of substring(s) in s that is a concatenation of each word in words exactly once, in any order, and without any intervening characters.
##### Sample input:
"barfoothefoobarman"
["foo","bar"]
##### Sample output:
[0,9]

##### Questions to ask to clarify requirements:
Can the words in the array be empty? Can the string s be empty? Can the words in the array contain duplicates?

##### Optimal Python solution:
```python
from collections import Counter
def findSubstring(s: str, words: List[str]) -> List[int]:
    if not s or not words:
        return []
    word_len = len(words[0])
    total_len = len(words) * word_len
    word_count = Counter(words)
    result = []
    for i in range(len(s) - total_len + 1):
        substring = s[i:i+total_len]
        substring_count = Counter([substring[j:j+word_len] for j in range(0, total_len, word_len)])
        if substring_count == word_count:
            result.append(i)
    return result
```
##### Time complexity:
O(n * m * k)
##### Space complexity:
O(m * k)
##### Notes:
1. Use a sliding window approach to iterate through the string.
2. Use a hash table to store the count of each word in the array.
3. Check if the count of each word in the current substring matches the count in the hash table.
4. If the counts match, add the starting index of the substring to the result list.
1. Use a sliding window approach to iterate through the string.
2. Use a hash table to store the count of each word in the array.
3. Check if the count of each word in the current substring matches the count in the hash table.
4. If the counts match, add the starting index of the substring to the result list.
Handling duplicates in the words array.
Using nested loops to check the count of each word in the substring.
    
### >> Comparison: 524 Longest Word in Dictionary through Deleting [Medium] *VS* 30 Substring with Concatenation of All Words [Hard]
> Similarity distance: 0.5048
##### Similarities

- Both questions involve string manipulation and searching for substrings.
- Both questions require finding a specific pattern within a given string.
##### Differences

- 524 Longest Word in Dictionary through Deleting focuses on finding the longest word in a dictionary that can be formed by deleting characters from a given string.
- 30 Substring with Concatenation of All Words focuses on finding all the starting indices of substrings in a given string that are a concatenation of all the words in a given list.
##### New Insights in 30 Substring with Concatenation of All Words [Hard]

- 524 Longest Word in Dictionary through Deleting teaches us how to efficiently search for substrings and compare them with words in a dictionary.
- 30 Substring with Concatenation of All Words teaches us how to use sliding window technique to efficiently search for concatenated substrings.


---
# 4. From 30 Substring with Concatenation of All Words [Hard] to 438 Find All Anagrams in a String [Medium]
> Similarity Distance: 0.4911

### >> Reminder: 30 Substring with Concatenation of All Words [Hard]
You are given a string s and an array of strings words of the same length. Return all starting indices of substring(s) in s that is a concatenation of each word in words exactly once, in any order, and without any intervening characters.
##### Optimal Python solution:
```python
from collections import Counter
def findSubstring(s: str, words: List[str]) -> List[int]:
    if not s or not words:
        return []
    word_len = len(words[0])
    total_len = len(words) * word_len
    word_count = Counter(words)
    result = []
    for i in range(len(s) - total_len + 1):
        substring = s[i:i+total_len]
        substring_count = Counter([substring[j:j+word_len] for j in range(0, total_len, word_len)])
        if substring_count == word_count:
            result.append(i)
    return result
```
Find all starting indices of substrings that are a concatenation of each word in the array.
    
### >> 438 Find All Anagrams in a String [Medium]
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s. Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100. The order of output does not matter.
##### Sample input:
"cbaebabacd"
"abc"
##### Sample output:
[0, 6]

##### Questions to ask to clarify requirements:
Can the input strings contain special characters or uppercase letters? Can the anagrams be overlapping?

##### Optimal Python solution:
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        result = []
        p_count = Counter(p)
        s_count = Counter(s[:len(p)-1])
        for i in range(len(p)-1, len(s)):
            s_count[s[i]] += 1
            if s_count == p_count:
                result.append(i-len(p)+1)
            s_count[s[i-len(p)+1]] -= 1
            if s_count[s[i-len(p)+1]] == 0:
                del s_count[s[i-len(p)+1]]
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a sliding window approach to find anagrams.
2. Use the Counter class from the collections module to count the occurrences of characters in the strings.
3. Compare the counts of characters in the sliding window with the counts of characters in the target string.
4. Move the sliding window one character at a time and update the counts of characters.
5. Return the start indices of the anagrams found.
Use the Counter class from the collections module to count the occurrences of characters in the strings.
The anagrams can be overlapping.
Avoid using a brute force approach that checks all possible substrings.
    
### >> Comparison: 30 Substring with Concatenation of All Words [Hard] *VS* 438 Find All Anagrams in a String [Medium]
> Similarity distance: 0.4911
##### Similarities

- Both questions involve finding substrings in a given string.
- Both questions require checking for anagrams or permutations of a set of words.
##### Differences

- Question 30 is a harder problem compared to question 438.
- Question 30 requires finding substrings that are concatenations of all words in a given list, while question 438 requires finding all anagrams of a given pattern in a string.
- Question 30 has a time complexity of O(n^2), while question 438 has a time complexity of O(n).
##### New Insights in 438 Find All Anagrams in a String [Medium]

- Question 30 introduces the concept of concatenating words to form substrings.
- Question 438 introduces the concept of finding anagrams in a string using a sliding window approach.


---
# 5. From 438 Find All Anagrams in a String [Medium] to 76 Minimum Window Substring [Hard]
> Similarity Distance: 0.4316

### >> Reminder: 438 Find All Anagrams in a String [Medium]
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s. Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100. The order of output does not matter.
##### Optimal Python solution:
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        result = []
        p_count = Counter(p)
        s_count = Counter(s[:len(p)-1])
        for i in range(len(p)-1, len(s)):
            s_count[s[i]] += 1
            if s_count == p_count:
                result.append(i-len(p)+1)
            s_count[s[i-len(p)+1]] -= 1
            if s_count[s[i-len(p)+1]] == 0:
                del s_count[s[i-len(p)+1]]
        return result
```
The essence of this problem is to find anagrams in a string using a sliding window approach.
    
### >> 76 Minimum Window Substring [Hard]
Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window in s that covers all characters in t, return the empty string "".
##### Sample input:
{"s": "ADOBECODEBANC", "t": "ABC"}
##### Sample output:
"BANC"

##### Questions to ask to clarify requirements:

- Can the input strings contain uppercase and lowercase letters?
- Can the input strings contain special characters?

##### Optimal Python solution:
```python
from collections import Counter

def minWindow(s, t):
    if len(s) < len(t):
        return ""
    target_counts = Counter(t)
    window_counts = Counter()
    left = 0
    min_window = ""
    min_length = float('inf')
    for right in range(len(s)):
        window_counts[s[right]] += 1
        while all(window_counts[char] >= target_counts[char] for char in target_counts):
            if right - left + 1 < min_length:
                min_window = s[left:right+1]
                min_length = right - left + 1
            window_counts[s[left]] -= 1
            if window_counts[s[left]] == 0:
                del window_counts[s[left]]
            left += 1
    return min_window
```
##### Time complexity:
O(n)
##### Space complexity:
O(m)
##### Notes:

- Use a sliding window approach to find the minimum window substring
- Use two pointers to maintain the window boundaries
- Use a dictionary to keep track of the character counts in the window and the target substring

- Use a dictionary to keep track of the character counts in the window and the target substring

- Handling the window boundaries correctly
- Updating the character counts in the window and the target substring

- Brute force approach with nested loops
    
### >> Comparison: 438 Find All Anagrams in a String [Medium] *VS* 76 Minimum Window Substring [Hard]
> Similarity distance: 0.4316
##### Similarities

- Both questions involve finding substrings in a given string.
- Both questions require checking for anagrams or matching characters in the substring.
- Both questions have a sliding window approach to solve the problem.
##### Differences

- Question 438 focuses on finding all anagrams of a given string, while question 76 focuses on finding the minimum window substring.
- Question 438 requires finding all the anagrams, while question 76 requires finding the minimum window substring that contains all the characters of a given pattern.
- Question 438 has a complexity of O(n), while question 76 has a complexity of O(n+m), where n is the length of the string and m is the length of the pattern.
##### New Insights in 76 Minimum Window Substring [Hard]

- Both questions can be solved using a sliding window approach.
- Both questions require maintaining a window of characters and updating it based on certain conditions.
- Both questions involve using a hashmap or an array to keep track of the characters and their frequencies in the window.
- Both questions require checking if the window satisfies the required conditions and updating the window accordingly.


---
# 6. From 438 Find All Anagrams in a String [Medium] to 28 Implement strStr() [Easy]
> Similarity Distance: 0.4716

### >> Reminder: 438 Find All Anagrams in a String [Medium]
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s. Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100. The order of output does not matter.
##### Optimal Python solution:
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        result = []
        p_count = Counter(p)
        s_count = Counter(s[:len(p)-1])
        for i in range(len(p)-1, len(s)):
            s_count[s[i]] += 1
            if s_count == p_count:
                result.append(i-len(p)+1)
            s_count[s[i-len(p)+1]] -= 1
            if s_count[s[i-len(p)+1]] == 0:
                del s_count[s[i-len(p)+1]]
        return result
```
The essence of this problem is to find anagrams in a string using a sliding window approach.
    
### >> 28 Implement strStr() [Easy]
Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
##### Sample input:
"hello"
"ll"
##### Sample output:
2

##### Questions to ask to clarify requirements:
Can the haystack or needle be empty? Can the needle be longer than the haystack?

##### Optimal Python solution:
```python
def strStr(haystack, needle):
    if needle == "":
        return 0
    for i in range(len(haystack) - len(needle) + 1):
        if haystack[i:i+len(needle)] == needle:
            return i
    return -1
```
##### Time complexity:
O(n*m)
##### Space complexity:
O(1)
##### Notes:
Use a sliding window to check if each substring of the haystack matches the needle.
Make sure to handle edge cases such as an empty haystack or needle.
None
None
    
### >> Comparison: 438 Find All Anagrams in a String [Medium] *VS* 28 Implement strStr() [Easy]
> Similarity distance: 0.4716
##### Similarities

- Both questions involve string manipulation.
- Both questions require finding patterns in a string.
##### Differences

- Question 438 focuses on finding all anagrams of a given string, while question 28 focuses on finding the first occurrence of a substring in a given string.
- Question 438 has a medium difficulty level, while question 28 has an easy difficulty level.
- Question 438 requires a more advanced algorithm to solve efficiently, while question 28 can be solved using basic string manipulation techniques.
##### New Insights in 28 Implement strStr() [Easy]

- Question 438 teaches us how to efficiently find all anagrams of a string using a sliding window technique.
- Question 28 teaches us how to implement a basic substring search algorithm using two pointers.


---
# 7. From 290 Word Pattern [Easy] to 246 Strobogrammatic Number [Easy]
> Similarity Distance: 0.5694

### >> Reminder: 290 Word Pattern [Easy]
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Example 1:

Input: pattern = "abba", str = "dog cat cat dog"
Output: true

Example 2:

Input:pattern = "abba", str = "dog cat cat fish"
Output: false

Example 3:

Input: pattern = "aaaa", str = "dog cat cat dog"
Output: false

Example 4:

Input: pattern = "abba", str = "dog dog dog dog"
Output: false

Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters that may be separated by a single space.
##### Optimal Python solution:
```python
def wordPattern(pattern, str):
    words = str.split()
    if len(pattern) != len(words):
        return False
    pattern_to_word = {}
    word_to_pattern = {}
    for p, w in zip(pattern, words):
        if p in pattern_to_word and pattern_to_word[p] != w:
            return False
        if w in word_to_pattern and word_to_pattern[w] != p:
            return False
        pattern_to_word[p] = w
        word_to_pattern[w] = p
    return True
```
The essence of this problem is to check if there is a consistent mapping between the pattern and words. This can be achieved by splitting the string into words and using dictionaries to store the mapping.
    
### >> 246 Strobogrammatic Number [Easy]
A strobogrammatic number is a number that looks the same when rotated 180 degrees (looked at upside down). Write a function to determine if a number is strobogrammatic. The number is represented as a string.
##### Sample input:
num = "69"
##### Sample output:
Output: true

##### Questions to ask to clarify requirements:

- Can the number contain leading zeros?
- Can the number be an empty string?

##### Optimal Python solution:
```python
def isStrobogrammatic(num):
    strobogrammatic_map = {
        '0': '0',
        '1': '1',
        '6': '9',
        '8': '8',
        '9': '6'
    }
    left = 0
    right = len(num) - 1
    while left <= right:
        if num[left] not in strobogrammatic_map or num[right] != strobogrammatic_map[num[left]]:
            return False
        left += 1
        right -= 1
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use a map to store the strobogrammatic pairs
- Iterate from both ends of the number and compare the corresponding digits

- Use a map to store related pairs of values
- Handle special cases separately to avoid unnecessary checks

- Handling the case when the number has an odd length

- Converting the number to an integer and comparing the digits
    
### >> Comparison: 290 Word Pattern [Easy] *VS* 246 Strobogrammatic Number [Easy]
> Similarity distance: 0.5694
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve pattern matching.
- Both questions require checking for a specific relationship between characters or digits.
- Both questions have a fixed input format.
##### Differences

- Word Pattern involves matching a pattern between a string of words and a pattern string, while Strobogrammatic Number involves checking if a number is strobogrammatic.
- Word Pattern uses words as input, while Strobogrammatic Number uses numbers as input.
- Word Pattern requires mapping each unique character in the pattern string to a unique word in the input string, while Strobogrammatic Number requires checking if the number is strobogrammatic.
- Word Pattern has a linear time complexity, while Strobogrammatic Number has a constant time complexity.
##### New Insights in 246 Strobogrammatic Number [Easy]

- Word Pattern teaches us how to map characters to words and check for a specific pattern in a string of words.
- Strobogrammatic Number teaches us how to check if a number is strobogrammatic, which means it looks the same when rotated 180 degrees.

