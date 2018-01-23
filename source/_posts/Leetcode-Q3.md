---
title: Leetcode Q3
categories:
  - Leetcode
date: 2018-01-23 14:31:54
tags:
---

There are basically two options here

1. O(n^3), loop through every possibility to find the longest substring
2. Use a hashmap to indicate the position of each character. If a replicate character is encountered, and is contained in the current substring, current substring will be updated such that it will start from one character next to the previous one, curr count will be updated accordingly.

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int longest = 0;
        int curr = 0;
        int prev = 0;
        for(int i=0; i < s.length(); i++){
            char c = s.charAt(i);
            if(map.get(c) != null && map.get(c) >= prev){
                prev = map.get(c);
                map.put(c, i);
                longest = Math.max(curr, longest);
                curr = i - prev;
                prev++;
            }else{
                map.put(c, i);
                curr++;
            }
        }
        longest = Math.max(curr, longest);
        return longest;
    }
}
```
