---
created: 2025-01-06
modified: 
completed: true
leetcode-index: 22
link: https://leetcode.com/problems/generate-parentheses
difficulty: Medium
tags:
  - leetcode/string
  - leetcode/dynamic-programming
  - leetcode/backtracking
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Generate Parentheses

## Problem Statement
Given `n` pairs of parentheses, write a function to *generate all combinations of well-formed parentheses*.

 

>[!Example]+ Example 1
>**Input**: `n = 3`
>**Output**: `["((()))","(()())","(())()","()(())","()()()"]
`

>[!Example]+ Example 2
>**Input**: `n = 1`
>**Output**: `["()"]
`

>[!warning]+ Constraints
>- `1 <= n <= 8`
## Hints
No hints available.
## Approach

- 
## Solution

```cpp
# Solution
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        dfs(0,0,"",n,result);
        return result;
    }
    void dfs(int open,int closed,string s,int stop, vector<string>& result) {
        if(open == closed && open + closed == stop*2){
            result.push_back(s);
            return;
        }
        if(open<stop){
            dfs(open+1,closed,s + "(", stop, result);
        }
        if(closed<open){
            dfs(open,closed+1,s+")",stop,result);
        }
    }
};
```

## Complexity Analysis

- Time complexity: $O(N*2^N)$
- Space complexity: $O(N)$

## Reflections
-  Honestly, I had to read the solution for this
- I don't have enough experience with dfs to be able to implement it on a new problem. I need to practice using dfs.