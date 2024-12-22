---
created: 2024-12-21
modified: 
completed: true
leetcode-index: 128
link: https://leetcode.com/problems/longest-consecutive-sequence
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/hash-table
  - leetcode/union-find
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Longest Consecutive Sequence

## Problem Statement
Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

 

>[!Example]+ Example 1
>**Input**: `nums = [100,4,200,1,3,2]`
>**Output**: `4`
>**Explanation**:
>The longest consecutive elements sequence is `[1, 2, 3, 4]`. Therefore its length is 4. 

>[!Example]+ Example 2
>**Input**: `nums = [0,3,7,2,5,8,4,6,0,1]`
>**Output**: `9
`

>[!warning]+ Constraints
>- `0 <= nums.length <= 10^5`
>
>- `-10^9 <= nums[i] <= 10^9`
## Hints
No hints available.
## Approach

- Avoid using sorting because sorting is $O(n*log(n))$
- 
## Solution

```cpp
# Solution
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> set;
        for(int i = 0; i<nums.size(); i++){
            set.insert(nums[i]);
        }
        int count = 0;
        for(int num : set){
            if(set.contains(num-1)){
                continue;
            }else{
                int currentcount = 1;
                int currentnum = num;
                while(set.contains(currentnum+1)){
                    currentcount++;
                    currentnum++;
                }
                count = max(currentcount,count);
            }
        }
        return count;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(n)$

## Reflections
- When needing to find relationships between elements in an unstructured or unsorted array but don't necessarily need sorting. Put all the elements into a set.