Python offers several built-in data types that are frequently used in competitive programming. Understanding their properties and common operations is crucial for efficient problem-solving. Here's a breakdown:

### 1. Numeric Types

Python has three core numeric types:

- **`int` (Integers):**
    
    - Arbitrary precision integers, meaning they can store numbers of any size (limited only by available memory). This is a significant advantage in competitive programming as you don't have to worry about overflow issues like in C++ or Java for large integers.
        
    - **Common Operations:**
        
        - Arithmetic: `+`, `-`, `*`, `/` (float division), `//` (integer division), `%` (modulo), `**` (exponentiation).
            
        - Bitwise: `&` (AND), `|` (OR), `^` (XOR), `~` (NOT), `<<` (left shift), `>>` (right shift).
            
        - Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`.
            
        - `abs(x)`: Absolute value.
            
        - `pow(x, y)` or `x ** y`: xy.
            
        - `pow(x, y, mod)`: xy(modmod) (highly optimized for modular exponentiation).
            
- **`float` (Floating-Point Numbers):**
    
    - Represent real numbers using double-precision (64-bit) floating-point representation.
        
    - **Common Operations:**
        
        - Arithmetic: `+`, `-`, `*`, `/`, `**`.
            
        - Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`. (Be cautious with direct equality comparison due to precision issues).
            
        - `math.ceil(x)`, `math.floor(x)`, `math.trunc(x)`: Ceiling, floor, and truncation.
            
        - `math.sqrt(x)`: Square root.
            
        - `round(x, n)`: Rounds x to n decimal places.
            
- **`complex` (Complex Numbers):**
    
    - Represent complex numbers with real and imaginary parts. Less common in typical competitive programming problems.
        

### 2. Sequence Types

These types store collections of items in a specific order.

- **`str` (Strings):**
    
    - Immutable sequence of Unicode characters.
        
    - **Common Operations:**
        
        - Concatenation: `+`.
            
        - Repetition: `*`.
            
        - Indexing: `s[i]` (access character at index `i`).
            
        - Slicing: `s[start:end]`, `s[start:end:step]`.
            
        - Length: `len(s)`.
            
        - Membership: `'char' in s`, `'substring' in s`.
            
        - String methods:
            
            - `s.lower()`, `s.upper()`: Case conversion.
                
            - `s.startswith(prefix)`, `s.endswith(suffix)`.
                
            - `s.find(sub)`, `s.count(sub)`.
                
            - `s.replace(old, new)`.
                
            - `s.split(delimiter)`: Returns a list of substrings.
                
            - `s.join(list_of_strings)`: Joins elements of an iterable with `s` as separator.
                
            - `s.strip()`, `s.lstrip()`, `s.rstrip()`: Remove leading/trailing whitespace.
                
            - `s.isdigit()`, `s.isalpha()`, `s.isalnum()`: Check character types.
                
- **`list` (Lists):**
    
    - Mutable, ordered sequence of items (can contain heterogeneous data types). Highly versatile.
        
    - **Common Operations:**
        
        - Creation: `[]`, `list()`, `[1, 2, 3]`.
            
        - Concatenation: `+`.
            
        - Repetition: `*`.
            
        - Indexing: `my_list[i]`.
            
        - Slicing: `my_list[start:end]`.
            
        - Length: `len(my_list)`.
            
        - Membership: `item in my_list`.
            
        - Modification:
            
            - `my_list[i] = new_value`.
                
            - `my_list.append(item)`: Add to end.
                
            - `my_list.extend(another_list)`: Extend with elements from another list.
                
            - `my_list.insert(index, item)`: Insert at specific index.
                
            - `my_list.remove(item)`: Remove first occurrence of item.
                
            - `my_list.pop(index)`: Remove and return item at index (defaults to last).
                
            - `del my_list[index]`, `del my_list[start:end]`.
                
            - `my_list.sort()`, `sorted(my_list)`: Sort in-place or return a new sorted list.
                
            - `my_list.reverse()`.
                
            - `my_list.clear()`.
                
- **`tuple` (Tuples):**
    
    - Immutable, ordered sequence of items. Often used for fixed collections of related data, or as dictionary keys (since they are hashable).
        
    - **Common Operations:**
        
        - Creation: `()`, `(1, 2, 3)`, `1,` (for single element tuple).
            
        - Concatenation: `+`.
            
        - Repetition: `*`.
            
        - Indexing: `my_tuple[i]`.
            
        - Slicing: `my_tuple[start:end]`.
            
        - Length: `len(my_tuple)`.
            
        - Membership: `item in my_tuple`.
            
        - Unpacking: `a, b, c = my_tuple`.
            

