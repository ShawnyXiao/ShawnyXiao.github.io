---
title: 【剑指Offer】面试题35：复杂链表的复制
date: 2018-04-07 19:01:23
categories:
- 剑指Offer
---

> 题目：输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的 head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）

<!-- more -->

## 实现

```java
/*
public class RandomListNode {
    int label;
    RandomListNode next = null;
    RandomListNode random = null;

    RandomListNode(int label) {
        this.label = label;
    }
}
*/
public class Solution {
    public RandomListNode Clone(RandomListNode pHead) {
        // 特殊输入的检查
        if (pHead == null)
            return null;

        // 复制节点，放置在原节点的后面。例如：(a -> b -> c) --> (a -> a' -> b -> b' -> c -> c')
        RandomListNode n = pHead;
        while (n != null) {
            RandomListNode nCopy = new RandomListNode(n.label);
            nCopy.next = n.next;
            n.next = nCopy;
            n = nCopy.next;;
        }

        // 复制 random 指针
        n = pHead;
        while (n != null) {
            if (n.random != null) {
                n.next.random = n.random.next;
            }
            n = n.next.next;
        }

        // 拆分链表
        RandomListNode newHead = pHead.next;
        RandomListNode newN = newHead;
        n = pHead;
        while (n != null) {
            n.next = newN.next;
            n = n.next;
            if (n != null) {
                newN.next = n.next;
                newN = newN.next;
            } else {
                newN.next = null;
            }
        }

        return newHead;
    }
}
```