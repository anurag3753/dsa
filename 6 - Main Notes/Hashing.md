
2025-07-01 15:47

Status:

Tags: [[dsa]]

# Hashing
- If you are declaring a `Hash` array, the maximum size you can declare is: `arr[10^6]`
- Hashing can be defined as `pre-storing` and `fetching`
- You can declare an array at max of size `10^6`
### Number Hashing
```python
# Count the frequency of the numbers
arr = [1, 2, 2, 2, 2, 4, 1, 6, 3, 3, 3, 3, 3, 6]

# Declare an array of size = max(arr) + 1
frequency_array = [0]* (max(arr) + 1)

# It will update the frequency with the number of elements occurence
for number in arr:
    frequency_array[number] += 1

print(frequency_array) # [0, 2, 4, 5, 1, 0, 2]
```
---
### Character Hashing
- You will be given `Q` queries, asking the frequency of a character `c` inside the string `s`
```python
s = "aaabra ka dabra nishank rabra"

frequency_array = [0] * 26

for char in s:
	frequency_array[ord(char) - ord('a')] += 1

# Running Queries
print(frequency_array[ord("r") - ord("a")]) # Frequency of char `r`
```
- If you have not been specified, the character limit. Take it of size `256`'.
- And then we will just store, each char at its specific ASCII value
```python
frequency_arry = [0]* 256
for any_char in s:
    frequency[ord(char)] += 1
```
---
## Python Dictionary Ordering

### Python 3.7+ (Current Standard)

- **Insertion order preserved** - dictionaries maintain the order in which keys were inserted
- **Not sorted order** - keys are stored in the order they were added, not alphabetically or numerically sorted
```python
# Example - insertion order preserved
d = {'c': 3, 'a': 1, 'b': 2}
print(list(d.keys()))  # Output: ['c', 'a', 'b'] (insertion order)
```
### Comparison with C++

| Language     | Data Structure       | Ordering                           |
| ------------ | -------------------- | ---------------------------------- |
| C++          | `std::map`           | **Sorted** by key (red-black tree) |
| C++          | `std::unordered_map` | No guaranteed order (hash table)   |
| Python 3.7+  | `dict`               | **Insertion order preserved**      |
| Python < 3.6 | `dict`               | **No guaranteed order**            |
### If You Need Sorted Order in Python
```python
d = {'c': 3, 'a': 1, 'b': 2}

# Get keys in sorted order
for key in sorted(d.keys()):
    print(f"{key}: {d[key]}")
# Output: a: 1, b: 2, c: 3
```
- If you need sorted access in Python, sort the keys when iterating or use `sorted(dict.items())`

## Detailed Comparison

|Operation|C++ std::map|Python dict|C++ std::unordered_map|
|---|---|---|---|
|Insert|O(log N)|O(1) avg, O(n) worst|O(1) avg, O(n) worst|
|Lookup|O(log N)|O(1) avg, O(n) worst|O(1) avg, O(n) worst|
|Delete|O(log N)|O(1) avg, O(n) worst|O(1) avg, O(n) worst|
|Iteration|O(N) sorted|O(N) insertion order|O(N) no order|
|Memory|Lower overhead|Higher overhead|Higher overhead|
### Why the Difference?

### C++ std::map (Tree-based)
```c++
std::map<int, string> m;
m[42] = "answer";     // O(log N) - tree traversal
auto val = m[42];     // O(log N) - tree traversal
```
### Python dict (Hash-based)
```python
d = {}
d[42] = "answer"      # O(1) average - hash lookup
val = d[42]           # O(1) average - hash lookup
```

## When Does Python dict Become O(n)?

The worst case O(n) happens with **hash collisions**:
```python
# Worst case scenario (theoretical)
# If all keys hash to the same bucket
d = {}
# Many keys that collide would degrade to O(n)
```
- In practice, Python's hash table implementation is highly optimized and O(n) the worst case is extremely rare.
### Hashing Strategies
![[hashing_strategies.png]]
- They don't ask this in the interviews, Just remember the names.
- Division Method: We do the modulo division to identify the index, where number needs to be present, and in case of collisions we append the number to the already stored number using the `Linear Chaining`(Basically creating a linked list)
**Example:**
![[hasing_example.png]]

# References
- [Striver A-Z](https://www.youtube.com/watch?v=KEs5UyBJ39g)