---
created: 2024-12-21
modified: 
completed: true
leetcode-index: 167
link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/two-pointers
  - leetcode/binary-search
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Two Sum II - Input Array Is Sorted

## Problem Statement
Given a 1-indexed array of integers `numbers` that is already *sorted in non-decreasing order*, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index<sub>1</sub>]` and `numbers[index<sub>2</sub>]` where `1 <= index<sub>1</sub> < index<sub>2</sub> <= numbers.length`.

Return* the indices of the two numbers, *`index<sub>1</sub>`* and *`index<sub>2</sub>`*, added by one as an integer array *`[index<sub>1</sub>, index<sub>2</sub>]`* of length 2.*

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

 

>[!Example]+ Example 1
>**Input**: `numbers = [<u>2</u>,<u>7</u>,11,15], target = 9`
>**Output**: `[1,2]`
>**Explanation**:
>The sum of 2 and 7 is 9. Therefore, index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2]. 

>[!Example]+ Example 2
>**Input**: `numbers = [<u>2</u>,3,<u>4</u>], target = 6`
>**Output**: `[1,3]`
>**Explanation**:
>The sum of 2 and 4 is 6. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 3. We return [1, 3]. 

>[!Example]+ Example 3
>**Input**: `numbers = [<u>-1</u>,<u>0</u>], target = -1`
>**Output**: `[1,2]`
>**Explanation**:
>The sum of -1 and 0 is -1. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2]. 

>[!warning]+ Constraints
>- `2 <= numbers.length <= 3 * 10^4`
>
>- `-1000 <= numbers[i] <= 1000`
>
>- `numbers` is sorted in non-decreasing order.
>
>- `-1000 <= target <= 1000`
>
>- The tests are generated such that there is exactly one solution.
## Hints
No hints available.
## Approach

- 
## Solution

```cpp
# Solution
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left = 0;
        int right = numbers.size()-1;
        while(left<right){
            int sum = numbers[left] + numbers[right];
            if(sum == target){
                return {left+1,right+1};
            }
            if(sum<target){
                left++;
            }
            if(sum>target){
                right--;
            }
        }
        return {};
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$ , The array is only traversed at most once
- Space complexity: $O(n)$ , Only a few ints used. Doesn't scale.

## Reflections
- Use two pointers when it's easy to traverse between sorted arrays/strings or symmetric things