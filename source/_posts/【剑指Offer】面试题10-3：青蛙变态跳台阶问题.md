---
title: 【剑指Offer】面试题10-3：青蛙变态跳台阶问题
date: 2018-03-22 18:37:18
categories:
- 剑指Offer
---

> 题目：一只青蛙一次可以跳上 1 级台阶，也可以跳上 2 级……它也可以跳上 n 级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

## 实现

```java
public class Solution {
    public int JumpFloorII(int target) {
        // 特殊输入检查
        if (target <= 0)
            return 0;

        // f(n) = f(n-1) + f(n-2) + ... + f(1) + 1 = 2^(n-1)
        return 1 << (target - 1);
    }
}
```