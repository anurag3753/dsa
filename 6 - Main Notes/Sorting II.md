
2025-07-03 12:10

Status:

Tags: [[dsa]] [[dsa sorting]]
# Sorting II

### Recursive Insertion Sort:
- [Reference URL](https://www.youtube.com/watch?v=uwV80JaZrPs) 
```python
def recursive_insertion_sort(arr, n):
    if n <= 1:
        return
    recursive_insertion_sort(arr, n - 1)
    key = arr[n - 1]
    j = n - 2
    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
        j -= 1
    arr[j+1] = key

arr = [5, 2, 9, 7, 14, 8]
recursive_insertion_sort(arr, len(arr))
print(arr)  # Output: [2, 5, 7, 8, 9, 14]
```
### Recursive Bubble Sort:
- [Reference URL](https://www.youtube.com/watch?v=hM5CppfgoTo)
```python
def recursive_bubble_sort(arr, high):
    if high == 0:
        return
    for i in range(high):
        if arr[i] > arr[i + 1]:
            arr[i], arr[i + 1] = arr[i + 1], arr[i]
    recursive_bubble_sort(arr, high - 1)

arr = [3, 2]
recursive_bubble_sort(arr, 1) # Output: [2, 3]
print(arr)
```
---
### Merge Sort:
- [Reference URL](https://www.youtube.com/watch?v=ogjf7ORKfd8)
- Theme : `Divide and Merge`
- Best Resource for explanation
- Best, Avg, Worst Case - O(nlogn)
- Space Complexity - O(n)
---
### Quick Sort
- Intuition
![[quick_sort.png]]
- [Reference URL](https://www.youtube.com/watch?v=WIrA4YexLRQ)
- [GFG Practice](https://www.geeksforgeeks.org/problems/quick-sort/1)
```python
def partition(arr, low, high):
    pivot = arr[low]
    i = low + 1
    j = high
    while i <= j:
        while i <= high and arr[i] <= pivot:
            i += 1
        while j >= low and arr[j] > pivot:
            j -= 1
        if i < j:
            arr[i], arr[j] = arr[j], arr[i]
    # i crosses j
    arr[low], arr[j] = arr[j], arr[low]
    return j

def quick_sort(arr, low, high):
    if low < high:
        partition_index = partition(arr, low, high)
        quick_sort(arr, low, partition_index - 1)
        quick_sort(arr, partition_index + 1, high)

arr = [8, 2, 5, 9, 14, 7]
quick_sort(arr, 0, 5)
print(arr)  # Output: [2, 5, 7, 8, 9, 14]
```

# References
