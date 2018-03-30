---
title: 【剑指Offer】面试题22：链表中倒数第k个节点
date: 2018-03-30 09:18:02
categories:
- 剑指Offer
---

> 题目：输入一个链表，输出该链表中倒数第 k 个结点。

## 实现

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}
*/

import java.util.Stack;

public class Solution {
    public ListNode FindKthToTail(ListNode head, int k) {
        // 特殊输入的检查
        if (head == null || k <= 0)
            return null;

        // 双指针
        ListNode pre = head;
        ListNode pos = head;
        for (int i = 0; i < k; i++) {
            if (pre == null)
                return null;
            pre = pre.next;
        }
        while (pre != null) {
            pre = pre.next;
            pos = pos.next;
        }
        return pos;
    }
}
```