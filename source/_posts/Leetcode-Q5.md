---
title: Leetcode Q5
categories:
  - Leetcode
date: 2018-04-08 23:16:58
tags:
---

```java
class Solution {
    public String longestPalindrome(String s) {
        if(s.length() <= 2)
            return s;
        int lo = 0, len = 0;
        boolean[][] dp = new boolean[s.length()][s.length()];
        for(int i= s.length() - 2; i >= 0; i--){
            for(int j=i+1; j < s.length(); j++){
                if(s.charAt(i) == s.charAt(j) &&
                  (j - i < 3 || dp[i + 1][j - 1])){
                    dp[i][j] = true;
                    int tlen = j - i;
                    if(tlen > len){
                        len = tlen;
                        lo = i;
                    }
                }
            }
        }
        return s.substring(lo,lo + len + 1);
    }
}
```
