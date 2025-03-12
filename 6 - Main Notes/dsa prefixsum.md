2025-01-28 19:20

Status:

Tags: [[dsa array]] [[notes/6 - Main Notes/dsa prefixsum|dsa prefixsum]] [[dsa subarray]]

# Prefix Sum

## Prefix for Arrays

- Any continuous segment of an array starting from index 0 is a prefix.
- Example:
  - Array: [1, 2, 3, 4, 5]
  - Prefixes: [1], [1, 2], [1, 2, 3], [1, 2, 3, 4], [1, 2, 3, 4, 5]

## Prefix Sum

- It is a sum array created from the main array, where `prefix_sum[i]` is the sum of all the elements of the array from 0 to i (inclusive).
- Formula: `prefix_sum[i] = arr[0] + arr[1] + arr[2] + ... + arr[i]`

### How to Compute the Prefix Sum

1. Initialize `prefix_sum[0] = arr[0]`.
2. For each `i` from 1 to n-1:
   - `prefix_sum[i] = prefix_sum[i-1] + arr[i]`

### Subarray Vs Subsequence:

1. subsequence is not continuous
2. where as subarray is continuous

Any subarray sum from (i,j) can we written as:

```python
sum(i,j) = prefix_sum[j] - prefix_sum[i-1] // Reduce the prefix sum of i-1
```

## Questions

- [Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/description/)

## References
