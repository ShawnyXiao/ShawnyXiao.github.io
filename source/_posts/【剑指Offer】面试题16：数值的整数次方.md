---
title: 【剑指Offer】面试题16：数值的整数次方
date: 2018-03-29 12:37:29
categories:
- 剑指Offer
---

> 题目：给定一个 double 类型的浮点数 base 和 int 类型的整数 exponent。求 base 的 exponent 次方。

<!-- more -->

## 实现

```java
public class Solution {
    public double Power(double base, int exponent) {
        // 特殊输入的检查
        if (base == 0 && exponent < 0)
            throw new RuntimeException("分母不能为0");
        if (base == 0)
            return 0;
        if (exponent == 0)
            return 1;

        // 判断 exponent 的符号
        int absExp = 0;
        if (exponent > 0)
            absExp = exponent;
        else if (exponent < 0)
            absExp = -exponent;

        // 按指数二进制表示，迭代
        double tmp = base;
        double res = 1;
        while (absExp != 0) {
            if ((absExp & 1) == 1)
                res *= tmp;
            tmp *= tmp;
            absExp >>= 1;
        }

        return exponent > 0 ? res : 1 / res;
  }
}
```