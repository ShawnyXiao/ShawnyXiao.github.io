---
title: 【剑指Offer】面试题6：从尾到头打印链表
date: 2018-03-21 15:31:36
categories:
- 剑指Offer
---

> 题目：输入一个链表，从尾到头打印链表每个节点的值。

<!-- more -->

## 实现

```java
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/

import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        ArrayList<Integer> result = new ArrayList<>();

        // 特殊输入检查
        if (listNode == null)
            return result;

        // 递归访问链表节点
        recursiveVisitListNode(listNode, result);
        return result;
    }

    private void recursiveVisitListNode(ListNode n, ArrayList<Integer> result) {
        if (n == null)
            return;

        recursiveVisitListNode(n.next, result);
        result.add(n.val);
    }
}
```