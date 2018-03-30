---
title: 【剑指Offer】面试题15：二进制中1的个数
date: 2018-03-29 12:36:02
categories:
- 剑指Offer
---

> 题目：输入一个整数，输出该数二进制表示中 1 的个数。其中负数用补码表示。

<!-- more -->

## 实现

```java
public class Solution {
    public int NumberOf1(int n) {
        int count = 0;
        while (n != 0) {
            n = n & (n - 1);
            count++;
        }
        return count;
    }
}
```