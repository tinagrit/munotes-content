
| LeetCode 9 | [Link](https://leetcode.com/problems/palindrome-number/description/) |
| ---------- | -------------------------------------------------------------------- |
| Status     | **Solved**                                                           |
| Solved     | Mar 20, 2025                                                         |
| Runtime    | 23 ms                                                                |
| Memory     | 12.3 MB                                                              |
| Language   | Python                                                               |


## Problem
Given an integer `x`, return `true` _if_ `x` _is a_ _**palindrome**__, and_ `false` _otherwise_.

> [!info] Example
> **Input:**
> `x = 121`
> 
> **Output:**
> `true`
> 
> **Explanation:**
> 121 reads as 121 from left to right and from right to left.


## 1st attempt

### Idea
- I believe that the best way is to reverse the integer `x`, then compare if the original `==` reversed
- Using a somewhat simplified logic from [[7 Reverse Integer]], set `result` to `0` and in a while loop:
	- Multiply `result * 10` to "shift" the result left by one digit, leaving the last digit of `result` to be `0`.
	- The last digit `lastdigit` of `x` is taken using `x % 10` instead of the more complicated arithmetic.
	- Add `lastdigit` to `result`. (instead of doing concatenation)
	- Floor divide `x = Math.floor(x/10)` and continue with the loop
- Compare the two integers

### Code
```python
class Solution(object):
    def isPalindrome(self, x):
        if x < 0: return False
        if x == 0: return True

        originalInt = x
        reversedInt = 0

        while x > 0:
            digit = x % 10
            x = x // 10
            reversedInt = (reversedInt * 10) + digit

        if originalInt == reversedInt: return True
        else: return False
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 23 ms
> **Memory:** 12.30 MB

### Reflection
- This algorithm is a continuation of [[7 Reverse Integer]], to compare the original and the reversed to determine if it is a palindrome
- While the runtime is clearly to the right of average, the faster runtime algorithms mostly involve comparing reversed strings. Those may be more efficient, but I still believe that it is logically better to not do the conversion on an integer problem when it is not necessary


---

> [!success] I consider this problem solved.

