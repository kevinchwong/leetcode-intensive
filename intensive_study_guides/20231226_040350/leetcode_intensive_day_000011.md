
# Leetcode Intensive Tutorial Day 11 
> [Difficulty Score: 13]

> [Version: 20231226_040350]

> [Including this day, you had studied : 82 leetcode problems]


## Courses overview of the day

- 594 Longest Harmonious Subsequence [Easy]
  - 266 Palindrome Permutation [Easy]
    - 451 Sort Characters By Frequency [Medium]
      - 423 Reconstruct Original Digits from English [Medium]
    - 192 Word Frequency [Medium]
    - 409 Longest Palindrome [Easy]
      - 242 Valid Anagram [Easy]
      - 443 String Compression [Medium]
    - 383 Ransom Note [Easy]

#### Step by step

 - [1. From 594 Longest Harmonious Subsequence [Easy] to 266 Palindrome Permutation [Easy]](#1-from-594-longest-harmonious-subsequence-easy-to-266-palindrome-permutation-easy))

 - [2. From 266 Palindrome Permutation [Easy] to 451 Sort Characters By Frequency [Medium]](#2-from-266-palindrome-permutation-easy-to-451-sort-characters-by-frequency-medium))

 - [3. From 451 Sort Characters By Frequency [Medium] to 423 Reconstruct Original Digits from English [Medium]](#3-from-451-sort-characters-by-frequency-medium-to-423-reconstruct-original-digits-from-english-medium))

 - [4. From 266 Palindrome Permutation [Easy] to 192 Word Frequency [Medium]](#4-from-266-palindrome-permutation-easy-to-192-word-frequency-medium))

 - [5. From 266 Palindrome Permutation [Easy] to 409 Longest Palindrome [Easy]](#5-from-266-palindrome-permutation-easy-to-409-longest-palindrome-easy))

 - [6. From 409 Longest Palindrome [Easy] to 242 Valid Anagram [Easy]](#6-from-409-longest-palindrome-easy-to-242-valid-anagram-easy))

 - [7. From 409 Longest Palindrome [Easy] to 443 String Compression [Medium]](#7-from-409-longest-palindrome-easy-to-443-string-compression-medium))

 - [8. From 266 Palindrome Permutation [Easy] to 383 Ransom Note [Easy]](#8-from-266-palindrome-permutation-easy-to-383-ransom-note-easy))

    

#### Summary


- 192 Word Frequency : Calculate the frequency of each word in a text file.
- 443 String Compression : Given an array of characters, compress it in-place.
- 451 Sort Characters By Frequency : Given a string, sort it in decreasing order based on the frequency of characters.
- 594 Longest Harmonious Subsequence : The essence of this problem is to find the length of the longest harmonious subsequence in the given array.
- 383 Ransom Note : Count the occurrences of each character in the magazine and check if there are enough occurrences for each character in the ransomNote.
- 423 Reconstruct Original Digits from English : The essence of this problem is counting the frequency of each character in the input string and using the frequencies to determine the digits in the output string.
- 266 Palindrome Permutation : The essence of this problem is to determine if a permutation of the string can form a palindrome.
- 242 Valid Anagram : The essence of the problem is to check if two strings are anagrams.
- 409 Longest Palindrome : Count the occurrences of each character. Add the count of even occurrences to the length. If there is an odd occurrence, subtract 1 from the count and set a flag. If the flag is set, add 1 to the length. Return the final length.
> Similarity Diameter of these problems: 0.7483


---
# 1. From 594 Longest Harmonious Subsequence [Easy] to 266 Palindrome Permutation [Easy]
> Similarity Distance: 0.4453

### >> 594 Longest Harmonious Subsequence [Easy]
Given an integer array nums, return the length of its longest harmonious subsequence.
##### Sample input:
[1,3,2,2,5,2,3,7]
##### Sample output:
5

##### Questions to ask to clarify requirements:
What is a harmonious subsequence?

##### Optimal Python solution:
```python
def findLHS(nums):
    count = {}
    for num in nums:
        count[num] = count.get(num, 0) + 1
    result = 0
    for num in count:
        if num + 1 in count:
            result = max(result, count[num] + count[num + 1])
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Count the frequency of each number
2. Check if the current number and the next number form a harmonious subsequence
3. Update the result if a longer subsequence is found
Use a dictionary to count the frequency of each number.
None
None
    
### >> 266 Palindrome Permutation [Easy]
Given a string s, return true if a permutation of the string could form a palindrome.
##### Sample input:
"code"
##### Sample output:
false

##### Questions to ask to clarify requirements:

- Can the string contain spaces or special characters?
- Should the palindrome be case-sensitive?

##### Optimal Python solution:
```python
def canPermutePalindrome(s):
    count = {}
    for char in s:
        count[char] = count.get(char, 0) + 1
    odd_count = 0
    for val in count.values():
        if val % 2 != 0:
            odd_count += 1
    return odd_count <= 1
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Count the frequency of each character in the string
- Check if the number of characters with odd frequency is less than or equal to 1

- Use a hash table to count the frequency of characters
- Optimize the solution by using a single pass through the string

- Handling strings with spaces or special characters

- Checking all possible permutations of the string
    
### >> Comparison: 594 Longest Harmonious Subsequence [Easy] *VS* 266 Palindrome Permutation [Easy]
> Similarity distance: 0.4453
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating a sequence of characters.
- Both questions require finding a subsequence or permutation with specific properties.
##### Differences

- Question 594 involves finding the longest subsequence with harmonious elements, while question 266 involves determining if a permutation of a string can form a palindrome.
- Question 594 requires finding a subsequence with a specific property, while question 266 requires determining if a permutation has a specific property.
- Question 594 involves finding a subsequence with elements that differ by at most 1, while question 266 involves determining if a permutation can be rearranged to form a palindrome.
##### New Insights in 266 Palindrome Permutation [Easy]

- Question 594 introduces the concept of harmonious subsequence, which is a subsequence with elements that differ by at most 1.
- Question 266 introduces the concept of palindrome permutation, which is a permutation that can be rearranged to form a palindrome.


---
# 2. From 266 Palindrome Permutation [Easy] to 451 Sort Characters By Frequency [Medium]
> Similarity Distance: 0.4270

### >> Reminder: 266 Palindrome Permutation [Easy]
Given a string s, return true if a permutation of the string could form a palindrome.
##### Optimal Python solution:
```python
def canPermutePalindrome(s):
    count = {}
    for char in s:
        count[char] = count.get(char, 0) + 1
    odd_count = 0
    for val in count.values():
        if val % 2 != 0:
            odd_count += 1
    return odd_count <= 1
```
The essence of this problem is to determine if a permutation of the string can form a palindrome.
    
### >> 451 Sort Characters By Frequency [Medium]
Given a string, sort it in decreasing order based on the frequency of characters.
##### Sample input:
"tree"
##### Sample output:
"eert"

##### Questions to ask to clarify requirements:
1. Can the input string contain special characters or only alphabets?
2. Should the output string be in lowercase or maintain the case of the input string?
3. What should be the behavior if the input string is empty?

##### Optimal Python solution:
```python
def frequencySort(s):
    freq = {}
    for char in s:
        freq[char] = freq.get(char, 0) + 1
    sorted_chars = sorted(freq.keys(), key=lambda x: freq[x], reverse=True)
    result = ""
    for char in sorted_chars:
        result += char * freq[char]
    return result
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:
1. Use a dictionary to count the frequency of each character.
2. Sort the characters based on their frequency in descending order.
3. Build the result string by concatenating each character the number of times it appears in the input string.
1. Use the collections.Counter class to count the frequency of characters.
2. Use the sorted() function with a custom key function to sort the characters based on their frequency.
1. Sorting the characters based on their frequency.
2. Handling characters with the same frequency.
1. Using a brute force approach to count the frequency of each character.
2. Sorting the characters using a custom comparison function.
    
### >> Comparison: 266 Palindrome Permutation [Easy] *VS* 451 Sort Characters By Frequency [Medium]
> Similarity distance: 0.4270
##### Similarities

- Both questions involve manipulating characters in a string.
- Both questions require counting the frequency of characters in a string.
##### Differences

- Question 266 is about determining if a string can be rearranged to form a palindrome, while question 451 is about sorting characters in a string based on their frequency.
- Question 266 is classified as easy, while question 451 is classified as medium.
##### New Insights in 451 Sort Characters By Frequency [Medium]

- Question 266 teaches us how to check if a string can be rearranged to form a palindrome by counting the frequency of characters.
- Question 451 teaches us how to sort characters in a string based on their frequency.


---
# 3. From 451 Sort Characters By Frequency [Medium] to 423 Reconstruct Original Digits from English [Medium]
> Similarity Distance: 0.3791

### >> Reminder: 451 Sort Characters By Frequency [Medium]
Given a string, sort it in decreasing order based on the frequency of characters.
##### Optimal Python solution:
```python
def frequencySort(s):
    freq = {}
    for char in s:
        freq[char] = freq.get(char, 0) + 1
    sorted_chars = sorted(freq.keys(), key=lambda x: freq[x], reverse=True)
    result = ""
    for char in sorted_chars:
        result += char * freq[char]
    return result
```
Given a string, sort it in decreasing order based on the frequency of characters.
    
### >> 423 Reconstruct Original Digits from English [Medium]
Given a non-empty string containing an out-of-order English representation of digits 0-9, output the digits in ascending order.
##### Sample input:
"owoztneoer"
##### Sample output:
"012"

##### Questions to ask to clarify requirements:
What is the range of the input string? Can the input string contain other characters besides the English representation of digits?

##### Optimal Python solution:
```python
class Solution:
    def originalDigits(self, s: str) -> str:
        count = [0] * 10
        for c in s:
            if c == 'z': count[0] += 1
            if c == 'w': count[2] += 1
            if c == 'u': count[4] += 1
            if c == 'x': count[6] += 1
            if c == 'g': count[8] += 1
            if c == 'o': count[1] += 1
            if c == 'h': count[3] += 1
            if c == 'f': count[5] += 1
            if c == 's': count[7] += 1
            if c == 'i': count[9] += 1
        count[1] -= count[0] + count[2] + count[4]
        count[3] -= count[8]
        count[5] -= count[4]
        count[7] -= count[6]
        count[9] -= count[5] + count[6] + count[8]
        res = ''
        for i in range(10):
            res += str(i) * count[i]
        return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Count the frequency of each character in the input string.
2. Use the frequencies to determine the digits in the output string.
3. Adjust the counts based on the dependencies between the digits.
1. Use an array to count the frequency of each character.
2. Use the frequencies to determine the digits in the output string.
3. Adjust the counts based on the dependencies between the digits.
The trickiest part of this problem is determining the dependencies between the digits.
Avoid using a brute force approach to count the frequencies of each character.
    
### >> Comparison: 451 Sort Characters By Frequency [Medium] *VS* 423 Reconstruct Original Digits from English [Medium]
> Similarity distance: 0.3791
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating characters in a string.
- Both questions require counting the frequency of characters.
##### Differences

- 451 Sort Characters By Frequency focuses on sorting characters by their frequency.
- 423 Reconstruct Original Digits from English focuses on reconstructing original digits from English words.
- 451 Sort Characters By Frequency uses a priority queue to sort characters.
- 423 Reconstruct Original Digits from English uses a unique pattern to reconstruct digits.
##### New Insights in 423 Reconstruct Original Digits from English [Medium]

- 451 Sort Characters By Frequency teaches us how to use a priority queue to sort characters by frequency.
- 423 Reconstruct Original Digits from English teaches us a unique pattern to reconstruct digits from English words.


---
# 4. From 266 Palindrome Permutation [Easy] to 192 Word Frequency [Medium]
> Similarity Distance: 0.4538

### >> Reminder: 266 Palindrome Permutation [Easy]
Given a string s, return true if a permutation of the string could form a palindrome.
##### Optimal Python solution:
```python
def canPermutePalindrome(s):
    count = {}
    for char in s:
        count[char] = count.get(char, 0) + 1
    odd_count = 0
    for val in count.values():
        if val % 2 != 0:
            odd_count += 1
    return odd_count <= 1
```
The essence of this problem is to determine if a permutation of the string can form a palindrome.
    
### >> 192 Word Frequency [Medium]
Write a bash script to calculate the frequency of each word in a text file words.txt.
##### Sample input:
words.txt:
the day is sunny the the
the sunny is is
##### Sample output:
the 4
is 3
sunny 2
day 1

##### Questions to ask to clarify requirements:
What is the expected output format? Should the output be sorted by frequency or by word?

##### Optimal Python solution:
```python
import collections

with open('words.txt', 'r') as file:
    words = file.read().split()

counter = collections.Counter(words)

for word, count in counter.items():
    print(word, count)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Read the text file and split it into words. Use a counter to count the frequency of each word. Print the word and its frequency.
Use the collections.Counter class to count the frequency of elements in a list.
None
None
    
### >> Comparison: 266 Palindrome Permutation [Easy] *VS* 192 Word Frequency [Medium]
> Similarity distance: 0.4538
##### Similarities

- Both questions involve manipulating strings.
- Both questions require counting characters in a string.
##### Differences

- Question 266 is about checking if a string can be rearranged to form a palindrome, while question 192 is about counting the frequency of words in a string.
- Question 266 is classified as easy, while question 192 is classified as medium.
- Question 266 requires checking for a specific condition (palindrome permutation), while question 192 requires counting frequencies.
- Question 266 has a time complexity of O(n), while question 192 has a time complexity of O(n log n).
##### New Insights in 192 Word Frequency [Medium]

- Question 266 teaches us how to check if a string can be rearranged to form a palindrome.
- Question 192 teaches us how to count the frequency of words in a string.


---
# 5. From 266 Palindrome Permutation [Easy] to 409 Longest Palindrome [Easy]
> Similarity Distance: 0.4888

### >> Reminder: 266 Palindrome Permutation [Easy]
Given a string s, return true if a permutation of the string could form a palindrome.
##### Optimal Python solution:
```python
def canPermutePalindrome(s):
    count = {}
    for char in s:
        count[char] = count.get(char, 0) + 1
    odd_count = 0
    for val in count.values():
        if val % 2 != 0:
            odd_count += 1
    return odd_count <= 1
```
The essence of this problem is to determine if a permutation of the string can form a palindrome.
    
### >> 409 Longest Palindrome [Easy]
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.
##### Sample input:
"abccccdd"
##### Sample output:
7

##### Questions to ask to clarify requirements:
Can the palindrome be formed using only a subset of the characters in the string?

##### Optimal Python solution:
```python
def longestPalindrome(s: str) -> int:
    count = collections.Counter(s)
    length = 0
    odd = False
    for c in count:
        if count[c] % 2 == 0:
            length += count[c]
        else:
            length += count[c] - 1
            odd = True
    return length + 1 if odd else length
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. A palindrome can have at most one character with an odd count.
2. Use a counter to count the occurrences of each character.
3. Iterate through the counter and add the count of even occurrences to the length.
4. If there is an odd occurrence, subtract 1 from the count and set a flag.
5. If the flag is set, add 1 to the length.
6. Return the final length.
Use the collections.Counter class to count the occurrences of each character in the string.
None
None
    
### >> Comparison: 266 Palindrome Permutation [Easy] *VS* 409 Longest Palindrome [Easy]
> Similarity distance: 0.4888
##### Similarities

- Both questions are related to palindromes.
- Both questions are classified as easy level.
- Both questions involve string manipulation.
##### Differences

- Question 266 checks if a given string can be rearranged to form a palindrome.
- Question 409 finds the length of the longest palindrome that can be formed using the characters in a given string.
##### New Insights in 409 Longest Palindrome [Easy]

- Question 266 requires understanding of the concept of palindromes and counting character frequencies.
- Question 409 requires finding the maximum length of a palindrome, considering both odd and even character frequencies.


---
# 6. From 409 Longest Palindrome [Easy] to 242 Valid Anagram [Easy]
> Similarity Distance: 0.5249

### >> Reminder: 409 Longest Palindrome [Easy]
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.
##### Optimal Python solution:
```python
def longestPalindrome(s: str) -> int:
    count = collections.Counter(s)
    length = 0
    odd = False
    for c in count:
        if count[c] % 2 == 0:
            length += count[c]
        else:
            length += count[c] - 1
            odd = True
    return length + 1 if odd else length
```
Count the occurrences of each character. Add the count of even occurrences to the length. If there is an odd occurrence, subtract 1 from the count and set a flag. If the flag is set, add 1 to the length. Return the final length.
    
### >> 242 Valid Anagram [Easy]
Given two strings s and t, return true if t is an anagram of s, and false otherwise.
##### Sample input:
"anagram", "nagaram"
##### Sample output:
true

##### Questions to ask to clarify requirements:
1. Can the input strings contain spaces?
2. Can the input strings contain invalid characters?
3. Can the input strings be empty?
4. Can the input strings have different lengths?
5. Can the input strings have duplicate characters?
6. Can the input strings have leading or trailing spaces?

##### Optimal Python solution:
```python
def isAnagram(s: str, t: str) -> bool:
    if len(s) != len(t):
        return False
    count = [0] * 26
    for i in range(len(s)):
        count[ord(s[i]) - ord('a')] += 1
        count[ord(t[i]) - ord('a')] -= 1
    for c in count:
        if c != 0:
            return False
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Check if the lengths of the two strings are equal.
2. Use an array to count the occurrences of each character in the first string.
3. Use the same array to subtract the occurrences of each character in the second string.
4. If all the counts in the array are zero, the strings are anagrams.
1. Check if the lengths of the two strings are equal.
2. Use an array to count the occurrences of each character in the first string.
3. Use the same array to subtract the occurrences of each character in the second string.
4. If all the counts in the array are zero, the strings are anagrams.
1. Be careful with the case when the lengths of the two strings are different.
2. Be careful with the case when the strings have duplicate characters.
1. Avoid using a loop to iterate through the strings.
2. Avoid using a stack to store intermediate results.
3. Avoid using a queue to store intermediate results.
4. Avoid using a heap to store intermediate results.
5. Avoid using a graph to represent the problem.
6. Avoid using a trie to represent the problem.
7. Avoid using a binary tree to represent the problem.
8. Avoid using a linked list to represent the problem.
9. Avoid using extra space to solve the problem.
10. Avoid using sorting to solve the problem.
11. Avoid using a hash table to store intermediate results.
12. Avoid using two pointers to solve the problem.
13. Avoid using sliding window technique to solve the problem.
14. Avoid using binary search to solve the problem.
    
### >> Comparison: 409 Longest Palindrome [Easy] *VS* 242 Valid Anagram [Easy]
> Similarity distance: 0.5249
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve string manipulation.
- Both questions require checking for character frequency in a string.
##### Differences

- Question 409 involves finding the length of the longest palindrome that can be formed using the characters in a given string.
- Question 242 involves checking if two given strings are anagrams of each other.
##### New Insights in 242 Valid Anagram [Easy]

- In question 409, we can use the frequency of characters to determine if a palindrome can be formed.
- In question 242, we can use a character frequency map to compare the characters in the two strings.


---
# 7. From 409 Longest Palindrome [Easy] to 443 String Compression [Medium]
> Similarity Distance: 0.6002

### >> Reminder: 409 Longest Palindrome [Easy]
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.
##### Optimal Python solution:
```python
def longestPalindrome(s: str) -> int:
    count = collections.Counter(s)
    length = 0
    odd = False
    for c in count:
        if count[c] % 2 == 0:
            length += count[c]
        else:
            length += count[c] - 1
            odd = True
    return length + 1 if odd else length
```
Count the occurrences of each character. Add the count of even occurrences to the length. If there is an odd occurrence, subtract 1 from the count and set a flag. If the flag is set, add 1 to the length. Return the final length.
    
### >> 443 String Compression [Medium]
Given an array of characters, compress it in-place.
##### Sample input:
["a","a","b","b","c","c","c"]
##### Sample output:
6

##### Questions to ask to clarify requirements:

- What should be the output if the compressed array is longer than the original array?
- Can we assume that the input array only contains uppercase and lowercase letters?

##### Optimal Python solution:
```python
def compress(chars):
    anchor = write = 0
    for read, c in enumerate(chars):
        if read + 1 == len(chars) or chars[read + 1] != c:
            chars[write] = chars[anchor]
            write += 1
            if read > anchor:
                for digit in str(read - anchor + 1):
                    chars[write] = digit
                    write += 1
            anchor = read + 1
    return write
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to keep track of the current character and the position to write the compressed characters.
- Iterate through the array and count the number of consecutive occurrences of each character.
- Update the array in-place by overwriting the characters with their compressed form.
- Return the length of the compressed array.

- Use the two pointers technique to solve the problem in-place.
- Convert the count of consecutive occurrences to a string and write each digit to the compressed array.
- Handle edge cases when the input array is empty or contains only one character.

- Handling the case when the compressed array is longer than the original array.
- Updating the array in-place while keeping track of the write position.

- Using additional data structures.
- Modifying the input array without using extra space.
    
### >> Comparison: 409 Longest Palindrome [Easy] *VS* 443 String Compression [Medium]
> Similarity distance: 0.6002
##### Similarities

- Both questions involve manipulating strings.
- Both questions require counting characters in a string.
##### Differences

- Question 409 focuses on finding the length of the longest palindrome that can be formed using the characters in a string.
- Question 443 focuses on compressing a string by replacing repeated characters with their count.
##### New Insights in 443 String Compression [Medium]

- Question 409 teaches us how to determine the maximum length of a palindrome by counting the characters.
- Question 443 teaches us how to compress a string by counting repeated characters.


---
# 8. From 266 Palindrome Permutation [Easy] to 383 Ransom Note [Easy]
> Similarity Distance: 0.6692

### >> Reminder: 266 Palindrome Permutation [Easy]
Given a string s, return true if a permutation of the string could form a palindrome.
##### Optimal Python solution:
```python
def canPermutePalindrome(s):
    count = {}
    for char in s:
        count[char] = count.get(char, 0) + 1
    odd_count = 0
    for val in count.values():
        if val % 2 != 0:
            odd_count += 1
    return odd_count <= 1
```
The essence of this problem is to determine if a permutation of the string can form a palindrome.
    
### >> 383 Ransom Note [Easy]
Given two stings ransomNote and magazine, return true if ransomNote can be constructed from magazine and false otherwise.
##### Sample input:
"a", "b"
"aa", "ab"
"aa", "aab"
##### Sample output:
false
false
true

##### Questions to ask to clarify requirements:
Can the ransomNote and magazine contain only lowercase letters? Can we assume the inputs are always valid?

##### Optimal Python solution:
```python
def canConstruct(ransomNote: str, magazine: str) -> bool:
    count = [0] * 26
    for c in magazine:
        count[ord(c) - ord('a')] += 1
    for c in ransomNote:
        count[ord(c) - ord('a')] -= 1
        if count[ord(c) - ord('a')] < 0:
            return False
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use an array to count the occurrences of each character in the magazine. Then, iterate through the ransomNote and decrement the count for each character. If the count becomes negative, return False.
Use the ord() function to convert characters to their ASCII values.
None
None
    
### >> Comparison: 266 Palindrome Permutation [Easy] *VS* 383 Ransom Note [Easy]
> Similarity distance: 0.6692
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating strings.
- Both questions require checking if a string can be formed using certain characters.
##### Differences

- Question 266 involves checking if a palindrome permutation can be formed from a given string.
- Question 383 involves checking if a ransom note can be formed from a given magazine text.
- Question 266 requires considering the concept of palindrome, while question 383 does not.
- Question 383 requires considering the frequency of characters in the magazine text.
##### New Insights in 383 Ransom Note [Easy]

- Question 266 teaches us how to check if a string can be rearranged into a palindrome.
- Question 383 teaches us how to check if a ransom note can be formed using characters from a magazine text.

