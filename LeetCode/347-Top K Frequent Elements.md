---
created: 2024-12-20
modified: 
completed: false
leetcode-index: 347 
link: https://leetcode.com/problems/top-k-frequent-elements
difficulty: Medium 
tags:
   - leetcode/array
   - leetcode/hash-table
   - leetcode/divide-and-conquer
   - leetcode/sorting
   - leetcode/heap-priority-queue
   - leetcode/bucket-sort
   - leetcode/counting
   - leetcode/quickselect 
   - programming/practice
   - leetcode/problem
   - your/tags
---
# Top K Frequent Elements

## Problem Statement
Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in any order.

 

>[!Example]+ Example 1
>**Input**: `nums = [1,1,1,2,2,3], k = 2`
>**Output**: `[1,2]
`

>[!Example]+ Example 2
>**Input**: `nums = [1], k = 1`
>**Output**: `[1]
`

>[!warning]+ Constraints
>- `1 <= nums.length <= 10^5`
>
>- `-10^4 <= nums[i] <= 10^4`
>
>- `k` is in the range `[1, the number of unique elements in the array]`.
>
>- It is guaranteed that the answer is unique.
>
>
>
>
>
>
>
>
>Follow up: Your algorithm's time complexity must be better than `O(n log n)`, where n is the array's size.
## Hints
No hints available.
## Approach

- The first thing that needs to be done is count the frequency of each number and this can be done using an `unordered_map`. Using a for loop this will be an operation with time complexity of $O(n)$.
- The second thing is we need to iterate over our map in order to find the numbers with the highest frequency. **The key intuition here is that we know there are only a fixed amount of frequencies, so we can declare a vector of that fixed size and sort using an $O(n)$ loop grouping into buckets as opposed to a normal $O(n*log(n))$ sorting method** 
## Solution

```cpp
# Solution
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int,int> map;
        vector<int> result;
        int count;
        for(int num : nums){
            map[num]++;
        }
        vector<vector<int>> ordered(nums.size()+1);
        for(const auto pair : map){
            ordered[pair.second].push_back(pair.first);
        }
        for(int i = size(ordered) - 1; i>=0; i--){
            for(int num : ordered[i]){
                result.push_back(num);
                if(result.size() == k){
                    return result;
                }
            }
        }
        return {};
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(n)$

## Reflections
- Be mindful of of the constraints of everything (ie the constraints to the amount of possible frequencies)
- Group by buckets to avoid $O(n*log(n))$ sorting algorithms if possible