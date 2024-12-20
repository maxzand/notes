---
created: 2024-12-20
modified: 
completed: false
leetcode-index: 49 
link: https://leetcode.com/problems/group-anagrams
difficulty: Medium 
tags:
   - leetcode/array
   - leetcode/hash-table
   - leetcode/string
   - leetcode/sorting 
   - programming/practice
   - leetcode/problem
   - your/tags
---
# Group Anagrams

## Problem Statement
Given an array of strings `strs`, group the <span data-keyword="anagram">anagrams</span> together. You can return the answer in any order.

 

>[!Example]+ Example 1
>**Input**: `strs = ["eat","tea","tan","ate","nat","bat"]`
>**Output**: `[["bat"],["nat","tan"],["ate","eat","tea"]]`
>**Explanation**:
>- There is no string in strs that can be rearranged to form `"bat"`. 	 - The strings `"nat"` and `"tan"` are anagrams as they can be rearranged to form each other. 	 - The strings `"ate"`, `"eat"`, and `"tea"` are anagrams as they can be rearranged to form each other.   

>[!Example]+ Example 2
>**Input**: `strs = [""]`
>**Output**: `[[""]]`

>[!Example]+ Example 3
>**Input**: `strs = ["a"]`
>**Output**: `[["a"]]`

>[!warning]+ Constraints
>- `1 <= strs.length <= 10^4`
>
>- `0 <= strs[i].length <= 100`
>
>- `strs[i]` consists of lowercase English letters.
## Hints
No hints available.
## Approach

- Initially I wanted to just use a hash table in order to map a raw array of 26 with each character count (which is basically a unique identifier for an anagram) to a vector of strings containing all of the anagrams. This approach would have worked if not for the fact that you can't hash raw arrays as keys. So instead of taking a worse approach in time complexity such as sorting (would introduce $n*log(n)$ time complexity), I decided to try converting my raw array into a string which can be hashed. This is just another $O(n)$ operation.
## Solution

```cpp
# Solution
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> map;

        for(string s: strs){
            int count[26] = {0};

            for(char c: s){
                count[c-'a']++;
            }
            string hash;
            for(int num : count){
                hash+=to_string(num) + ' ';
            }
            map[hash].push_back(s);
        }
        vector<vector<string>> result;
        for(auto x : map){
            result.push_back(move(x.second));
        }
        return result;
    }
};
```

## Complexity Analysis

- Time complexity: $O(n*m)$
- Space complexity: $O(n*m)$
- Where $n$ is the size of the vector `strs` and $m$ is the size of the string `s`

## Reflections
- Raw arrays cannot be hashed
- Important to use std functions like `move()` to avoid unnecessary copying 