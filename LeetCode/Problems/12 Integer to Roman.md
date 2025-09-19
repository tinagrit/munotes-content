
| LeetCode 12 | [Link](https://leetcode.com/problems/integer-to-roman/description/) |
| ----------- | ------------------------------------------------------------------- |
| Status      | **Solved**                                                          |
| Solved      | Aug 8, 2025                                                         |
| Runtime     | 3 ms                                                                |
| Memory      | 17.9 MB                                                             |
| Language    | Python                                                              |


## Problem
Seven different symbols represent Roman numerals with the following values:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

Roman numerals are formed by appending the conversions of decimal place values from highest to lowest. Converting a decimal place value into a Roman numeral has the following rules:

- If the value does not start with 4 or 9, select the symbol of the maximal value that can be subtracted from the input, append that symbol to the result, subtract its value, and convert the remainder to a Roman numeral.
- If the value starts with 4 or 9 use the **subtractive form** representing one symbol subtracted from the following symbol, for example, 4 is 1 (`I`) less than 5 (`V`): `IV` and 9 is 1 (`I`) less than 10 (`X`): `IX`. Only the following subtractive forms are used: 4 (`IV`), 9 (`IX`), 40 (`XL`), 90 (`XC`), 400 (`CD`) and 900 (`CM`).
- Only powers of 10 (`I`, `X`, `C`, `M`) can be appended consecutively at most 3 times to represent multiples of 10. You cannot append 5 (`V`), 50 (`L`), or 500 (`D`) multiple times. If you need to append a symbol 4 times use the **subtractive form**.

Given an integer, convert it to a Roman numeral.

> [!info] Example
> **Input:**
> `num = 3749`
> 
> **Output:**
> `"MMMDCCXLIX"`
> 
> **Explanation:**
> 3000 = MMM as 1000 (M) + 1000 (M) + 1000 (M)
 700 = DCC as 500 (D) + 100 (C) + 100 (C)
  40 = XL as 10 (X) less of 50 (L)
   9 = IX as 1 (I) less of 10 (X)
*Note*: 49 is not 1 (I) less of 50 (L) because the conversion is based on decimal places


## 1st attempt

### Idea
- Create a dictionary from the given table. Lookup keys being the integers, and the values being the letters.
- Set up an empty `roman` string.
- Iterate through each **digit** of the integer, going from left to right. The digit's corresponding *log10 value* (ten to the power of) is also stored.
```
Example integer: 35825

Digits:            3   5   8   2   5
Log10 value:       4   3   2   1   0
```
$$
35,825 = (3\cdot10^4)+(5\cdot 10^{3})+(8\cdot 10^{2})+(2\cdot 10)+(5)
$$
- **If the digit is** `1 2 3` (*additive*), it will be 1, 2, or 3 instances of `I`, `X`, `C`, `M`, depending on the *log10 value*. Loop `digit` many times to add to the `roman` string.
- **If the digit is** `4` (*subtractive*), it will be one of: `IV`, `XL`, `CD`. Add the *log10 value* to `roman` (either: `I`, `X`, `C`), then add the $5\times$*log10 value* (either `V`,`L`,`D`).
- **If the digit is** `5 6 7 8` (*additive with 5 in front*), for example, `7` is `5+2`→`VII`. Add the $5\times$*log10 value* (either `V`,`L`,`D`) to `roman`. Then, add 1, 2, or 3 instances of `I`, `X`, `C`, `M`, depending on the *log10 value* by looping `digit-5` many times to add to the `roman` string. 
- **If the digit is** `9` (*subtractive*), it will be one of: `IX`, `XC`, `CM`. Add the *log10 value* to `roman` (either: `I`, `X`, `C`), then add the *log10 value* $+1$ (either `X`, `C`, `M`).
- Before the next iteration, **remove** that digit from the integer.
- Stop the loop and return `roman` when `num == 0`

### Code
```python
class Solution:
    def intToRoman(self, num: int) -> str:
        roman = ""    
        intToRoman = {
            1: "I",
            5: "V",
            10: "X",
            50: "L",
            100: "C",
            500: "D",
            1000: "M"
        }    
        while num > 0:
            tenToThePowerOf = int(math.log10(num))
            digit = int(num / (10 ** tenToThePowerOf))

            if digit < 4 and digit > 0:
                for i in range(0,digit):
                    roman += intToRoman[10 ** tenToThePowerOf]
            elif digit == 4:
                roman += intToRoman[10 ** tenToThePowerOf]
                roman += intToRoman[5 * (10 ** tenToThePowerOf)]
            elif digit > 4 and digit < 9:
                roman += intToRoman[5 * (10 ** tenToThePowerOf)]
                for i in range(6, digit+1):
                    roman += intToRoman[10 ** tenToThePowerOf]
            elif digit == 9:
                roman += intToRoman[10 ** tenToThePowerOf]
                roman += intToRoman[10 ** (tenToThePowerOf + 1)]

            num = num - (digit*(10 ** tenToThePowerOf))
    
        return roman
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 6 ms
> **Memory:** 17.60 MB

### Reflection
- This algorithm works well and should be robust for any integers <3999.
- Since hash maps are really fast, room for improvement includes adding more values to the dictionary, for example, `900`→`CM` and `40`→`XL`. This could save time from the conditionals and calculations.


## 2nd attempt

### Idea
- New dictionary with more values added: (*real code is in descending order*)

| Key     | Value  |
| ------- | ------ |
| 1       | I      |
| **4**   | **IV** |
| 5       | V      |
| **9**   | **IX** |
| 10      | X      |
| **40**  | **XL** |
| 50      | L      |
| **90**  | **XC** |
| 100     | C      |
| **400** | **CD** |
| 500     | D      |
| **900** | **CM** |
| 1000    | M      |

- Instead of picking each digit, we can iterate through the dictionary in **descending order**.
- Find the **largest value** that can be subtracted from the integer without it going negative. (Conditional `num >= key`)
	- Repeat the check with while loop, since letters can repeat. For example, `300`→`CCC`.
	- Add the dictionary `value` to `roman`, and subtract the `key` from the integer.
- This `for` iteration should repeat until there are multiple (*or none*) of `I`. Then, the integer should be `0`.
- Return `roman`

### Code
```python
class Solution:
    def intToRoman(self, num: int) -> str:
        roman = ""    
        intToRoman = {
            1000: "M",
            900: "CM",
            500: "D",
            400: "CD",
            100: "C",
            90: "XC",
            50: "L",
            40: "XL",
            10: "X",
            9: "IX",
            5: "V",
            4: "IV",
            1: "I"
        }

        for key, value in intToRoman.items():
            while num >= key:
                roman += value
                num = num - key
        return roman
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 3 ms
> **Memory:** 17.90 MB

### Reflection
 - This algorithm cuts the runtime by half, by using more of **defined hash map** values rather than manual calculation inside.
 - This may be cleaner and easier to understand as well.


---

> [!success] I consider this problem solved.
