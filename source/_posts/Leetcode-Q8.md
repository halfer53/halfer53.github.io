---
title: Leetcode Q8
categories:
  - Leetcode
date: 2018-04-23 21:46:33
tags:
---

```c
static inline bool is_char(char c){
    return '0' <= c && c <= '9';
}

int myAtoi(char* str) {
    long ret = 0;
    int sign = 1;
    if(!str)
        return ret;
    while(*str == ' ')
        str++;
    if(*str && *str == '-'){
        sign = -1;
        str++;
    }else if(*str && *str == '+')
        str++;
    
    while(*str && is_char(*str)){
        ret = ret * 10 + (*str - '0');
        if(ret * sign < (1 << 31))
            return 1 << 31;
        if(ret * sign > ~(1 << 31))
            return ~(1 << 31);

        str++;
    }
    return ret * sign;
}
```