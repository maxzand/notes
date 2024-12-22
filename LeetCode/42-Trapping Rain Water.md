---
created: 2024-12-22
modified: 
completed: true
leetcode-index: 42
link: https://leetcode.com/problems/trapping-rain-water
difficulty: Hard
tags:
  - leetcode/array
  - leetcode/two-pointers
  - leetcode/dynamic-programming
  - leetcode/stack
  - leetcode/monotonic-stack
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Trapping Rain Water

## Problem Statement
Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

 

>[!Example]+ Example 1
>![](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png)
>
>**Input**: `height = [0,1,0,2,1,0,1,3,2,1,2,1]`
>**Output**: `6`
>**Explanation**:
>The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. 

>[!Example]+ Example 2
>**Input**: `height = [4,2,0,3,2,5]`
>**Output**: `9
`

>[!warning]+ Constraints
>- `n == height.length`
>
>- `1 <= n <= 2 * 10^4`
>
>- `0 <= height[i] <= 10^5`
## Hints
No hints available.
## Approach

- Use prefix and suffix arrays in order to store the water for calculating the amount of water when i actually loop through
## Solution

```cpp
# Solution
class Solution {
public:
    int trap(vector<int>& height) {
        vector<int> prefix(height.size());
        vector<int> suffix(height.size());
        prefix[0] = height[0];
        suffix[height.size()-1] = height[height.size()-1];
        int trapped = 0;
        for(int i =1; i<height.size(); i++){
            prefix[i] = max(height[i],prefix[i-1]);
        }
        for(int i = height.size()-2; i>=0; i--){
            suffix[i] = max(height[i],suffix[i+1]);
            
        }
        for(int i = 1; i<height.size()-1; i++){
            trapped+= max(min(prefix[i-1],suffix[i+1]) - height[i],0);
        }
        return trapped;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(n)$

## Reflections
- This shouldn't be a hard problem.