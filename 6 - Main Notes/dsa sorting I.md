

2025-06-05 15:09

Status:

Tags: [[dsa sorting]]


# dsa sorting I


### Selection Sort:
- [url](https://youtu.be/HGk_ypEuS24?t=167)
- **select minimum element & swap**
- Best, Average, Worst Case Time Complexity = O(n2)

### Bubble Sort:
- [url](https://youtu.be/HGk_ypEuS24?t=1061)
- **Pushes the maximum element to the last by adjacent swaps**
- Best Case - O(n) (It occurs when the array is already sorted, use a flag to identify)
- Average, Worst Case - O(n2) (It occurs when the array is reverse sorted)

![[bubble_sort.jpg]]

### Insertion Sort:
- [url](https://youtu.be/HGk_ypEuS24?t=1900)
- **Takes an element and places it in its correct position.**
- Look at the element and then see if it can be swapped with the left side element. If yes, then swap it. Do it till you no longer can swap the element. It also means that you have identified the correct position of the element.
- For every element i under consideration, we can guarantee that (0 to i-1) elements are already sorted.

- Best Case - O(n) (It occurs when the array is already sorted)
- Average, Worst Case - O(n2) (It occurs when the array is reverse sorted)

```python
arr = [6, 2, 9, 4, 3, 8]

def swap(my_list, index1, index2):
    my_list[index1], my_list[index2] = my_list[index2], my_list[index1]

def bubble_sort(arr):
    n = len(arr)
    for i in range(n-1):
        for j in range(n-i-1):
            if arr[j] > arr[j+1]:
                swap(arr, j, j+1)

def selection_sort(arr):
    n = len(arr)
    for i in range(n-1):
        smallest_index, smallest_value = i, arr[i]
        for j in range(i+1, n):
            if arr[j] < smallest_value:
                smallest_value = arr[j]
                smallest_index = j
        swap(arr, i, smallest_index)

def insertion_sort(arr):
    n = len(arr)
    for i in range(1, n): # 1st element is already sorted, Also running from 0 will also work.
        ele = arr[i]
        j = i - 1
        """We need to break from loop, when correct position is found.
        For loop, we need to unnecessary do break etc. Safe to use while loop.
        """
        while j >= 0 and arr[j] > ele:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = ele

def main():
    print("Before Sorting:", arr)
    # bubble_sort(arr)
    # selection_sort(arr)
    # insertion_sort(arr)
    print("After Sorting:", arr)

main()
```

# References

[Striver Sorting I A-Z Sheet](https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/)

