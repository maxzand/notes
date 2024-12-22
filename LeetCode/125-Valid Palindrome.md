---
created: 2024-12-21
modified: 
completed: true
leetcode-index: 125
link: https://leetcode.com/problems/valid-palindrome
difficulty: Easy
tags:
  - leetcode/two-pointers
  - leetcode/string
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Valid Palindrome

## Problem Statement
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true`* if it is a palindrome, or *`false`* otherwise*.

 

>[!Example]+ Example 1
>**Input**: `s = "A man, a plan, a canal: Panama"`
>**Output**: `true`
>**Explanation**:
>"amanaplanacanalpanama" is a palindrome. 

>[!Example]+ Example 2
>**Input**: `s = "race a car"`
>**Output**: `false`
>**Explanation**:
>"raceacar" is not a palindrome. 

>[!Example]+ Example 3
>**Input**: `s = " "`
>**Output**: `true`
>**Explanation**:
>s is an empty string "" after removing non-alphanumeric characters. Since an empty string reads the same forward and backward, it is a palindrome. 

>[!warning]+ Constraints
>- `1 <= s.length <= 2 * 10^5`
>
>- `s` consists only of printable ASCII characters.
## Hints
No hints available.
## Approach

- Use a two pointer approach. Start on the left and right sides and slowly make comparisons as you move each towards the middle.
## Solution

```cpp
# Solution
class Solution {
public:
    bool isPalindrome(string s) {
        int left = 0; 
        int right = s.size()-1;
        while(right > left){
            if(!isalnum(s[right])){ right--; continue;}
            if(!isalnum(s[left])){ left++; continue;}
            if(tolower(s[left]) != tolower(s[right])){
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n)$ Loop thru array at 2x speed so $O(n/2) --> O(n)$
- Space complexity: $O(1)$ used two pointers

## Reflections
- **Important Functions**: 
```cpp
std::tolower() // Converts any char to lowercase
std::isalnum() // Checks if char is alpha numeric
```