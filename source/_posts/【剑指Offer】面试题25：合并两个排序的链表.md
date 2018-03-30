---
title: 【剑指Offer】面试题25：合并两个排序的链表
date: 2018-03-30 09:18:40
categories:
- 剑指Offer
---

> 题目：输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。

<!-- more -->

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
    public ListNode Merge(ListNode list1, ListNode list2) {
        // 特殊输入的检查
        if (list1 == null)
            return list2;
        if (list2 == null)
            return list1;

        // 定义节点变量
        ListNode head = null;
        ListNode p = null;
        ListNode q = null;
        ListNode n = null;
        if (list1.val <= list2.val) {
            head = list1;
            p = list1.next;
            q = list2;
            n = list1;
        } else {
            head = list2;
            p = list1;
            q = list2.next;
            n = list2;
        }

        // 遍历两个链表
        while (p != null && q != null) {
            if (p.val <= q.val) {
                n.next = p;
                n = p;
                p = p.next;
            } else {
                n.next = q;
                n = q;
                q = q.next;
            }
        }
        if (p == null) {
            n.next = q;
        } else if (q == null) {
            n.next = p;
        }

        return head;
    }
}
```