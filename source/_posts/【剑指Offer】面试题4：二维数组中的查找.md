---
title: 【剑指Offer】面试题4：二维数组中的查找
date: 2018-03-21 15:30:24
categories:
- 剑指Offer
---

> 题目：在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

<!-- more -->

## 实现

```java
public class Solution {
    public boolean Find(int target, int [][] array) {
        // 特殊输入的检查
        if (array == null || array.length < 1 || array[0].length < 1)
            return false;
        int rows = array.length;
        int columns = array[0].length;
        if (target < array[0][0] || target > array[rows - 1][columns - 1])
            return false;

        // 从右上角开始
        int row = 0;
        int column = columns - 1;

        // 向左向下查找
        while (row >= 0 && row < rows && column >= 0 && column < columns) {
            if (array[row][column] == target)
                return true;
            else if (array[row][column] < target)
                row++;
            else
                column--;
        }
        return false;
    }
}
```