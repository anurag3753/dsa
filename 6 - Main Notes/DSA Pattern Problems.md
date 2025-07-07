
2025-06-28 11:50

Status:

Tags: [[dsa]]
# DSA Pattern Problems

### Approach:

![[pattern_problems.png]]

1. [Print the below Pattern](https://www.naukri.com/code360/problems/star-triangle_6573671)
	[Solution](https://youtu.be/tNm_NNSB3_w?t=1473)
```
   *
  ***
 *****
```

2.  [Print the below Pattern](https://www.naukri.com/code360/problems/reverse-star-triangle_6573685)
	[Solution](https://youtu.be/tNm_NNSB3_w?t=1870)
```
 *****
  ***
   *
```

3. [Print the below Pattern](https://www.naukri.com/code360/problems/binary-number-triangle_6581890)
    [Solution](https://youtu.be/tNm_NNSB3_w?t=2362)
	![[question_dsa_pattern1.png]]
- **Idea to flip bits:**
	- Assume `initial_value=1`
	- Updated Initial Value: `initial_value = 1 - initial_value`

3. [Print the below Pattern](https://www.naukri.com/code360/problems/star-diamond_6573686)
    [Solution](https://youtu.be/tNm_NNSB3_w?t=2056)
![[question_dsa_pattern2.png]]
- Divide it into 2 parts and work on each part.
- Observe here both halves are completely mirror image of each other

4. [Print the below Pattern](https://www.naukri.com/code360/problems/rotated-triangle_6573688)
    [Solution](https://youtu.be/tNm_NNSB3_w?t=2112)
![[question_dsa_pattern3.png]]
- It is a symmetrical pattern. Unlike the above example question.
- Here, rule number 4 from our notes will be applicable.
- Formula for decreasing `2*n - i - 1`

4. [Print the below Pattern](https://www.naukri.com/code360/problems/alpha-hill_6581921)
	[Solution](https://youtu.be/tNm_NNSB3_w?t=3282)
![[question_dsa_pattern4.png]]
- We can keep printing ABC. But somehow in middle we, need to break it and print it in reverse

 5. [Print the below Pattern]()
	[Solution](https://youtu.be/tNm_NNSB3_w?t=4349)
- **I solved it, but look at its solution, I learned something new**
- One way, to think the below pattern it, we need to print a square, and we need to fill the `*` only at boundaries.

![[question_dsa_pattern5.png]]

6. [Print the below Pattern](https://www.naukri.com/code360/problems/ninja-and-the-number-pattern-i_6581959)
   [Solution](https://youtu.be/tNm_NNSB3_w?t=4541)
- **This you will not get in the first go.**
- You need to subtract `n`.
# References
