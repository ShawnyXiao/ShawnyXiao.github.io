---
title: 【剑指Offer】面试题21：调整数组顺序使奇数位于偶数前面
date: 2018-03-30 09:17:37
categories:
- 剑指Offer
---

> 题目：输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

## 实现

```java
public class Solution {
    public void reOrderArray(int [] array) {
        // 特殊输入的检查
        if (array == null || array.length <= 1)
            return;

        // 参考插入排序的思想
        for (int i = 0; i < array.length; i++) {
            // 寻找偶数
            if (isEven(array[i])) {
                // 寻找奇数
                for (int j = i + 1; j < array.length; j++) {
                    if (!isEven(array[j])) {
                        // 将奇数插入到偶数前面
                        int tmp = array[j];
                        for (int k = j; k > i; k--)
                            array[k] = array[k - 1];
                        array[i] = tmp;
                        break;
                    }
                }
            }
        }
    }
    private boolean isEven(int num) {
        return num % 2 == 0;
    }
}
```