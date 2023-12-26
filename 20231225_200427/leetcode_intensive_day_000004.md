
# Leetcode Intensive Tutorial Day 4 
> [Difficulty Score: 12]

> [Version: 20231225_200427]

## Courses overview of the day

- 521 Longest Uncommon Subsequence I [Easy]
  - 58 Length of Last Word [Easy]
    - 557 Reverse Words in a String III [Easy]
      - 151 Reverse Words in a String [Medium]
      - 418 Sentence Screen Fitting [Medium]
        - 68 Text Justification [Hard]
      - 434 Number of Segments in a String [Easy]

#### Steps by steps

 - [1. From 521 Longest Uncommon Subsequence I [Easy] to 58 Length of Last Word [Easy]](#1-from-521-longest-uncommon-subsequence-i-easy-to-58-length-of-last-word-easy)

 - [2. From 58 Length of Last Word [Easy] to 557 Reverse Words in a String III [Easy]](#2-from-58-length-of-last-word-easy-to-557-reverse-words-in-a-string-iii-easy)

 - [3. From 557 Reverse Words in a String III [Easy] to 151 Reverse Words in a String [Medium]](#3-from-557-reverse-words-in-a-string-iii-easy-to-151-reverse-words-in-a-string-medium)

 - [4. From 557 Reverse Words in a String III [Easy] to 418 Sentence Screen Fitting [Medium]](#4-from-557-reverse-words-in-a-string-iii-easy-to-418-sentence-screen-fitting-medium)

 - [5. From 418 Sentence Screen Fitting [Medium] to 68 Text Justification [Hard]](#5-from-418-sentence-screen-fitting-medium-to-68-text-justification-hard)

 - [6. From 557 Reverse Words in a String III [Easy] to 434 Number of Segments in a String [Easy]](#6-from-557-reverse-words-in-a-string-iii-easy-to-434-number-of-segments-in-a-string-easy)

#### Summary


- 521 Longest Uncommon Subsequence I : The essence of this question is to find the longest uncommon subsequence of two strings.
- 58 Length of Last Word : Given a string s consists of some words separated by spaces, return the length of the last word in the string.
- 418 Sentence Screen Fitting : Given a screen and a sentence, find the number of times the sentence can be fitted on the screen.
- 557 Reverse Words in a String III : Reverse the order of characters in each word within a sentence while preserving whitespace and initial word order.
- 434 Number of Segments in a String : Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.
- 151 Reverse Words in a String : The essence of this problem is to reverse the words in a string.
- 68 Text Justification : Formatting text by adding words to lines and justifying the lines.
> Similarity Diameter of these problems: 0.5766


---
# 1. From 521 Longest Uncommon Subsequence I [Easy] to 58 Length of Last Word [Easy]
> Similarity Distance: 0.4655

### >> 521 Longest Uncommon Subsequence I [Easy]
Given two strings, you need to find the longest uncommon subsequence of this two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other string.
##### Sample input:
"aba"
"cdc"
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is a subsequence of a string?

##### Optimal Python solution:
```python
def findLUSlength(a: str, b: str) -> int:
    if a == b:
        return -1
    else:
        return max(len(a), len(b))
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. The longest uncommon subsequence is the longer string if the two strings are different.
2. If the two strings are the same, there is no uncommon subsequence.
3. The longest uncommon subsequence cannot be a subsequence of the other string.
There is no specific programming tip for this question.
There is no tricky part in this question.
There is no specific thing to avoid in this question.
    
### >> 58 Length of Last Word [Easy]
Given a string s consists of some words separated by spaces, return the length of the last word in the string. If the last word does not exist, return 0.
##### Sample input:
"Hello World"
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can the string be empty?
- Can the string contain leading or trailing spaces?

##### Optimal Python solution:
```python
def lengthOfLastWord(s):
    words = s.split()
    if len(words) == 0:
        return 0
    return len(words[-1])
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Split the string into words using spaces as separators.
- Return the length of the last word in the list of words.
- Handle the cases where the string is empty or contains only spaces.

- Use the split() method to split the string into words using spaces as separators.
- Handle the cases where the string is empty or contains only spaces by checking the length of the resulting list of words.

- Handling the cases where the string is empty or contains only spaces.

- Using regular expressions to split the string.
    
### >> Comparison: 521 Longest Uncommon Subsequence I [Easy] *VS* 58 Length of Last Word [Easy]
> Similarity distance: 0.4655
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve string manipulation.
- Both questions require finding the length of a subsequence or word.
##### Differences

- Question 521: Longest Uncommon Subsequence I involves finding the length of the longest uncommon subsequence between two strings.
- Question 58: Length of Last Word involves finding the length of the last word in a given string.
##### New Insights in 58 Length of Last Word [Easy]

- Question 521: Longest Uncommon Subsequence I introduces the concept of uncommon subsequences, which are subsequences that do not appear in both strings.
- Question 58: Length of Last Word introduces the concept of finding the length of the last word in a string, which requires handling whitespace and edge cases.


---
# 2. From 58 Length of Last Word [Easy] to 557 Reverse Words in a String III [Easy]
> Similarity Distance: 0.4289

### >> Reminder: 58 Length of Last Word [Easy]
Given a string s consists of some words separated by spaces, return the length of the last word in the string. If the last word does not exist, return 0.
##### Optimal Python solution:
```python
def lengthOfLastWord(s):
    words = s.split()
    if len(words) == 0:
        return 0
    return len(words[-1])
```
Given a string s consists of some words separated by spaces, return the length of the last word in the string.
    
### >> 557 Reverse Words in a String III [Easy]
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
##### Sample input:
"Let's take LeetCode contest"
##### Sample output:
"s'teL ekat edoCteeL tsetnoc"

##### Questions to ask to clarify requirements:
Are the words separated by a single space? Can the input string be empty?

##### Optimal Python solution:
```python
def reverseWords(s):
    return ' '.join(word[::-1] for word in s.split())
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Split the string into words
2. Reverse each word
3. Join the reversed words with a space
No specific tips
No tricky parts
No specific pitfalls
    
### >> Comparison: 58 Length of Last Word [Easy] *VS* 557 Reverse Words in a String III [Easy]
> Similarity distance: 0.4289
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating strings.
- Both questions require reversing or extracting words from a string.
##### Differences

- Question 58 focuses on finding the length of the last word in a string.
- Question 557 focuses on reversing the order of words in a string.
##### New Insights in 557 Reverse Words in a String III [Easy]

- Question 58 teaches us how to find the length of the last word in a string by utilizing string manipulation techniques.
- Question 557 teaches us how to reverse the order of words in a string by utilizing string manipulation techniques.


---
# 3. From 557 Reverse Words in a String III [Easy] to 151 Reverse Words in a String [Medium]
> Similarity Distance: 0.2405

### >> Reminder: 557 Reverse Words in a String III [Easy]
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
##### Optimal Python solution:
```python
def reverseWords(s):
    return ' '.join(word[::-1] for word in s.split())
```
Reverse the order of characters in each word within a sentence while preserving whitespace and initial word order.
    
### >> 151 Reverse Words in a String [Medium]
Given an input string, reverse the string word by word.
##### Sample input:
s = "the sky is blue"
Output: "blue is sky the"
##### Sample output:
"blue is sky the"

##### Questions to ask to clarify requirements:
What should be the output if the input string is empty? Can the input string contain leading or trailing spaces?

##### Optimal Python solution:
```python
def reverseWords(s):
    return ' '.join(s.split()[::-1])
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Split the input string into a list of words.
2. Reverse the list of words.
3. Join the reversed list of words with spaces.
1. Use built-in functions like split(), reverse(), and join() for string manipulation.
2. Handle edge cases like empty string and leading/trailing spaces.
3. Consider using two pointers to reverse a list in-place.
1. Handling leading and trailing spaces.
2. Handling multiple spaces between words.
1. Using built-in functions like split() and join().
2. Using extra space.
    
### >> Comparison: 557 Reverse Words in a String III [Easy] *VS* 151 Reverse Words in a String [Medium]
> Similarity distance: 0.2405
##### Similarities

- Both questions involve reversing the order of words in a string.
##### Differences

- Question 557 is classified as Easy, while question 151 is classified as Medium.
- Question 557 requires reversing the order of characters within each word, while question 151 does not.
- Question 557 allows leading and trailing spaces, while question 151 does not.
- Question 557 has a constraint on the length of the input string, while question 151 does not.
##### New Insights in 151 Reverse Words in a String [Medium]

- Question 557 requires a two-pointer approach to reverse the order of characters within each word.
- Question 151 can be solved using a three-step approach: reverse the entire string, reverse each word, and remove extra spaces.


---
# 4. From 557 Reverse Words in a String III [Easy] to 418 Sentence Screen Fitting [Medium]
> Similarity Distance: 0.3969

### >> Reminder: 557 Reverse Words in a String III [Easy]
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
##### Optimal Python solution:
```python
def reverseWords(s):
    return ' '.join(word[::-1] for word in s.split())
```
Reverse the order of characters in each word within a sentence while preserving whitespace and initial word order.
    
### >> 418 Sentence Screen Fitting [Medium]
Given a rows x cols screen and a sentence represented as a list of strings, return the number of times the given sentence can be fitted on the screen.
##### Sample input:

- rows = 3, cols = 6, sentence = ["a", "bcd", "e"]
##### Sample output:

- 2

##### Questions to ask to clarify requirements:

- Can the screen have empty rows?
- Can the screen have empty columns?
- Can the sentence be empty?
- Can the sentence contain empty strings?
- Can the sentence contain strings longer than the screen width?

##### Optimal Python solution:
```python

- from typing import List
- 
- class Solution:
-     def wordsTyping(self, sentence: List[str], rows: int, cols: int) -> int:
-         s = ' '.join(sentence) + ' '
-         start = 0
-         n = len(s)
-         for i in range(rows):
-             start += cols
-             if s[start % n] == ' ':
-                 start += 1
-             else:
-                 while start > 0 and s[(start - 1) % n] != ' ':
-                     start -= 1
-         return start // n
- 
- solution = Solution()
- result = solution.wordsTyping(["a", "bcd", "e"], 3, 6)
- print(result)
```
##### Time complexity:
O(rows + n)
##### Space complexity:
O(n)
##### Notes:

- Join the sentence into a single string with spaces
- Iterate over the rows and count the number of times the sentence can be fitted

- Use the modulo operator to handle wrapping around the string
- Optimize the solution by avoiding unnecessary iterations

- Using modulo operator to handle wrapping around the string

- Using a nested loop to iterate over the screen
    
### >> Comparison: 557 Reverse Words in a String III [Easy] *VS* 418 Sentence Screen Fitting [Medium]
> Similarity distance: 0.3969
##### Similarities

- Both questions involve manipulating strings.
- Both questions require iterating through the input string.
- Both questions involve reversing parts of the string.
##### Differences

- Question 557 reverses each word in the string, while question 418 fits sentences on a screen.
- Question 557 operates on individual words, while question 418 operates on complete sentences.
- Question 557 requires reversing the order of characters within each word, while question 418 requires fitting sentences on multiple lines.
- Question 557 has an easy difficulty level, while question 418 has a medium difficulty level.
##### New Insights in 418 Sentence Screen Fitting [Medium]

- Question 557 teaches us how to reverse the order of characters within a word.
- Question 418 teaches us how to fit sentences on multiple lines based on screen width.


---
# 5. From 418 Sentence Screen Fitting [Medium] to 68 Text Justification [Hard]
> Similarity Distance: 0.5103

### >> Reminder: 418 Sentence Screen Fitting [Medium]
Given a rows x cols screen and a sentence represented as a list of strings, return the number of times the given sentence can be fitted on the screen.
##### Optimal Python solution:
```python

- from typing import List
- 
- class Solution:
-     def wordsTyping(self, sentence: List[str], rows: int, cols: int) -> int:
-         s = ' '.join(sentence) + ' '
-         start = 0
-         n = len(s)
-         for i in range(rows):
-             start += cols
-             if s[start % n] == ' ':
-                 start += 1
-             else:
-                 while start > 0 and s[(start - 1) % n] != ' ':
-                     start -= 1
-         return start // n
- 
- solution = Solution()
- result = solution.wordsTyping(["a", "bcd", "e"], 3, 6)
- print(result)
```
Given a screen and a sentence, find the number of times the sentence can be fitted on the screen.
    
### >> 68 Text Justification [Hard]
Given an array of words and a width maxWidth, format the text such that each line has exactly maxWidth characters and is fully (left and right) justified.
##### Sample input:
["This", "is", "an", "example", "of", "text", "justification."], 16
##### Sample output:
["This    is    an", "example  of text", "justification.  "]

##### Questions to ask to clarify requirements:
What should be done if a word cannot fit in a line with maxWidth characters?

##### Optimal Python solution:
```python
def fullJustify(words: List[str], maxWidth: int) -> List[str]:
    result = []
    line = []
    line_length = 0
    for word in words:
        if line_length + len(line) + len(word) <= maxWidth:
            line.append(word)
            line_length += len(word)
        else:
            num_spaces = maxWidth - line_length
            if len(line) == 1:
                result.append(line[0] + ' ' * num_spaces)
            else:
                num_gaps = len(line) - 1
                spaces_per_gap = num_spaces // num_gaps
                extra_spaces = num_spaces % num_gaps
                justified_line = ''
                for i in range(len(line) - 1):
                    justified_line += line[i] + ' ' * spaces_per_gap
                    if i < extra_spaces:
                        justified_line += ' '
                justified_line += line[-1]
                result.append(justified_line)
            line = [word]
            line_length = len(word)
    result.append(' '.join(line).ljust(maxWidth))
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Iterate through the words and add them to a line until the line length exceeds maxWidth.
2. Justify the line by evenly distributing the extra spaces between the words.
3. Add the justified line to the result.
4. Repeat until all words have been processed.
Use the built-in functions len() and ljust() to calculate the length of a line and add spaces to the right side of a line.
Handling the last line and the case when a word cannot fit in a line with maxWidth characters.
Creating a new string for each line.
    
### >> Comparison: 418 Sentence Screen Fitting [Medium] *VS* 68 Text Justification [Hard]
> Similarity distance: 0.5103
##### Similarities

- Both questions involve manipulating strings and solving text formatting problems.
- Both questions require careful consideration of word boundaries and line breaks.
- Both questions involve optimizing the placement of words within a given space.
##### Differences

- 418 Sentence Screen Fitting focuses on fitting sentences into a screen with a fixed width and height.
- 68 Text Justification focuses on justifying text by adding spaces between words to achieve a balanced appearance.
- 418 Sentence Screen Fitting has a linear time complexity solution, while 68 Text Justification has a more complex solution with a time complexity of O(n^2).
##### New Insights in 68 Text Justification [Hard]

- From 418 Sentence Screen Fitting, we can learn how to efficiently fit sentences into a screen by considering word boundaries and line breaks.
- From 68 Text Justification, we can learn how to justify text by adding spaces between words to achieve a balanced appearance.


---
# 6. From 557 Reverse Words in a String III [Easy] to 434 Number of Segments in a String [Easy]
> Similarity Distance: 0.4248

### >> Reminder: 557 Reverse Words in a String III [Easy]
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
##### Optimal Python solution:
```python
def reverseWords(s):
    return ' '.join(word[::-1] for word in s.split())
```
Reverse the order of characters in each word within a sentence while preserving whitespace and initial word order.
    
### >> 434 Number of Segments in a String [Easy]
Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.
##### Sample input:
"Hello, my name is John"
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can there be multiple spaces between words?
- Should we count empty segments?

##### Optimal Python solution:
```python

- def countSegments(s: str) -> int:
-     return len(s.split())
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:

- Split the string by spaces
- Count the number of non-empty segments

- Use the split function to split the string by spaces.
- Use the len function to get the count of segments.

- Handling multiple spaces between words

- Using regular expressions
    
### >> Comparison: 557 Reverse Words in a String III [Easy] *VS* 434 Number of Segments in a String [Easy]
> Similarity distance: 0.4248
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve manipulating strings.
- Both questions require reversing or counting segments in a string.
##### Differences

- 557 Reverse Words in a String III focuses on reversing individual words in a string, while 434 Number of Segments in a String focuses on counting the number of segments in a string.
- 557 Reverse Words in a String III reverses the order of characters within each word, while 434 Number of Segments in a String counts the number of segments separated by spaces.
- 557 Reverse Words in a String III requires reversing the entire string, while 434 Number of Segments in a String does not require any string reversal.
##### New Insights in 434 Number of Segments in a String [Easy]

- From 557 Reverse Words in a String III, we can learn how to reverse the order of characters within each word in a string.
- From 434 Number of Segments in a String, we can learn how to count the number of segments in a string by identifying the spaces between segments.

