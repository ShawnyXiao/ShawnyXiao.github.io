---
title: 【剑指Offer】面试题24：反转链表
date: 2018-03-30 09:18:22
categories:
- 剑指Offer
---

> 题目：输入一个链表，反转链表后，输出链表的所有元素。

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

public class Solution {
    public ListNode ReverseList(ListNode head) {
        // 特殊输入的检查
        if (head == null || head.next == null)
            return head;

        // 定义节点变量
        ListNode pre = null;
        ListNode n = head;
        ListNode pos = null;

        // 遍历所有节点
        while (n != null) {
            pos = n.next;
            n.next = pre;
            pre = n;
            n = pos;
        }

        return pre;
    }
}
```