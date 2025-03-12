2025-01-27 17:02

Status: #baby

Tags: [[python collections]]

# Counter

It allows us to count the frequency of elements in an iterable.

```python
from collections import Counter
x = Counter("geeksforgeeks") # It is a dict
x_keys = list(x.keys())
x_values = list(x.values())
```

### Comparing 2 dicts in a Counter object

```python
# Comparing 2 dicts of a Counter
s = Counter(list1)
t = Counter(list2)

import operator
if operator.eq(s, t):
    print("Equal")
else:
    print("Not Equal")
```

References
[GFG](https://www.geeksforgeeks.org/python-counter-objects-elements/)
