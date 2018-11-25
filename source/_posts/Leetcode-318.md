---
title: Leetcode-318
categories:
  - Leetcode
date: 2018-11-26 11:27:08
tags:
---

```java
class Solution {
    public int maxProduct(String[] words) {
        
        int[] charbits = new int[words.length];
        for(int i = 0; i < words.length; i++){
            for(int j = 0; j < words[i].length(); j++){
                charbits[i] |= 1 << (words[i].charAt(j) - 'a');
            }
        }
        
        int max = 0;
        
        for(int i = 0; i < words.length; i++){
            String firstword = words[i];
            
            for(int j = i + 1; j < words.length; j++){
                String secondword = words[j];
                
                if((charbits[i] & charbits[j]) == 0){
                    max = Math.max(firstword.length() * secondword.length(), max);
                }
            }
            
        }
        
        return max;
    }
}
```
