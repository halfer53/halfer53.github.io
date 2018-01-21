---
title: Leetcode Q9
date: 2018-01-21 03:58:33
categories:
- Leetcode
tags:
---

https://leetcode.com/problems/palindrome-number/description/

```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x == 0)
            return true;
        if(x < 0)
            return false;
        long rev = 0;
        int val = x;
        int count = 0;
        while( val!= 0){
            rev = rev * 10 + val % 10;
            val /= 10;
            count++;
            if( rev > Integer.MAX_VALUE || rev < Integer.MIN_VALUE)
                return false;
        }
        int irev = (int)rev;
        while(x != irev){
            int shift = count * 10;
            int left = irev / shift;
            int right = x % 10;
            if( left != right)
                return false;
            x/= 10;
            irev /= shift;
            count--;
        }
        return true;
    }
}
```
