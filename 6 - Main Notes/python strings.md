
2025-06-04 13:55

Status:

Tags: [[python]] [[python string]]

# python strings


###  String Replace

```python
a = "This is CS50"
print(a.replace(" ", "...")) 
# Will output : This...is...CS50
```

### String lowercase
```python
a = "This is CS50"
print(a.lower()) 
```

### String split
- `split` returns a list. It is a good idea to keep a variable only a single variable on the LHS to receive the value. 
```python
filename, filetype = filename.split(".") # BAD, will fail if there is no file type
parts = filename.rsplit('.', 1) # This is better in this case, as it will split from RHS and atmax 1 split will be performed.
```

- `title()`: It capitalizes each first letter in the title
- `capitalize()`: It capitalizes only the first letter of the word.
- `isUpper()`: It checks if a char is in uppercase. Returns True/False
- `isalpha()`: It checks if all the characters are alphabets. Returns True/False
- `isalnum()`: The `isalnum()` method returns True if all the characters are alphanumeric, meaning alphabet letter (a-z) and numbers (0-9).
- `isnumeric()/isdigit()`: returns True if all characters in the string are numeric, such as digits, and False if the string contains any non-numeric character
- 

### Join
The `join()` method in Python is used to **combine a list (or any iterable) of strings into a single string**, with a specified separator between each element.
```python
words = ['hello', 'world']
sentence = ' '.join(words)
print(sentence)  # Output: hello world
```

# References
