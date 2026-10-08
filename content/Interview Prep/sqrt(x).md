---
title: Sqrt(x)
tags:
  - explorerexclude
publish: "true"
---
File Created: 2026-01-06 02:02  
Last Modified: 2026-01-06 02:02

Tags: [[LeetCode]]

---

**Problem Description:** Given a non-negative integer `x`, return the `sqrt(x)`.  

The constraints are:  

- You **must not use** any built-in exponent function or operator.  
- `0 <= x <= 231 - 1`

---

**Examples:**  

**Example 1:**  

**Input:** x = 4  
**Output:** 2  
**Explanation:** The square root of 4 is 2, so we return 2.  

**Example 2:**  

**Input:** x = 8  
**Output:** 2  
**Explanation:** The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.

---

**Solution:**  There are a few ways one could go about this. There is the most intuitive, but most inefficient way, which is to just iterate through the integers, checking their squares, and when you see $num$ such that $num^2 > x$, you return $num - 1$.  The Python implementation can be seen below.  

```python
num = 0
while((num * num) <= x):
	if ((num * num) == x):
		return num
	num += 1
return num - 1
```

This is logically solid, but there is a similar, much faster way to do it using [[BinarySearch|binary search]]. One will have to define three pointers, `H`, `M`, and `L`, where `H` is initialized to be `x`, `L` to be zero, and `M` to be the midpoint of the two.  

From here, we check to see if the square of `M` is greater than or less than `x`. If it is equal, we just return `M`. If it is less, than we assign `L` to be our sitting version of `M`, leave `H` be, and again assign `M` to be the midpoint between the two. If it is greater, we assign `H` to `M`, leave `L` alone, and then reassign `M` to be the midpoint. This way, we eventually converge to a single number, the breaking condition being that `L == M`. The reasoning behind `L == M` being our breaking condition is because for `x > 2`, we will always converge to two consecutive integers `L` and `H`, of which the floor of the midpoint will be `L`, and thus `L == M`.

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        M = x//2
        L = 0
        H = x
        if (x == 1):
            return 1
        while (M != L):
            if ((M*M) > x):
                H = M
                M = (H + L)//2
            elif ((M*M) < x):
                L = M
                M = (H + L)//2
            else:
                return M
        return M
```

Thanks for reading! Please email me any comments or suggestions at [brianoeaden@gmail.com](mailto:brianoeaden@gmail.com) :)