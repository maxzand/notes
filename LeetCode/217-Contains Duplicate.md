---
created: 2024-12-18
modified: 
completed: true
leetcode-index: 217
link: https://leetcode.com/problems/contains-duplicate
difficulty: Easy
tags:
  - leetcode/array
  - leetcode/hash-table
  - leetcode/sorting
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Contains Duplicate

## Problem Statement
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

 

>[!Example]+ Example 1
>**Input**: `<span class="example-io">nums = [1,2,3,1]</span>`
>**Output**: `<span class="example-io">true</span>`
>**Explanation**: `The element 1 occurs at the indices 0 and 3.
></div>`

>[!Example]+ Example 2
>**Input**: `<span class="example-io">nums = [1,2,3,4]</span>`
>**Output**: `<span class="example-io">false</span>`
>**Explanation**: `All elements are distinct.
></div>`

>[!Example]+ Example 3
>**Input**: `<span class="example-io">nums = [1,1,1,3,3,4,3,2,4,2]</span>`
>**Output**: `<span class="example-io">true</span>
</div>`

>[!warning]+ Constraints
>- `1 <= nums.length <= 10^5`
>
>- `-10^9 <= nums[i] <= 10^9`
## Hints
No hints available.
## Approach

- 
## Solution

```cpp
# Solution
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        std::unordered_map<int,int> map;
        for(int i=0;i<nums.size();i++) {
            if(map[nums[i]] == 1) {
                return true;
            }else{
                map[nums[i]] = 1;
            }
        }
        return false;
    }
};
```

## Complexity Analysis

- Time complexity:  O(n)
- Space complexity: O(n)

## Reflections

Basically just [[1-Two Sum |TwoSum]] but easier. Instead of searching for what we need, we can create a hashtable in order to find what we need.