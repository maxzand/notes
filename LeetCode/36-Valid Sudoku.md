---
created: 2024-12-21
modified: 
completed: true
leetcode-index: 36
link: https://leetcode.com/problems/valid-sudoku
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/hash-table
  - leetcode/matrix
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Valid Sudoku

## Problem Statement
Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

	
1. Each row must contain the digits `1-9` without repetition.
	
2. Each column must contain the digits `1-9` without repetition.
	
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

Note:

	
- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
	
- Only the filled cells need to be validated according to the mentioned rules.

 

>[!Example]+ Example 1
>![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)
>
>**Input**: `board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]`
>**Output**: `true
`

>[!Example]+ Example 2
>**Input**: `board = 
[["8","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]`
>**Output**: `false`
>**Explanation**:
>Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid. 

>[!warning]+ Constraints
>- `board.length == 9`
>
>- `board[i].length == 9`
>
>- `board[i][j]` is a digit `1-9` or `'.'`.
## Hints
No hints available.
## Approach

- Intuitive solution, create 3 hash tables and use them to track appearances in rows, columns, and boxes as you iterate over all of them.
## Solution

```cpp
# Solution
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {

            for(int i = 0; i<9; i++){
                unordered_map<char,int> vertical;
                unordered_map<char,int> horizontal;
                for(int j = 0; j<9; j++){
                    if(vertical[board[i][j]] == 1){
                        return false;
                    }else if(board[i][j] != '.'){
                        vertical[board[i][j]] = 1;
                    }
                    if(horizontal[board[j][i]] == 1){
                        return false;
                    }else if(board[j][i] != '.'){
                        horizontal[board[j][i]] = 1;
                    }
                }
            } 
            for(int y = 0; y<3; y++){
                for(int z = 0;z<3;z++){
                    unordered_map<char,int> gridMap;
                    for(int i = z*3; i<z*3+3; i++){
                        for(int j = y*3; j<y*3+3; j++){
                            if(gridMap[board[i][j]] == 1){
                                return false;
                            }else if(board[i][j] != '.'){
                                gridMap[board[i][j]] = 1;
                            }
                        }
                    }
                }
            }
            return true;
    }
};
```

## Complexity Analysis

- Time complexity: $O(1)$ because of fixed size of sudoku board
- Space complexity: $O(1)$ same reason

## Reflections
- After I did the solution I now realize a more readable way to write this would be to instead of declaring three hash tables, declare one hash table and append something to my keys to distinguish between rows, columns, and boxes.