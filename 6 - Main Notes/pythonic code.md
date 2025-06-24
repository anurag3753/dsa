
2025-06-04 13:33

Status:

Tags: [[python]]


# pythonic code

```python
def is_even(n): 
    return True if n % 2 == 0 else False # Check for parity. Like english readable code
```

#### match keyword (introduced in 3.10+)
- This is the substitute for the `switch` in Python

```python
  name = input("What's your name? ")

  match name: 
      case "Harry" | "Hermione" | "Ron":
          print("Gryffindor")
      case "Draco":
          print("Slytherin")
      case _:
          print("Who?")
# | Much like or keyword, this allows us to check for multiple values in the same case statement.
```

```python
def get_media_type(filename):

    filename, filetype = get_parts(filename)
    
    match filetype:
        case "gif" | "png":
            return f"image/{filetype}"
        case "jpg" | "jpeg":
            return f"image/jpeg"
        case "txt":
            return "text/plain"
        case "pdf" | "zip":
            return f"application/{filetype}"
        case "" | _: # Note, how to check any empty case and for all case
            return "application/octet-stream"
```

## Dict
- `update()`: To add values inside a python dictionary. It accepts a dict as an argument.\
- `pop()`: To remove a key from a python dictionary. It returns the value of the removed key.
- clear() : Will empty the entire dict. It does not return a value on success.
- Scenario, where you do not want the values to be changed, tuple is better than lists.

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

## List
- `remove(value)` : It removes an entry from the list if present. Raise `ValueError` otherwise.
- `pop()`: Removes the last entry from a list. Raise `IndexError` if pop from an empty list.
- `extend([newlist])`: It accepts another list as an argument. It attaches the other list to the current list.
- `insert(index, value)`: It inserts the value at the mentioned index.
- `index(value)`: It returns the index of the first match. Raise `ValueError` if no match.
- reverse(): Reverses the list inplace.

## Swapping list elements inside another function in python
```python
def swap(my_list, index1, index2):
    my_list[index1], my_list[index2] = my_list[index2], my_list[index1]
```
This line of Python code, `my_list[index1], my_list[index2] = my_list[index2], my_list[index1]`, is a classic and very Pythonic way to swap two values without needing a temporary variable.

Here's how this "simultaneous assignment" or "tuple unpacking" works:

1. Right-Hand Side (RHS) Evaluation First:
    
    Python first evaluates everything on the right side of the = operator. It fetches the value currently at my_list[index2] and the value currently at my_list[index1]. These two values are temporarily stored together (conceptually as a tuple).
    
    - **Example:** If `my_list = [10, 20, 30]`, `index1 = 0`, `index2 = 2`:
        - RHS: `my_list[2]` (which is `30`) and `my_list[0]` (which is `10`)
        - This creates a temporary structure like `(30, 10)`.
2. Left-Hand Side (LHS) Assignment (Unpacking):
    
    Once the right side is fully evaluated and the temporary tuple is formed, Python then proceeds to assign these values to the variables (or list elements) on the left side, from left to right.
    
    - **Example (continued):**
        - The first value from the temporary structure (`30`) is assigned to `my_list[index1]` (i.e., `my_list[0]`). So, `my_list` becomes `[30, 20, 30]`.
        - The second value from the temporary structure (`10`) is assigned to `my_list[index2]` (i.e., `my_list[2]`). So, `my_list` becomes `[30, 20, 10]`.

The key is that the RHS is fully evaluated _before_ any assignments on the LHS are made. This prevents a scenario where the value of `my_list[index1]` would be overwritten before it's used to set `my_list[index2]`.


## List  & Dictionary Comprehensions
```python
numbers = [1, 4, 2, 1, 1, 5, 3, 4, 4, 4, 5, 6]
# Create a frequency dict out of it.
frequency = {number: numbers.count(number) for number in numbers}
```


## Coding Tips
- It’s best practice in programming to begin counting with zero.
- The term iteration has special significance within coding. By iteration, we mean one cycle through the loop. The first iteration is the `0th` iteration through the loop. The second is the `1st` iteration. In programming, we count starting with 0, then 1, then 2.
- A good idea while debugging using print statements is that, use proper separator inside the print statement. Ex:
	```python
	print(student, students[student], sep=", ")
	```
- Above statement will segregate the program output using `,` and a space.
- 
# References
