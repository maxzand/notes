---
created: 2024-12-20
modified: 
completed: true
leetcode-index: 238
link: https://leetcode.com/problems/product-of-array-except-self
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/prefix-sum
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Product of Array Except Self

## Problem Statement
Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

 

>[!Example]+ Example 1
>**Input**: `nums = [1,2,3,4]`
>**Output**: `[24,12,8,6]
`

>[!Example]+ Example 2
>**Input**: `nums = [-1,1,0,-3,3]`
>**Output**: `[0,0,9,0,0]
`

>[!warning]+ Constraints
>- `2 <= nums.length <= 10^5`
>
>- `-30 <= nums[i] <= 30`
>
>- The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.
>
>
>
>
>
>
>
>
>Follow up: Can you solve the problem in `O(1)` extra space complexity? (The output array does not count as extra space for space complexity analysis.)
## Hints
>[!Hint]- Hint 1
>Think how you can efficiently utilize prefix and suffix products to calculate the product of all elements except self for each index. Can you pre-compute the prefix and suffix products in linear time to avoid redundant calculations?

>[!Hint]- Hint 2
>Can you minimize additional space usage by reusing memory or modifying the input array to store intermediate results?
## Approach

- Avoid using nested loops and the problem is simple. For any given index into the array `i`, it's value should be equal to the product of the previous index in the prefix array and the following index in the suffix array (product arrays).
## Solution

```cpp
# Solution
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> prefix = nums;
        vector<int> suffix = nums;
        for(int i = 1; i<nums.size(); i++){
            prefix[i] = prefix[i-1]*prefix[i];
        }

        for(int i = nums.size()-2;i>=0;i--){
            suffix[i] = suffix[i]*suffix[i+1];

        }

        vector<int> answer(nums.size());
        answer[0] = suffix[1];
        answer[nums.size()-1] = prefix[nums.size()-2];

        for(int i = 1; i<nums.size()-1;i++){
            answer[i] = prefix[i-1] * suffix[i+1];
        }
        return answer;
    }
};
```
## Follow up Solution

Follow up: Can you solve the problem in `O(1)` extra space complexity? (The output array does not count as extra space for space complexity analysis.)

### Notes 
* Currently my solution has $O(n)$ extra space complexity because I use two $O(n)$ vectors in order to store my product arrays. I could avoid this by using a two pointer approach.


```cpp
# Solution
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> answer(nums.size(),1);
        int left = 1;
        for(int i = 0; i<nums.size(); i++){
            answer[i]*=left;
            left*=nums[i];
        }
        int right = 1;
        for(int i = nums.size()-1; i>=0; i--){
            answer[i]*=right;
            right*=nums[i];
        }
        return answer;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(n)$

## Reflections
-  Use two pointer approaches when needing to iterate over elements and not needing the entire array
	- The intuition is that for any index `i` we only need the prefix or suffix product of that element both before and after.