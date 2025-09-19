
> [!fail] This note is incomplete.

| LeetCode 36 | [Link](https://leetcode.com/problems/valid-sudoku/description/) |
| ----------- | --------------------------------------------------------------- |
| Status      | **Solved**                                                      |
| Solved      | Mar 20, 2025                                                    |
| Runtime     | 0 ms                                                            |
| Memory      | 17.8 MB                                                         |
| Language    | Python                                                          |


## Problem
Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

**Note:**
- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
- Only the filled cells need to be validated according to the mentioned rules.

> [!info] Example
> **Input:**
> 
> ![[Sudoku-by-L2G-20050714.svg.png|300]]
> 
> `board =`
> `[["5","3",".",".","7",".",".",".","."]`
> `,["6",".",".","1","9","5",".",".","."]`
> `,[".","9","8",".",".",".",".","6","."]`
> `,["8",".",".",".","6",".",".",".","3"]`
> `,["4",".",".","8",".","3",".",".","1"]`
> `,["7",".",".",".","2",".",".",".","6"]`
> `,[".","6",".",".",".",".","2","8","."]`
> `,[".",".",".","4","1","9",".",".","5"]`
> `,[".",".",".",".","8",".",".","7","9"]]`
> 
> **Output:**
> `true`


## 1st attempt

### Idea
- For each of the listed "rule", use algorithm to 