---
title: Leetcode Q1
date: 2018-01-23 00:40:51
tags:
categories:
- Leetcode
---

```java

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int[] res = new int[2];
        
        for(int i=0; i < nums.length; i++){
            int remaining = target - nums[i];
            if(map.get(remaining) == null){
                map.put(nums[i], i);
            }else{
                res[0] = map.get(remaining);
                res[1] = i;
                return res;
            }
        }
        return res;
    }
}
```
