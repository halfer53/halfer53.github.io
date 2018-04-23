---
title: Leetcode Q10
categories:
  - Leetcode
date: 2018-04-24 00:41:56
tags:
---


I tried to use non-deterministic state machine first, but the code seems too slow that the Time Limit was reached :(

```java
class Solution {
    Character repchar = null;
    Character stopchar = null;
    int maxlen = 0;
    int i = 0;
    String p = null;
    String s = null;
    int j = 0;
    
    void compile(){
        if(j >= p.length()){
            repchar = null;
            return;
        }
        repchar = p.charAt(j++);
        if(j < p.length()){
            if(p.charAt(j) == '*'){
                stopchar = j < s.length() -1 ? p.charAt(++j) : null;
                maxlen = 0;
            }else{
                stopchar = p.charAt(j);
                maxlen = 1;
            }
        }else{
            stopchar = null;
            maxlen = 1;
        }
        
    }
    
    public boolean isMatch(String s, String p) {
        this.p = p;
        this.s = s;
        compile();
        while( i < s.length()){
            char c = s.charAt(i);
            if(repchar == null)
                return false;
            
            if(maxlen == 1 || (stopchar != null && c != stopchar)){
                if(repchar == '.' || repchar == c){
                    i++;
                }else{
                    return false;
                }
            }
            if((stopchar != null &&c == stopchar) || maxlen == 1)
                compile();
            
        }
        if(repchar != null)
            return false;
        return true;
    }
}
```
