
| LeetCode 49 | [Link](https://leetcode.com/problems/group-anagrams/description/) |
| ----------- | ----------------------------------------------------------------- |
| Status      | **Solved**                                                        |
| Solved      | May 5, 2025                                                       |
| Runtime     | 55 ms                                                             |
| Memory      | 21.5 MB                                                           |
| Language    | Python                                                            |


## Problem
Given an array of strings `strs`, group the anagrams together. You can return the answer in **any order**.

> [!info] Example
> **Input:**
> `strs = ["eat","tea","tan","ate","nat","bat"]`
> 
> **Output:**
> `[["bat"],["nat","tan"],["ate","eat","tea"]]`
> 
> **Explanation:**
> - There is no string in `strs` that can be rearranged to form `"bat"`.
> - The strings `"nat"` and `"tan"` are anagrams as they can be rearranged to form each other.
> - The strings `"ate"`, `"eat"`, and `"tea"` are anagrams as they can be rearranged to form each other.


## 1st attempt

### Idea
- Create a hash map `maps` to store the letter hash maps, and a hash map `out` to store the output
- For each word in `strs`, using a similar algorithm to [[242 Valid Anagram|242 Valid Anagram]], create a hash map to count the number of instances of each letter
	- For example, for a string `"hello"`, we should get the following in the hash map:
	- `{"h":1, "e":1, "l":2, "o":1}`
- Store the hash map in the array `maps`, and the `[`string`]` in the array `out`
- For the remaining strings, do a linear search of `maps` to see if an anagram exists.
	- If so, append the string in the same group as the anagram in `out`
	- If not, store the hash map in the array `maps`, and the `[`string`]` in the array `out`

### Code
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        maps = []
        out = []

        for word in strs:
            found = False
            wordmap = {}
            for letter in word:
                if letter not in wordmap:
                    wordmap[letter] = 1
                else:
                    wordmap[letter] += 1
            for i in range(len(maps)):
                if wordmap == maps[i]:
                    out[i].append(word)
                    found = True
                    break
            if not found:
                out.append([word])
                maps.append(wordmap)
        return out
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 1712 ms
> **Memory:** 22.38 MB

### Reflection
- Similar to what happened in [[217 Contains Duplicate|217 Contains Duplicate]], the linear search of `maps` makes the algorithm $O(n^{2})$ and slows it down significantly.
- The goal is to find a way to use a similar algorithm, but to utilize a hash map for constant time search for `maps`


## 2nd attempt

### Idea
- It would be nice if a hash map can be a key in another hash map, that way, the `maps` array can be a hash map, with each word maps becoming keys. 
- Instead of using a hash map for each word, we can find a way to **use a string instead**
	- Since there is a limited number of alphabets in the English language, instead of doing `{"a":2, "c":3, "y":1}`, we can do `"2030...010"` to stand for instances of `"abcd...xyz"`
	- This can be used as **keys**, and if this string match, the two words must be anagrams
- For each word in `strs`:
	- If an anagram doesn't exist in `maps`, store the "*instances of each letter*" map as a string in the hash map `maps`, and append the word into `out`. Store the index in `out` as value in the hash map
	- If an anagram exists, append the word into the correct index in `out`

### Code
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        if strs == [""]: return [[""]]
        frequencyMap = {}
        indexCount = 0
        out = []

        for word in strs:
            frequency = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
            for letter in word:
                letterIndex = ord(letter) - ord('a')
                frequency[letterIndex] += 1
            
            frequencyKey = ''.join(str(e) for e in frequency)
            if frequencyKey not in frequencyMap:
                frequencyMap[frequencyKey] = indexCount
                out.append([word])
                indexCount += 1
            else:
                out[frequencyMap[frequencyKey]].append(word)

        return out
```

> [!info] Result
> **Input:**
> `strs = ["bdddddddddd","bbbbbbbbbbc"]`
> 
> **Output:**
> `[["bdddddddddd","bbbbbbbbbbc"]]`
> 
> **Expected:**
> `[["bbbbbbbbbbc"],["bdddddddddd"]]`

### Reflection
- This algorithm works most of the time (123/126 passed), but in the shown test case, it groups the two strings that are definitely not anagrams.
- Investigating this further, we found that the map strings for:
	- `"bdddddddddd"` → `010100...` 
	- `"bbbbbbbbbbc"` → `010100...`
- While the map strings are identical, they mean different things:
	- `"bdddddddddd"` → `0 1 0 10 0 ...` 
	- `"bbbbbbbbbbc"` → `0 10 1 0 0 ...` 
- This algorithm **cannot handle** more than one digit of the number of letters.


## 3rd attempt

### Idea
- Use the same algorithm as the [[#2nd attempt]], except add a separating `/` in between each letter. 
- Instead of `"2030...010"` for `"abcd...xyz"`, we will have `"2/0/3/0/.../0/1/0"` for `"a/b/c/d/.../x/y/z"`

### Code
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        if strs == [""]: return [[""]]
        frequencyMap = {}
        indexCount = 0
        out = []

        for word in strs:
            frequency = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
            for letter in word:
                letterIndex = ord(letter) - ord('a')
                frequency[letterIndex] += 1
            
            frequencyKey = '/'.join(str(e) for e in frequency)
            if frequencyKey not in frequencyMap:
                frequencyMap[frequencyKey] = indexCount
                out.append([word])
                indexCount += 1
            else:
                out[frequencyMap[frequencyKey]].append(word)

        return out
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 55 ms
> **Memory:** 21.5 MB

### Reflection
- The idea we had in the [[#2nd attempt]] was right, except for a small logic error. 
- Compared to the [[#1st attempt]], this "*string as key*" algorithm runs on **linear time** complexity $O(n)$, making it much faster and more efficient


---

> [!success] I consider this problem solved.

