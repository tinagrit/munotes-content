
| LeetCode 217 | [Link](https://leetcode.com/problems/contains-duplicate/description/) |
| ------------ | --------------------------------------------------------------------- |
| Status       | **Solved**                                                            |
| Solved       | May 1, 2025                                                           |
| Runtime      | 14 ms                                                                 |
| Memory       | 34.9 MB                                                               |
| Language     | Python                                                                |


## Problem
Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

> [!info] Example
> **Input:**
> `nums = [1,2,3,1]`
> 
> **Output:**
> `true`
> 
> **Explanation:**
> The element 1 occurs at the indices 0 and 3.


## 1st attempt

### Idea
Iterate through the array `nums`: 
- Store the number in a new array `seen`. 
- For each of the following numbers, check if the number is already in the array `seen`.
- If so, then there must be a duplicate and return `true`.
- If not, append that number into the `seen` array and continue.

### Code
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = []
        for num in nums:
            if num not in seen:
                seen.append(num)
            else:
                return True

        return False
```

> [!info] Result
> **Test case:**
> *\[a 99999-element array\]*
> 
> **Output:**
> *Time Limit Exceeded*

### Reflection
- This code should work for all test cases, but 99999 elements probably take too much time for LeetCode to process.
- This is due to the use of the array `seen`. For each iteration, the `if num not in seen` performs a **linear search** on the array `seen`, resulting in the average complexity of $O(n^{2})$


## 2nd attempt

### Idea
Iterate through the array `nums`: 
- Store the number in a new **hash map** `seen`. 
- For each of the following numbers, check if the number is already a key in the hash map `seen`.
- If so, then there must be a duplicate and return `true`.
- If not, append that number into the `seen` hash map and continue.

### Code
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = {}
        for num in nums:
            if num not in seen:
                seen[num] = 1
            else:
                return True

        return False
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime**: 14 ms 
> **Memory**: 34.9 MB

### Reflection
- It is more appropriate to use a **hash map** since it would perform a key search in **constant** time.
	- A hash map parses the **key** into an integer index. This way, it can pretty much immediately calculate the memory location and access the value. 
	- For example, asking if the number `91234` exists in an array vs hash map:
		- **Array**: iterates through each element of the array and return when there is a match
		- **Hash map**: parses `91234` to a memory location, access that memory slot, and return if there is an existing value
- This allows the entire algorithm to be **linear** time $O(n)$, making it way faster than the first approach.


---

> [!success] I consider this problem solved.

