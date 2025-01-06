---
created: 2025-01-06
modified: 
completed: true
leetcode-index: 1769
link: https://leetcode.com/problems/minimum-number-of-operations-to-move-all-balls-to-each-box
difficulty: Medium
tags:
  - leetcode/array
  - leetcode/string
  - leetcode/prefix-sum
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Minimum Number of Operations to Move All Balls to Each Box

## Problem Statement
You have `n` boxes. You are given a binary string `boxes` of length `n`, where `boxes[i]` is `'0'` if the `i^th` box is empty, and `'1'` if it contains one ball.

In one operation, you can move one ball from a box to an adjacent box. Box `i` is adjacent to box `j` if `abs(i - j) == 1`. Note that after doing so, there may be more than one ball in some boxes.

Return an array `answer` of size `n`, where `answer[i]` is the minimum number of operations needed to move all the balls to the `i^th` box.

Each `answer[i]` is calculated considering the initial state of the boxes.

 

>[!Example]+ Example 1
>**Input**: `boxes = "110"`
>**Output**: `[1,1,3]`
>**Explanation**:
>The answer for each box is as follows: 
> 1) First box: you will have to move one ball from the second box to the first box in one operation. 
> 2) Second box: you will have to move one ball from the first box to the second box in one operation. 
> 3) Third box: you will have to move one ball from the first box to the third box in two operations, and move one ball from the second box to the third box in one operation. 

>[!Example]+ Example 2
>**Input**: `boxes = "001011"`
>**Output**: `[11,8,5,4,3,4]`

>[!warning]+ Constraints
>- `n == boxes.length`
>
>- `1 <= n <= 2000`
>
>- `boxes[i]` is either `'0'` or `'1'`.
## Hints
>[!Hint]- Hint 1
>If you want to move a ball from box i to box j, you'll need abs(i-j) moves.

>[!Hint]- Hint 2
>To move all balls to some box, you can move them one by one.

>[!Hint]- Hint 3
>For each box i, iterate on each ball in a box j, and add abs(i-j) to answers[i].
## Approach

- 
## Solution

```cpp
# Solution
class Solution {
public:
    vector<int> minOperations(string boxes) {
        int count = 0;
        int right = boxes.size() -1;
        vector<int> prefix(boxes.length());

        for(int i = 1; i<boxes.size();i++){
            if(boxes[i-1] == '1'){
                count+=1;
            }
            prefix[i] += count + prefix[i-1];
        }
        count = 0;
        vector<int> suffix(boxes.length());
        for(int i = boxes.size() - 2;i>=0; i--){
            if(boxes[i+1] == '1'){
                count+=1;
            }
            suffix[i] += count+suffix[i+1];
        }
        for(int i = 0;i<boxes.size(); i++){
            prefix[i] += suffix[i];
        }
        return prefix;
        
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$
- Space complexity: $O(n)$

## Reflections
-  This problem REALLY reminded me of [[238-Product of Array Except Self]]
- Pretty easy, pass left and right using $O(n)$ time and space complexity. Honestly, I could probably do better using $O(1)$ extra space complexity if i calculated my prefixes and suffixes more intuitively.