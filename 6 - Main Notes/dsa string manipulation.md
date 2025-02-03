
2025-01-27 17:45

Status:

Tags: [[dsa string]] [[dsa pattern]]


# dsa string manipulation

Ques: You are given a string containing lower-case english alphabets. You need to perform the following operation as many times as possible:
Take the first occurrence of each alphabet if it exists and remove it from the string. Eventually the string becomes empty.

For example, let’s say the string is “ababcba”.
In the first move, we need to remove the first occurrence of each character ‘a’, ‘b’ and ‘c’. It becomes 
“ababcba” → “abba”
Again, we repeat unless the string becomes empty
“abba” → “ba”
“ba” → “”

Find the last non-empty value for the string.

Example 1:

Input : s = "ababcba"
Output: "ba"

## Tip: 
-  Whenever there is some moves involved, generally there is some pattern that is followed that can help us quickly determine the final state.
- Let’s answer these 2 questions:
    1. What will be the final set of characters?
    2. Which occurrence of these final set of characters are remaining?


References
