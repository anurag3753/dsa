
2025-01-28 19:20

Status:

Tags: [[dsa array]]


# dsa prefix

Prefix for arrays:
    Any continuous segment of array starting from index 0 is a prefix.
    Example:
        Array = [1,2,3,4,5]
        Prefixes:
            [1], [1,2], [1,2,3], [1,2,3,4], [1,2,3,4,5]


Prefix sum:
    It is a sum array that we create from the main array, where prefix_sum[i] = sum of all the elements of the array from 0 to i (inclusive)
    prefix_sum[i] = arr[0] + arr[1] + arr[2] + arr[3] ....... + arr[i]

How to compute the prefix sum ?
	prefix_sum[i] = prefix_sum[i-1] + arr[i]
	Populate prefix_sum[0] = arr[0] separately.

Questions:
	[Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/description/)

References
