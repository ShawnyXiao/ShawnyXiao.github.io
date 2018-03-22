---
title: 【剑指Offer】面试题11：旋转数组的最小数字
date: 2018-03-22 18:37:21
categories:
- 剑指Offer
---

> 题目：把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。例如数组 {3, 4, 5, 1, 2} 为 {1, 2, 3, 4, 5} 的一个旋转，该数组的最小值为 1。

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