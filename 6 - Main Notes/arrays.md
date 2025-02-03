
2025-01-26 21:00

Status: #baby 

Tags: [[dsa array]]


# arrays


2025-01-27 13:38

Status:

Tags:


# arrays


A technique to approach problems: 
    - (80% of the time it works)
    - At other times it could be some specific algorithm problem, which we should solve using that algorithm only.
    - Can be used whenever we need to find something for any contiguous ranges in the array.

Whenever you have a problem which involves finding 2 indices (one or all pairs) from the array following some property, you can solve it by treating each element
as the `right` element of the pair and trying to find an appropriate `left` element such that (left, right) satisfies the property. As we are moving from left to 
right in the loop, when we reach any element the data structure only contains elements on the left hand side. So using the data structure, we should be able to quickly
compute the left elements satisfying the property with the current element.

Tip: A subarray can also be treated as 2 indices, in case of subarrays we use the prefix computation as well. To compute for a subarray (i, j), we can use the prefix computation
(0, j) and from that remove the computation for (0, i-1)

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
