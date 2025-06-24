
2025-06-20 19:58

Status:

Tags: [[binary search]] [[dsa]] [[dsa array]] 


# dsa binary search

### Overflow Condition in Binary Search:
- What if the search space is too big. Example: `0 - INT_MAX`, in that case this operation of `mid = (low+high)/2` will be an overflow problem. Because temporary computed value can not be stored correctly inside computer due to integer overflow.
- Solution : Only valid if the search space is between `0-INT_MAX`
```python
mid = low + (high - low)/2
```
-  [Reference](https://youtu.be/MHf6awe89xw?t=1748)

### Lower Bound

The lower bound in a binary search is the smallest index `i` in a sorted array such that `arr[i] >= target`. If no such index exists, the function returns the size of the array, indicating that all elements in the array are less than the target. This is useful for finding the first position where the target could be inserted to maintain sorted order.
```python
import bisect
# Find the index of the first element that is >= target, else return len(arr)
index = bisect.bisect_left(arr, target)

# Specify the range within which to search
start_index = 1
end_index = 4

index = bisect.bisect_left(arr, target, lo=start_index, hi=end_index)
```

[Implementation](https://www.geeksforgeeks.org/problems/implement-lower-bound/1)
[Learning Reference](https://youtu.be/6zhGS79oQ4k?t=454)
### Upper Bound

The upper bound in a binary search is the smallest index `i` in a sorted array such that `arr[i] > target`. If no such index exists, the function returns the size of the array, indicating that all elements in the array are less than or equal to the target. This is useful for finding the first position where an element greater than the target could be inserted to maintain sorted order.
```python
import bisect

index = bisect.bisect_right(arr, target)
```

### Floor & Ceil in Sorted array
![[floor_and_ceil_in_sorted_array.png]]
- We need to return the number here, unlike `index` which we returned in `lower bound`
- `Floor = 20, Ceil = 30`
- `Ceil = Same as lower_bound`
-  [Reference](https://youtu.be/6zhGS79oQ4k)






[Learning Reference](https://youtu.be/6zhGS79oQ4k?t=949)


# References
