---
title: Add Binary
publish: "true"
---
File Created: 2026-01-05 15:54  
Last Modified: 2026-01-05 15:54

Tags: [[LeetCode]]

---

**Problem Description:** In this problem, you are provided with two binary strings `a` and `b`, of which you need to return the sum, also as a binary string.

The constraints are:  

- `1 <= a.length, b.length <= 104`
- `a` and `b` consist only of `'0'` or `'1'` characters.
- Each string does not contain leading zeros except for the zero itself.

---

**Examples:**  

**Example 1:**  

**Input:** a = "11", b = "1"  
**Output:** "100"  

**Example 2:**  

**Input:** a = "1010", b = "1011"  
**Output:** "10101"  

**Example 3:**

**Input:** a = "1111", b = "111"  
**Output:** "10110"  

**Example 4:**  

**Input:** a = "1", b = "1"  
**Output:** "10" 

---

**Solution:** There exist functions within Python that would allow us to simply convert each string into integers, sum them, and then convert the sum into a binary string. We aren't interested in this however, as it does not employ much of the actual binary addition logic.  

Thus, we will model our solution after the binary addition algorithm. In other words, iterate through each operand, add corresponding bits, and generate carry's to be used in further additions if necessary.  

To make our addition a bit easier, we are going to zero-extend our operands to be the same length. This requires performing a check to see which operand is shorter, if any. Before we do so, though, concatenating strings, which we will use for zero-extension, appends to the end of the string. Assuming our MSB is on the left, we will first need to reverse our binary strings before performing our zero-extension. This way, our zeros are precisely where they need to be.  

Iterating through our binary strings and performing our addition will be easier if both strings are reversed anyway, so we'll go ahead and just reverse both before doing anything.  

Now that our strings are reversed and are the same length, we can perform our addition. To do so, we will initialize a `carry` variable, which we will check at each bit addition. If `carry == 1`, then we will add it the corresponding bit in `b`. If the bit in `b` is 1, then we will generate another carry. The logic then looks like[^1]:  

	If carry == 1
		If b[i] == 1
			=>b[i] = 0
			=>carry = 1
		else:
			=>b[i] = 1
			=>carry = 0
	*perform bitwise addition here*  

Note that any carry generated during the bitwise addition will not clash with our assignment of `carry` in the logic above, since the only case where we might assign `carry = 1` is if both bits in `a` and `b` are 1, in which case our `carry` must be 0.  

The bitwise addition is pretty simple. If `a[i] = b[i] = 1`, then append a 0 to our resultant binary string and generate a carry. If `a[i] = b[i] = 0`, then append a 0 to our resultant binary string. In either of the two last cases: `a[i] = 1 and b[i] = 0` or `a[i] = 0 and b[i] = 1`, we can simply append a 1 to our resultant binary string. We loop through everything described above for the entire length of our operands.  

At the end of our loop, it might be the case that our final bitwise addition yielded a carry, in which case we perform a check and append it to the end of our result. Since we performed our binary addition with reversed operands, we must then reverse our resultant binary string before returning anything.  

Yippee! That should be all! The implementation in Python can be seen below.  

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        carry = 0
        diff = len(a) - len(b)
        result = ""

        a = a[::-1]
        b = b[::-1]
        
        #zero-extend to same length
        if (len(b) < len(a)):
            for i in range(diff):
                b += "0"
        elif (len(a) < len(b)):
            for i in range(-diff):
                a += "0"

        b = list(b)

        #perform addition
        for i in range(len(b)):
            if (carry == 1):
                if b[i] == "1":
                    b[i] = "0"
                    carry = 1
                else:
                    b[i] = "1"
                    carry = 0
            if (b[i] == "1" and a[i] == "1"):
                result += "0"
                carry = 1
            elif (b[i] == "0" and a[i] == "0"):
                result += "0"
            else:
                result += "1"

        #add final carry, if it exists
        if carry == 1:
            result += "1"

        result = result[::-1]
        return result
```

Thanks for reading! Please email me any comments or suggestions at [brianoeaden@gmail.com](mailto:brianoeaden@gmail.com) :)


[^1]: To perform the following assignment, we will need to convert our `b` binary string into a list.