### 3. Set Types

- **`set` (Sets):**
    
    - Mutable, unordered collection of unique hashable items. Used for fast membership testing, removing duplicates, and set operations.
        
    - **Common Operations:**
        
        - Creation: `{1, 2, 3}`, `set([1, 2, 3])`.
            
        - Adding elements: `my_set.add(item)`.
            
        - Removing elements: `my_set.remove(item)` (raises KeyError if not found), `my_set.discard(item)` (no error if not found).
            
        - Membership: `item in my_set` (average O(1) time complexity).
            
        - Set operations:
            
            - `my_set.union(other_set)` or `my_set | other_set`.
                
            - `my_set.intersection(other_set)` or `my_set & other_set`.
                
            - `my_set.difference(other_set)` or `my_set - other_set`.
                
            - `my_set.symmetric_difference(other_set)` or `my_set ^ other_set`.
                
            - `my_set.issubset(other_set)`, `my_set.issuperset(other_set)`.
                
        - Length: `len(my_set)`.
            
- **`frozenset` (Frozen Sets):**
    
    - Immutable version of `set`. Can be used as dictionary keys.
        

### 4. Mapping Type

- **`dict` (Dictionaries):**
    
    - Mutable, unordered collection of key-value pairs. Keys must be unique and hashable. Values can be of any type.
        
    - **Common Operations:**
        
        - Creation: `{}`, `dict()`, `{'a': 1, 'b': 2}`.
            
        - Accessing values: `my_dict[key]` (raises KeyError if key not found), `my_dict.get(key, default_value)`.
            
        - Adding/modifying: `my_dict[key] = value`.
            
        - Removing: `del my_dict[key]`, `my_dict.pop(key, default_value)`.
            
        - Length: `len(my_dict)`.
            
        - Membership: `key in my_dict`.
            
        - Iterating:
            
            - `for key in my_dict:`
                
            - `for value in my_dict.values():`
                
            - `for key, value in my_dict.items():`
                
        - `my_dict.keys()`, `my_dict.values()`, `my_dict.items()`: Returns view objects.
            
        - `my_dict.clear()`.
            

### 5. Other Important Types/Concepts

- **`bool` (Booleans):**
    
    - `True` and `False`. Used in conditional statements.
        
    - Operations: `and`, `or`, `not`.
        
- **`NoneType` (`None`):**
    
    - Represents the absence of a value.
        
- **`collections` Module:**
    
    - Provides specialized container datatypes:
        
        - `collections.deque`: Double-ended queue, efficient appends and pops from both ends (O(1)). Great for BFS and sliding window problems.
            
        - `collections.Counter`: A dict subclass for counting hashable objects.
            
        - `collections.defaultdict`: A dict subclass that calls a factory function to supply missing values.
            
- **`heapq` Module:**
    
    - Implements the heap queue algorithm (min-heap by default). Useful for priority queues.
        
    - `heapq.heappush(heap, item)`, `heapq.heappop(heap)`.
        

### Tips for Competitive Programming:

- **Choose the Right Data Structure:** Selecting the most appropriate data type for a given task is crucial for efficiency. For example, use a `set` for unique elements and fast lookups, a `list` for ordered mutable collections, and a `dict` for key-value mappings.
    
- **Immutability vs. Mutability:** Understand the difference. Immutable types (tuples, strings, frozensets, numbers) cannot be changed after creation. Mutable types (lists, dictionaries, sets) can be modified. This impacts how you pass them to functions and what can be used as dictionary keys or set elements.
    
- **Time Complexity:** Be aware of the time complexity of operations. For instance, `item in list` is O(N) on average, while `item in set` is O(1) on average.
    
- **List Comprehensions:** Use them for concise and efficient list creation and transformation.
    
    - `[i*2 for i in range(5)]`
        
    - `[i for i in my_list if i % 2 == 0]`
        
- **String Formatting:** Use f-strings (Python 3.6+) for easy and readable string formatting: `f"The answer is {ans}"`.
    
- **Built-in Functions:** Leverage built-in functions like `min()`, `max()`, `sum()`, `all()`, `any()`, `zip()`, `map()`, `filter()`.
    
- **Debugging:** Use `print()` statements effectively.
    
- **Input/Output:** In competitive programming, efficient I/O can sometimes be critical for large inputs. Consider using `sys.stdin.readline` and `sys.stdout.write` for faster I/O than `input()` and `print()`.
    

By mastering these data types and their operations, you'll be well-equipped to tackle a wide range of competitive programming problems in Python.