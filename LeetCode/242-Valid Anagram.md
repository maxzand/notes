---
created: 2024-12-19
modified: 
completed: true
leetcode-index: 242
link: https://leetcode.com/problems/valid-anagram
difficulty: Easy
tags:
  - leetcode/hash-table
  - leetcode/string
  - leetcode/sorting
  - programming/practice
  - leetcode/problem
  - your/tags
---
# Valid Anagram

## Problem Statement
Given two strings `s` and `t`, return `true` if `t` is an <span data-keyword="anagram">anagram</span> of `s`, and `false` otherwise.

 

>[!Example]+ Example 1
>**Input**: `s = "anagram", t = "nagaram"`
>**Output**: `true`

>[!Example]+ Example 2
>**Input**: `s = "rat", t = "car"`
>**Output**: `false`

>[!warning]+ Constraints
>- `1 <= s.length, t.length <= 5 * 10^4`
>
>- `s` and `t` consist of lowercase English letters.
>
>
>
>
>
>
>
>
>Follow up: What if the inputs contain Unicode characters? How would you adapt your solution to such a case?
## Hints
No hints available.
## Approach

- Initially I was going to use a hash table but after consideration because we only need to count 26 possible characters (lowercase alphabet), then that means we can use a raw array to count it. 
## Solution

```cpp
# Solution
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size()){
            return false;
        }
        int frequency[26] = {0};
        for(int i = 0;i<s.size();i++){
            frequency[s[i]-'a']++;
            frequency[t[i]-'a']--;
        }
        for(int j = 0;j<26;j++){
            if(frequency[j]!=0){
                return false;
            }
        }
        return true;
    }
};
```

## Complexity Analysis

- Time complexity: O(n) , O(n) + O(n) + O(1)
- Space complexity: O(1)

## Reflections
-  If all UNICODE characters were used, then I would use a hash table. Otherwise I am happy with the solution. I think for readability, I can sacrifice 4 bytes of memory to define a variable for the amount of characters (26), so that when i iterate the array at the end there isn't a random 26 that might confuse someone reading my code.