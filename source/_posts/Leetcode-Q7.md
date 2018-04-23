---
title: Leetcode Q7
categories:
  - Leetcode
date: 2018-04-23 21:11:25
tags:
---

```java
public class Solution {
    public int reverse(int x) {
        long i = 0;
        int l = String.valueOf(Math.abs(x)).length();
        int count = 1;
        for(;l>1;l--){
            count *= 10;  
        }
        
        while(x!=0){
            i += ((long)x%10) * (long)count;
            count /= 10;
            x /= 10;
        }
        if(i>Integer.MAX_VALUE || i<Integer.MIN_VALUE){
            return 0;
        }
        if(x<0) i*= -1;
        return (int)i;
    }
}
```