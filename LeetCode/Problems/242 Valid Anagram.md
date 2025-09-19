
| LeetCode 242 | [Link](https://leetcode.com/problems/valid-anagram/description/) |
| ------------ | ---------------------------------------------------------------- |
| Status       | **Solved**                                                       |
| Solved       | May 1, 2025                                                      |
| Runtime      | 11 ms                                                            |
| Memory       | 17.8 MB                                                          |
| Language     | Python                                                           |


## Problem
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

> [!info] Example
> **Input**:
> `s = "anagram"`, `t = "nagaram"`
> 
> **Output**:
> `true`


## 1st attempt

### Idea
- Create two hash maps, one for `s` and `t`
- For both strings, iterate through each letter to count the number of instances of each letter
	- For example, for a string `"hello"`, we should get the following in the hash map:
	- `{"h":1, "e":1, "l":2, "o":1}`
- Iterate through the keys of the hash map for `s`:
	- Return `false` if the key doesn't exist in the hash map for `t`, or if the value of the key in `s` is different from the value of the key in `t`

### Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        sCounter = {}
        tCounter = {}

        for letter in s:
            if letter not in sCounter:
                sCounter[letter] = 1
            else:
                sCounter[letter] += 1

        for letter in t:
            if letter not in tCounter:
                tCounter[letter] = 1
            else:
                tCounter[letter] += 1

        for letter in sCounter:
            if letter not in tCounter or sCounter[letter] != tCounter[letter]:
                return False
        
        return True
```

> [!info] Result
> **Test case:**
> `s = "a"`, `t = "ab"`
> 
> **Output:**
> `true`
> 
> **Expected:**
> `false`

### Reflection
- This code mostly works, except for the comparison logic at the end.
- The logic "*Return* `false` *if the key doesn't exist in the hash map for* `t`*, or if the value of the key in* `s` *is different from the value of the key in* `t`" is flawed because, as shown in the test case, it would **only check for letters in the** `s` **hash map**.
- If the string `t` has extra letters not in `s`, it would return a **false positive**.


## 2nd attempt

### Idea
- Create two hash maps, one for `s` and `t`
- For both strings, iterate through each letter to count the number of instances of each letter
- Use Python's **built-in** operator to **compare** hash maps, return `true` if the two hash maps are the same

### Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        sCounter = {}
        tCounter = {}

        for letter in s:
            if letter not in sCounter:
                sCounter[letter] = 1
            else:
                sCounter[letter] += 1

        for letter in t:
            if letter not in tCounter:
                tCounter[letter] = 1
            else:
                tCounter[letter] += 1

        if tCounter == sCounter:
            return True
        else:
            return False
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime**: 11 ms 
> **Memory**: 17.8 MB

### Reflection
- To avoid the flawed custom logic, I learned that Python has a **built-in operator** to compare hash maps
- Not only this works, the code is a lot cleaner as well


---

> [!success] I consider this problem solved.

