
| LeetCode 7 | [Link](https://leetcode.com/problems/reverse-integer/) |
| ---------- | ------------------------------------------------------ |
| Status     | **Solved**                                             |
| Solved     | Feb 14, 2025                                           |
| Runtime    | 68 ms                                                  |
| Memory     | 52.7 MB                                                |
| Language   | JavaScript                                             |


## Problem
Given a signed 32-bit integer `x`, return `x` _with its digits reversed_. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

> [!info] Example
> **Input:**
> `x = 123`
> 
> **Output:**
> `321`


## 1st attempt

### Idea
- Reverse the integer recursively
	- Split the integer `x` into the last digit, and everything else
	- the "everything else" `xExceptLastDigit` is the floor division `Math.floor(x/10)`
	- the last digit is `(x - (xExceptLastDigit * 10))`
	- return the concatenation of the last digit, and this recursive function taking in `xExceptLastDigit`

### Code
```javascript
var reverse = function(x) {
    let result = 0;

    if (x<0) result = Number("-"+recursiveReverse(Math.abs(x),0));
    else result = Number(recursiveReverse(x,0));

    if (result<=(2**31 -1) && result>=((-2)**31)) return result;
    else return 0;
};

var recursiveReverse = function(x,n) {
    let xExceptLastDigit = Math.floor(x/10);
    if (xExceptLastDigit == 0) {return "" + x;}
    let result = "" + (x - (xExceptLastDigit * 10));
    n++;
    return result + recursiveReverse(xExceptLastDigit,n);
};
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 80 ms
> **Memory:** 53.32 MB

### Reflection
- While this algorithm works well, it relies on recursion. There should be a more efficient way through regular iteration.
- Since I got this idea from the recursive palindrome checker, each digit has to be converted into a string. It would have been easier to convert the entire integer into a string and deal with that.


## 2nd attempt

### Idea
- Instead of doing it recursively, use a while loop and break when there are no more digits left to reverse
- For the first iteration, `result` will be `0`.
- For each iteration:
	- Multiply `result * 10` to "shift" the result left by one digit, leaving the last digit of `result` to be `0`.
	- The last digit `lastdigit` of `x` is taken using `x % 10` instead of the more complicated arithmetic.
	- Add `lastdigit` to `result`. (instead of doing concatenation)
	- Floor divide `x = Math.floor(x/10)` and continue with the loop

### Code
```javascript
var reverse = function(x) {
    let negative = false;
    let result = 0;
    
    if (x < 0) {
        negative = true;
        x *= -1;
    }

    while(true) {
        if (x<=0) break;
        let lastdigit = x % 10;
        result *= 10;
        result += lastdigit;
        x = Math.floor(x/10);
    }

    if (result > 2147483647) return 0;
    if (negative) result *= -1;
    return result;
};
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 68 ms
> **Memory:** 52.68 MB

### Reflection
- This algorithm runs faster, is cleaner, and possibly easier to understand than the recursive-string approach.
- I believe that it is better to not convert an integer to a string when it is not necessary. This problem is easily solved without having to do so.


---

> [!success] I consider this problem solved.

