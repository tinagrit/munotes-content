
| LeetCode 347 | [Link](https://leetcode.com/problems/top-k-frequent-elements/) |
| ------------ | -------------------------------------------------------------- |
| Status       | <span style="color:#FF9B45">Partially Solved</span>            |
| Solved       | May 6, 2025                                                    |
| Runtime      | 46 ms                                                          |
| Memory       | 21.0 MB                                                        |
| Language     | Python                                                         |


## Problem
Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.

> [!info] Example
> **Input:**
> `nums = [1,1,1,2,2,3]`, `k = 2`
> 
> **Output:**
> `[1,2]`


## 1st attempt

### Idea
- Create a hash map `maps` and an array `out`
- Iterate through the array `nums`, and store the frequency of each number in the hash map `maps`
- Using a similar algorithm to **selection sort**:
	- iterate through the hash map `maps`
	- append the most frequent entry to `out`
	- remove that entry from the hash map. 
- Iterate `k` many times.

### Code
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        maps = {}
        out = []

        for num in nums:
            if num not in maps:
                maps[num] = 1
            else:
                maps[num] += 1
            
        for i in range(k):
            currentMax = 0
            currentMaxKey = 0
            for key,value in maps.items():
                if value > currentMax:
                    currentMax = value
                    currentMaxKey = key
            del maps[currentMaxKey]
            out.append(currentMaxKey)
        
        return out
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 46 ms
> **Memory:** 21 MB


### Reflection
- This algorithm works well. The only issue is that the **double** `for` loop to find the largest frequency runs on an $O(n^{2})$ time complexity. 
- The goal is to utilize the **constant search time** of hash maps to reduce this algorithm to a constant $O(n)$ complexity


---

> [!question] Since I believe that this algorithm can be more efficient, I consider this problem partially solved.

