---
publish: "true"
---
# Length of Last Word

File Created: 2026-01-03 13:15
Last Modified: 2026-01-03 13:15

Tags: [[LeetCode]]

---

**Problem Description:** The problem is a fairly simple one to conceptualize. You are only required to, in a string *s* of words and spaces, return the length of the LAST word in the string. 

The only real trick here is that there may be additional spaces at the end of the string, after the last word. 

The constraints are:

$1 \leq \textit{s} \leq 10^4$  
*s* contains only characters and ' ', and contains at *least* one word

---

**Examples:**

s = "Hello World", length = 5  
s = "Hello World   ", length = 5  
s = "Hello, my    name   is  Aden Briano", length = 6  
s = "a", length = 1

---

**Solution:** So, there are a couple ways one could go about this. We could simply iterate through the string, incrementing a counter at each character, and resetting at each space. Note that this would require additional logic to account for the case that there are additional spaces following the last word in the string[^1], and is overall inefficient.

	Sidenote: This solution has O(n) time complexity, like the more "efficient" solution I'm about to present.

Instead of iterating through the string starting from the beginning, we can set a pointer at the end of the string. In the event that we encounter a ' ' character, we simply decrement the pointer. Once we finally encounter an alphabetical character, we can begin incrementing a counter, and decrementing our pointer until we encounter a second ' ', or reach the beginning of the string. Note that we need to check that right >= 0 so that we do not risk indexing out of bounds. 

This way, we don't ALWAYS have to iterate through the entire string, only in the worst case. In the worst case, the time complexity is also O(n), and since we only consider the worst case when determining time complexity, we can say that the two solutions presented on this page have the same time complexity.

The solution, in Python, would look like:

```python
def lengthOfLastWord(self, s: str) -> int:
		right = len(s) - 1
        length = 0
        while (s[right] == " "):
            right -= 1
        while (s[right] != " " and right >= 0):
            right -= 1
            length += 1
        return length
```


Thanks for reading! Please email me any comments or suggestions at [brianoeaden@gmail.com](mailto:brianoeaden@gmail.com) :)

[^1]: You could store an additional counter variable which stores the previously reset counter variable. This way, if the final character in the string is a ' ', you can return the counter copy variable.
