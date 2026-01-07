---
title: Binary Search
publish: "true"
---  

File Created: 2026-01-06 11:00

Binary Search is a searching [[Algorithms|algorithm]] applied to an ordered array of elements. The idea is that instead of iterating through, or searching the entire array for some value `x`, one might be able to take advantage of the ordered nature of the array, and split it into halves, one of which it will continue splitting, and the other which will be discarded. This occurs until we eventually converge on the value we are searching for. Note that this takes O(log N), which is faster than the the O(N) time it takes to fully search an array.  

![[file-20260106125349484.png]] 

**Conditions to Use Binary Search Algorithm:**
- The data structure is ordered.
- Time to fetch any element is O(1).[^1]

**Binary Search Algorithm:**
1. Divide the ordered array into halves by finding the `midpoint`.
2. Compare `midpoint` to `x`, the value you are searching for.
	1. If `x == midpoint`, return the index.
	2. If `midpoint < x` continue the process on the left half.
	3. If `midpoint > x` continue the process on the right half.
3. Continue splitting until the desired value is found or the entire array is exhausted.  

**Iterative Algorithm: O(Log N) Time and O(1) Space** 
```python
def binarysearch(arr, x):
	low = 0
	high = len(arr) - 1
	while (low <= high):
		#calculate the midpoint
		mid = (high + low)//2
		
		#check if midpoint is desired value
		if (arr[mid] == x):
			return mid
		
		#search upper half
		elif (arr[mid] < x):
			low = mid + 1
			
		#search lower half	
		else:
			high = mid - 1
			
	#value must not exist inside array
	return -1
```  

Below is the [[Recursion|recursive]] implementation.  

**Recursive Algorithm: O(Log N) Time and O(Log N) Space**[^2]

```python
def binarysearch(l, r, arr, x):
	if (low > high):
		return -1
	
	mid = (high + low)//2
	
	if (arr[mid] == x):
		return mid
		
	elif (arr[mid] < x):
		return binarysearch(l, mid + 1, arr, x)
	
	else:
		return binarysearch(mid - 1, h, arr, x)
```  

Thank you for reading! I hope you learned something useful!  

# References  

[BinarySearch: GeeksForGeeks](https://www.geeksforgeeks.org/dsa/binary-search/)

[^1]: This means you can't perform binary search on a linked list, since searching is sequential, and the time to search is O(N).  

[^2]: Notice that the iterative implementation is more space efficient than the recursive implementation. Interesting!

