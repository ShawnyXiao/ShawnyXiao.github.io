---
title: 【剑指Offer】面试题10-1：求斐波那契数列的第n项
date: 2018-03-22 18:36:17
categories:
- 剑指Offer
---

> 题目：大家都知道斐波那契数列，现在要求输入一个整数 n，请你输出斐波那契数列的第 n 项。

<!-- more -->

## 实现

```java
public class Solution {
    public int Fibonacci(int n) {
        // 特殊输入检查
        if (n <= 0)
            return 0;
        if (n == 1 || n == 2)
            return 1;

        // 动态规划
        int a = 1, b = 1;
        int tmp;
        for (int i = 3; i <= n; i++) {
            tmp = a + b;
            a = b;
            b = tmp;
        }
        return b;
    }
}
```