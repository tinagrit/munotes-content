
| LeetCode 13 | [Link](https://leetcode.com/problems/roman-to-integer/description/) |
| ----------- | ------------------------------------------------------------------- |
| Status      | **Solved**                                                          |
| Solved      | Mar 20, 2025                                                        |
| Runtime     | 6 ms                                                                |
| Memory      | 18.0 MB                                                             |
| Language    | Python                                                              |


## Problem
Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

|Symbol|Value|
|---|---|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|

For example, `2` is written as `II` in Roman numeral, just two ones added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

> [!info] Example
> **Input:**
> `s = "III"`
> 
> **Output:**
> `3`
> 
> **Explanation:**
> III = 3


## 1st attempt

### Idea
- Create a dictionary from the given table. Lookup keys being the letters, and the values being the corresponding integers.
- Set up an answer integer `final` to `0`
- Iterate each letter in the input string `str`, match the letter with its dictionary value, and add that to `final`
- This should work for all letters, except for its **subtractive** form (see [[12 Integer to Roman]] for more about subtractive forms) 
- For each letter, specifically check if there is a subtractive form. Checking by comparing if:
	- Letter is `I` and follows by `V` or `X`
	- Letter is `X` and follows by `L` or `C`
	- Letter is `C` and follows by `D` or `M`
- If it is a subtractive form, subtract the second letter by the first letter and add the result to `final`
- Before the next iteration, remove the letter from the string
- When the string runs out of letters, return `final`

### Code
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        roman = {
            "I": 1,
            "V": 5,
            "X": 10,
            "L": 50,
            "C": 100,
            "D": 500,
            "M": 1000
        } 
        if s == "": return 0
        final = 0
        
        while len(s) > 0:
            if (
                len(s) > 1 and (
                    (s[0] == "I" and s[1] in ["V","X"]) or
                    (s[0] == "X" and s[1] in ["L","C"]) or
                    (s[0] == "C" and s[1] in ["D","M"])
                )
            ):
                final += (roman[s[1]]-roman[s[0]])
                s = s[2:]
            else:
                final += roman[s[0]]
                s = s[1:]
        return final
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 6 ms
> **Memory:** 17.99 MB

### Reflection
- With the way roman numerals work, I believe that the subtractive form should be specifically handled, which is the only special condition in this algorithm.
- This algorithm is simple and should be robust for any roman numeral <=3999


---

> [!success] I consider this problem solved.

