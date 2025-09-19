
| LeetCode 1 | [Link](https://leetcode.com/problems/two-sum/description/) |
| ---------- | ---------------------------------------------------------- |
| Status     | **Solved**                                                 |
| Solved     | Jan 31, 2025                                               |
| Runtime    | 0 ms                                                       |
| Memory     | 51.6 MB                                                    |
| Language   | JavaScript                                                 |


## Problem
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

> [!info] Example
> **Input:**
> `nums = [2,7,11,15], target = 9`
> 
> **Output:**
> `[0,1]`
> 
> **Explanation:**
> Because `nums[0]` + `nums[1]` = `9`, we return `[0, 1]`.


## 1st attempt

### Idea
- Run a similar iteration algorithm to insertion sort. For each element in the array `nums`, iterate through the rest of the elements
- For example, using a list: `1 2 3 4`, it will iterate through `(1,2)`, `(1,3)`, `(1,4)`, `(2,3)`, `(2,4)`, `(3,4)`.
- This will basically go through **all possible pairs** in the array.
- Add up each pair. If the result is equal to the target, return the two indices.

### Code
```javascript
var twoSum = function(nums, target) {
    for (let i=0; i<nums.length; i++) {
        for (let j=i+1; j<nums.length; j++) {
            if (nums[i]+nums[j] == target) return [i,j];
        }
    }
    return [0,0];
};
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 47 ms
> **Memory:** 49.4 MB

### Reflection
- Since there is a double `for` loop, this is an $O(n^{2})$ algorithm, making it slow and inefficient. 


## 2nd attempt

### Idea
- Instead of matching each and every possible pair, for each element, calculate the `diff` (how far it is to the target)
- Search if the array there exists a `diff`. If so, return both indices

### Code
```javascript
var twoSum = function(nums, target) {
    for (let i=0; i<nums.length; i++) {
        let diff = target - nums[i];
        if (nums.includes(diff)) {
            let diffIndex = nums.indexOf(diff);
            if (diffIndex != i) {
                return [i,diffIndex];
            }
        }
    }
};
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 76 ms
> **Memory**: 49.4 MB

### Reflection
- Although there isn't a double for loop, this algorithm is **worse** than the 1st attempt.
- **Both** `nums.includes(diff)` and `nums.indexOf(diff)` perform **linear** searches in the array, equivalent to **two** `for` loops. This algorithm remains $O(n^{2})$


## 3rd attempt

### Idea
- Similar to what I've done with [[217 Contains Duplicate|217 Contains Duplicate]], to check if something exists in a list (*in this case* `diff`), it is better to use a **hash map**
- Create a hash map `iteration` to store each **element as key** and its index as value
- For each element, calculate the `diff` and search if the `diff` **already exists** in the hash map `iteration`. If so, return the two indices

### Code
```javascript
var twoSum = function(nums, target) {
    let iteration = new Map();
    for (let i=0; i<nums.length; i++) {
        let diff = target - nums[i];
        let getDiff = iteration.get(diff);
        if (getDiff !== undefined) {
            return [i,getDiff];
        } else {
            iteration.set(nums[i],i)
        }
    }
};
```

> [!info] Result
> **All test cases passed.**
> 
> **Runtime:** 0 ms
> **Memory**: 51.6 MB

### Reflection
- This algorithm now runs in a $O(n)$ **linear** time complexity, making it a lot faster and more efficient
- I could have also used the **regular object** in JavaScript (*similar to a dictionary in Python*), although the `Map()` object works similarly


---

> [!success] I consider this problem solved.

