---
title: Leetcode Q32
categories:
  - Leetcode
date: 2018-04-09 20:04:25
tags:
---

First attempt was a naive solution with Time Complexity O(n^2)

```java
class Solution {
    public int longestValidParentheses(String s) {
        boolean[][] dp = new boolean[s.length()][s.length()];
        int[] ends = new int[s.length()+1];
        int longest = 0;
        for(int i=s.length() - 1; i >= 0; i--){
            for(int j = i; j < s.length(); j++){
                if(s.charAt(i) == '(' && s.charAt(j) == ')'
                  && (j - i == 1 || dp[i + 1][j - 1])){
                        dp[i][j] = true;
                        ends[i] = j;
                        int nexthop = j + 1;
                        while(ends[nexthop] != 0){
                            ends[i] = ends[nexthop];
                            int end = ends[i];
                            nexthop = end + 1;
                            dp[i][end] = true;
                        }
                        longest = Math.max(longest, ends[i] - i + 1);
                        // System.out.println(i + " " + j + " " + longest);
                  }
            }
        }
        return longest;
    }
}
```