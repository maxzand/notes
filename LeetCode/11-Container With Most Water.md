---
created: 2024-12-21
modified: 
completed: true
leetcode-index: 11
link: https://leetcode.com/problems/container-with-most-water
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/two-pointers
  - leetcode/greedy
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Container With Most Water

## Problem Statement
You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i^th` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return *the maximum amount of water a container can store*.

Notice that you may not slant the container.

 

>[!Example]+ Example 1
>![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)
>
>**Input**: `height = [1,8,6,2,5,4,8,3,7]`
>**Output**: `49`
>**Explanation**:
>The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49. 

>[!Example]+ Example 2
>**Input**: `height = [1,1]`
>**Output**: `1
`

>[!warning]+ Constraints
>- `n == height.length`
>
>- `2 <= n <= 10^5`
>
>- `0 <= height[i] <= 10^4`
## Hints
>[!Hint]- Hint 1
>If you simulate the problem, it will be O(n^2) which is not efficient.

>[!Hint]- Hint 2
>Try to use two-pointers. Set one pointer to the left and one to the right of the array. Always move the pointer that points to the lower line.

>[!Hint]- Hint 3
>How can you calculate the amount of water at each step?
## Approach

- Two pointer approach. Move the pointer with the lower height. If the pointers are equal, it doesn't actually matter because in the next step it will just move the one with the lower height again so they converge to the same solution.
## Solution

```cpp
# Solution
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int maximum = 0;
        while(right>left){
            
            maximum = max(maximum,(right-left)*min(height[right],height[left]));

            if(height[left] > height[right]){
                right--;
            }
            if(height[right] > height[left]){
                left++;
            } else{
                left++;
            }
        }
        return maximum;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(1)$

## Reflections
- Use two pointer when you need pairs of numbers.