---
title: 【剑指Offer】面试题10-3：矩形覆盖
date: 2018-03-29 12:32:25
categories:
- 剑指Offer
---

> 题目：我们可以用 2\*1 的小矩形横着或者竖着去覆盖更大的矩形。请问用 n 个 2\*1 的小矩形无重叠地覆盖一个 2\*n 的大矩形，总共有多少种方法？

## 实现

```java
public class Solution {
    public int RectCover(int target) {
        // 特殊输入检查
        if (target == 0)
            return 0;
        if (target == 1)
            return 1;
        if (target == 2)
            return 2;

        // 动态规划 f(n)=f(n-1)+f(n-2)
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