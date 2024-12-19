---
created: 2024-12-17
modified: 
completed: true
leetcode-index: 1
link: https://leetcode.com/problems/two-sum
difficulty: Easy
tags:
  - leetcode/array
  - leetcode/hash-table
  - programming/practice
  - leetcode/problem
---
# Two Sum

## Problem Statement
Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have *exactly* one solution, and you may not use the *same* element twice.

You can return the answer in any order.

 

>[!Example]+ Example 1
>**Input**: `nums = [2,7,11,15], target = 9`
>**Output**: `[0,1]`
>**Explanation**: `Because nums[0] + nums[1] == 9, we return [0, 1].
>`

>[!Example]+ Example 2
>**Input**: `nums = [3,2,4], target = 6`
>**Output**: `[1,2]
`

>[!Example]+ Example 3
>**Input**: `nums = [3,3], target = 6`
>**Output**: `[0,1]
`

>[!warning]+ Constraints
>- `2 <= nums.length <= 10^4`
>
>- `-10^9 <= nums[i] <= 10^9`
>
>- `-10^9 <= target <= 10^9`
>
>- Only one valid answer exists.

>[!Todo]- Follow Up
>Can you come up with an algorithm that is less than `O(n^2)` time complexity?
## Hints
>[!Hint]- Hint 1
>A really brute force way would be to search for all possible pairs of numbers but that would be too slow. Again, it's best to try out brute force solutions for just for completeness. It is from these brute force solutions that you can come up with optimizations.

>[!Hint]- Hint 2
>So, if we fix one of the numbers, say x, we have to scan the entire array to find the next number y which is value - x where value is the input parameter. Can we change our array somehow so that this search becomes faster?

>[!Hint]- Hint 3
>The second train of thought is, without changing the array, can we use additional space somehow? Like maybe a hash map to speed up the search?
## Approach

- 
## Solution

```cpp
# Solution
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::unordered_map<int,int> map; //Hashtable
        for(int i=0;i<nums.size(); i++) {
            int desired = target - nums[i]; //What value would we need for the current value to work?
            
            if(map.find(desired) != map.end()){
	            // Have we seen this value we need?
                return {map[desired],i};
            }
	        // If not save the current index with it's value as key for future lookup
            map[nums[i]] = i;
        }

        return {}; // No solution found.
    }
};
```

## Complexity Analysis

- Time complexity: O(N)
- Space complexity: O(N)

## Reflections
This is one of the most intuitive problems to solve with a hashmap. Initially an O(N^2) approach can be taken using loops but easily can be changed to be O(N) with a hash table