
2025-06-26 22:21

Status:

Tags: [[python]] [[dsa]] [[python string]]
# Python Data Types

## INT
- `abs(x)`: Absolute value.
- Bitwise: `&` (AND), `|` (OR), `^` (XOR), `~` (NOT), `<<` (left shift), `>>` (right shift).
- `pow(x, y)` Or `x ** y`: `x^y`.
- `pow(x, y, mod)`: It is **highly optimized** and much faster (and uses less memory) than doing `pow(x, y) % mod` for large numbers.
```python
result = pow(2, 10, 1000)  # (2^10) % 1000 = 1024 % 1000 = 24
print(result)  # Output: 24
```
---
## Float
- Does not work on Bitwise Operators
- Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`. (Be cautious with direct equality comparison due to precision issues).
- `round(x, n)`: Rounds x to n decimal places.
### Using Math module
```python
import math
print(math.sqrt(16)) # returns the float value
print(math.pi) # Returns the pi value in float
print(math.gcd(12, 18)) # Expect and return int
print(math.factorial(5)) # Expect and return int
print(math.ceil(x))
print(math.floor(x))
```

## String
- Repetition: `*`.
- Membership: `'char' in s`, `'substring' in s`.
- String Methods:
	- `s.lower()`,  `s.upper()`: Case conversion. (Converts all letters to uppercase/lowercase)
	- `s.startswith(prefix)`,  `s.endswith(suffix)`.
	- `s.find(sub)`,  `s.count(sub)`.
	- `s.replace(old, new)`.
	- `s.split(delimiter)`: Returns a list of substrings.
	- `s.join(list_of_strings)`: Joins elements of an iterable with `s` as separator.
	- `s.strip()`, `s.lstrip()`, `s.rstrip()`: Remove leading/trailing whitespace.
	- `s.isdigit()`, `s.isalpha()`, `s.isalnum()`: Check character types.
####  Number to ASCII character
```python
num = 65
char = chr(num)  # 'A'
print(char)
```
#### ASCII character to number
```python
char = 'A'
num = ord(char)  # 65
print(num)
```

## List
- `remove(value)` : It removes an entry from the list if present. Raise `ValueError` otherwise.
- `pop()`: Removes the last entry from a list. Raise `IndexError` if pop from an empty list.
- `extend([newlist])`: It accepts another list as an argument. It attaches the other list to the current list.
- `insert(index, value)`: It inserts the value at the mentioned index.
- `index(value)`: It returns the index of the first match. Raise `ValueError` if no match.
- reverse(): Reverses the list in place.

**Note**: Scenario, where you do not want the values to be changed, tuple is better than lists.
## Tuple
 - Tuple is an immutable data type. It does not support item assignment.
 - Also, tuple does not support any addition/removal of values from it. After it is created.
 - Also tuple is memory efficient as compared to list.
```python
import sys

def main():
  cordinate_tuple = (42.376, -71.115)
  cordinate_list = [42.376, -71.115]
  print(f"{sys.getsizeof(cordinate_tuple)} bytes")
  print(f"{sys.getsizeof(cordinate_list)} bytes")
```
```shell
# Output
>> 56 bytes
>> 72 bytes
```
---
## Dictionary
- Accessing values: `my_dict[key]` (raises KeyError if key not found), `my_dict.get(key, default_value)`
- Removing: `my_dict.pop(key, default_value)`
	-  **Removes** the item with the specified `key` from the dictionary.
	- **Returns** the value associated with that `key`.
	- If the `key` does **not** exist, it returns `default_value` instead of raising a `KeyError`.
- Clear: `my_dict.clear()` : Will empty the entire dict. It does not return a value on success.
- Update: `my_dict.update()`: To add values inside a python dictionary. It accepts a dict as an argument.
- Iterating:    
    - `for key in my_dict:`        
    - `for value in my_dict.values():`        
    - `for key, value in my_dict.items():`        
- `my_dict.keys()`, `my_dict.values()`, `my_dict.items()`: Returns view objects.

# References
