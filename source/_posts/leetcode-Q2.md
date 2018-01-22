---
title: leetcode Q2
categories:
  - Leetcode
date: 2018-01-23 00:58:28
tags:
---

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;
        int carry = 0;
        
        while( l1 != null || l2 != null){
            int l1i = l1 != null ? l1.val : 0;
            int l2i = l2 != null ? l2.val : 0;
            int combine = (l1i + l2i) + carry;
            int newval = combine % 10;
            carry = combine / 10;
            
            ListNode tmp = new ListNode(newval);
            
            curr.next = tmp;
            curr = tmp;
            if(l1 != null)
                l1 = l1.next;
            if(l2 != null)
                l2 = l2.next;
        }
        
        if(carry != 0){
            curr.next = new ListNode(carry);
        }
            
        return dummy.next;
    }
}
```