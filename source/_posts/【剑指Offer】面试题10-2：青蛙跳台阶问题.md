---
title: 【剑指Offer】面试题10-2：青蛙跳台阶问题
date: 2018-03-22 18:36:44
categories:
- 剑指Offer
---

> 题目：一只青蛙一次可以跳上 1 级台阶，也可以跳上 2 级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

<!-- more -->

## 实现

```java
public class Solution {
    public int JumpFloor(int target) {
        // 特殊输入检查
        if (target <= 0)
            return 0;
        if (target == 1)
            return 1;
        if (target == 2)
            return 2;

        // 动态规划
        int a = 1, b = 2;
        int tmp;
        for (int i = 3; i <= target; i++) {
            tmp = a + b;
            a = b;
            b = tmp;
        }
        return b;
    }
}
```