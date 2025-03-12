2025-01-26 21:00

Status: #baby

Tags: [[dsa array]]

# Arrays

## Technique to Approach Problems

1. **General Approach**:

   - This technique works 80% of the time.
   - For specific algorithm problems, use the appropriate algorithm.
   - Useful for finding something in any contiguous ranges in the array.

2. **Finding Pairs**:

   - For problems involving finding two indices (one or all pairs) from the array following some property:
     - Treat each element as the `right` element of the pair.
     - Find an appropriate `left` element such that (left, right) satisfies the property.
     - As we move from left to right in the loop, the data structure only contains elements on the left-hand side.
     - Use the data structure to quickly compute the left elements satisfying the property with the current element.

3. **Subarrays**:
   - A subarray can also be treated as two indices.
   - Use prefix computation for subarrays.
   - To compute for a subarray (i, j), use the prefix computation (0, j) and remove the computation for (0, i-1).

```
for (right=0; right < n; right++) {
    // fixed right, now search for left
    for (left=0; left < right; left++){
        if (left, right) satisfy the property
            ans++
    }
}
```

# References
