---
title: 【剑指Offer】面试题29：顺时针打印矩阵
date: 2018-04-03 21:36:37
categories:
- 剑指Offer
---

> 题目：输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。
例如，如果输入如下矩阵：
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
则依次打印出数字
1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10

<!-- more -->

## 实现

```java
/**
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printMatrix(int [][] matrix) {
        ArrayList<Integer> res = new ArrayList<Integer>();

        // 特殊输入的检查
        if (matrix == null)
            return res;

        int row = matrix.length;
        int col = matrix[0].length;

        // 循环次数=圈数（已经开始进入圈中了也算一圈）
        for (int i = 0; i <= ((row - 1) / 2) && i <= ((col - 1) / 2); i++) {
            // 从左至右
            for (int j = i; j < col - i; j++)
                res.add(matrix[i][j]);
            // 从上至下
            for (int j = i + 1; j < row - i; j++)
                res.add(matrix[j][col - i - 1]);
            // 从右至左
            if (row - i - 1 > i)
                for (int j = col - i - 2; j >= i; j--)
                    res.add(matrix[row - i - 1][j]);
            // 从下至上
            if (col - i - 1 > i)
                for (int j = row - i - 2; j >= i + 1; j--)
                    res.add(matrix[j][i]);
        }

        return res;
    }
}
```