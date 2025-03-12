2025-01-27 17:45

Status:

Tags: [[dsa string]] [[dsa pattern]] [[frequency array]]

# Frequency Arrays

```python
def create_frequency_array(s):
    # Initialize frequency array for 26 letters
    freq = [0] * 26

    # Iterate through the string
    for char in s:
        # Update the frequency based on ASCII value
        freq[ord(char) - ord('a')] += 1

    return freq

# Example usage
s = "ababcba"
frequency_array = create_frequency_array(s)
print(frequency_array)
```

```python
# Convert integer to character
integer_value = 97
character = chr(integer_value)
print(f"Integer {integer_value} to character: {character}")

# Convert character to integer
char_value = 'a'
integer = ord(char_value)
print(f"Character '{char_value}' to integer: {integer}")
```

# String Manipulation

## Problem Statement

You are given a string containing lower-case English alphabets. You need to perform the following operation as many times as possible:

- Take the first occurrence of each alphabet if it exists and remove it from the string. Eventually, the string becomes empty.

### Example

- Given string: "ababcba"
- Steps:

  1. Remove the first occurrence of each character 'a', 'b', and 'c':
     - "ababcba" → "abba"
  2. Repeat the process:
     - "abba" → "ba"
     - "ba" → ""

- Last non-empty value for the string: "ba"

### Example 1

- Input: s = "ababcba"
- Output: "ba"

## Tip

- Whenever there are some moves involved, generally there is some pattern that can help us quickly determine the final state.
- Questions to consider:
  1. What will be the final set of characters?
  2. Which occurrence of these final set of characters are remaining?

## References
