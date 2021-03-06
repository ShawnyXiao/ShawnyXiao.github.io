---
title: 【剑指Offer】面试题52：两个链表的第一个公共节点
date: 2018-04-26 10:36:14
categories:
- 剑指Offer
---

> 题目：输入两个单向链表，找出它们的第一个公共节点。

<!-- more -->

## 思路 1：穷举

最直接的思路是：**对其中一个链表从头到尾遍历每个节点，在遍历一个节点时，对另一个链表从头到尾的遍历，搜索相同的节点，第一个相同的节点就是我们要找的**。这样的做法，如果两个链表的长度分别是 n 和 m，那么时间复杂度是 O(nm)。我们需要思考更快的方法。

## 思路 2：栈

由于是单向链表，因此第一个公共节点之后的节点全是公共的，也就是说两个链表只有前面有一小段不一样，后面都是公共部分。我们需要找到后面公共部分的第一个节点，栈是一个极好的选择。这个方法的思路是：**使用两个栈，分别将两条链表的节点依次压入不同的栈中，由于两条节点后面的节点是相同的，将两个栈同时弹出节点，直到弹出不同的节点，这样便可以找到第一个公共节点了**。这个算法的时间复杂度是 O(n+m)，空间复杂度是 O(n+m)。

## 思路 3：截掉长链表长的那一部分

上一个思路需要两个栈，我们能不能不要额外的空间呢？答案是可以的。这个算法的思路是：**分别遍历两条链表，得到两条链表的长度为 n 和 m（假设 n > m），于是可以知道长链表比短链表多出 n-m 个节点，可以先扫描长链表的 n-m 个节点，这时两条链表需要扫描的部分的长度便相同了，同时扫描两条链表并比较节点是否相同，直到找到第一个相同的节点**。这个算法的时间复杂度是 O(n+m)，空间复杂度是 O(1)。

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
    public ListNode FindFirstCommonNode(ListNode pHead1, ListNode pHead2) {
        // 特殊输入的检查
        if (pHead1 == null || pHead2 == null)
            return null;

        // 计算两个链表的长度
        int l1 = 0, l2 = 0;
        ListNode h = pHead1;
        while (h != null) {
            l1++;
            h = h.next;
        }
        h = pHead2;
        while (h != null) {
            l2++;
            h = h.next;
        }

        // 长链表先遍历长的那一部分
        ListNode n1 = pHead1;
        ListNode n2 = pHead2;
        if (l1 > l2) {
            for (int i = 0; i < l1 - l2; i++)
                n1 = n1.next;
        } else {
            for (int i = 0; i < l2 - l1; i++)
                n2 = n2.next;
        }

        // 两个链表齐头并进
        while (n1 != null) {
            if (n1.val == n2.val)
                return n1;
            n1 = n1.next;
            n2 = n2.next;
        }
        return null;
    }
}
```