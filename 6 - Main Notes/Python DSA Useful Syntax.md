
2025-06-15 11:33

Status: 

Tags: [[notes/3 - Tags/dsa|dsa]] [[python]] [[syntax]]

# Python DSA Useful Syntax

### Represent largest and smallest number
```python

largest = float("inf")
smallest = float("-inf")
```

# Using Sort and Sorted
#### sort:
- `sort()`: is a method that can be used on lists, but not directly on strings. Strings are immutable in Python, so you cannot sort them in place.
- **Modifies the List in Place**: `sort()` sorts the list it is called on and modifies it directly.
- **Syntax**: `list.sort(key=None, reverse=False)`
#### sorted:
- `sorted()`: **Applicable to Strings**: `sorted()` can be used to sort the characters within a string. It returns a list of characters sorted in ascending order (by default).
- **Returns a New List**: `sorted()` does not modify the original string. Instead, it returns a new list containing the sorted characters.
- **Syntax**: `sorted(iterable, key=None, reverse=False)`




### Reverse a python list, with the specific left and right index
- Given a list say `arr=[1, 2, 3, 4, 5, 6]` reverse sublist from (0, 3) index
- Ans = `[4, 3, 2, 1, 5, 6]`
```python
def reverse_sublist(lst, left, right):
    # Ensure the indices are within the bounds of the list
    if left < 0 or right >= len(lst) or left > right:
        raise ValueError("Invalid indices")

    # Reverse the sublist using slicing with [::-1]
    lst[left:right+1] = lst[left:right+1][::-1]

    return lst
```
#### Explanation:
The expression `lst[left:right+1] = sublist` is used to replace a portion of a list with another list (in this case, a reversed sublist). Let's break down what this means:

- **Slicing**: `lst[left:right+1]` is a slice of the list `lst`. It includes all elements starting from index `left` up to and including index `right`. The `+1` is necessary because list slicing in Python is exclusive of the end index, so `right+1` ensures that the element at index `right` is included in the slice.
    
- **Assignment**: The assignment operation `=` replaces the elements in the specified slice of `lst` with the elements from `sublist`. This means that the elements in `lst` from index `left` to `right` are replaced by the elements in `sublist`.
    
- **In-place Modification**: This operation modifies the original list `lst` in place. It does not create a new list but rather updates the existing list with the new values.

### Running a for loop `k` times in a backward iteration
```python
n = len(arr)
for i in range(n-1, n-k-1, -1):
   ...
```

### XOR Operator Use
- **Bit Manipulation:**    
    - X^X = 0
    - X^0 = X


### Short Circuit
I want to check the last element value of my `answer` array, but it could be possible that initially it is empty and accessing its `[-1]` index will result me an error. What we can do in this case:
```python
if not ans or ans[-1] != a[l]: # not ans will save us
	ans.append(a[l])
```


# References
