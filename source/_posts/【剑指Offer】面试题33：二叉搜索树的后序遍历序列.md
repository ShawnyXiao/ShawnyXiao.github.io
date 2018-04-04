---
title: 【剑指Offer】面试题33：二叉搜索树的后序遍历序列
date: 2018-04-04 10:08:45
categories:
- 剑指Offer
---

> 题目：输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则输出 Yes，否则输出 No。假设输入的数组的任意两个数字都互不相同。

<!-- more -->

## 实现

```java
public class Solution {
    public boolean VerifySquenceOfBST(int[] sequence) {
        // 特殊输入的检查
        if (sequence == null || sequence.length == 0)
            return false;

        return verify(sequence, 0, sequence.length);
    }

    private boolean verify(int[] s, int lo, int hi) {
        // 退出边界
        if (hi - lo <= 1)
            return true;

        // 查找划分下标
        int split = lo;
        for (; split < hi - 1; split++) {
            if (s[split] > s[hi - 1]) {
                break;
            }
        }

        // 验证右边部分大于等于最后的节点
        for (int i = split; i < hi - 1; i++) {
            if (s[i] < s[hi - 1]) {
                return false;
            }
        }

        return verify(s, lo, split) && verify(s, split, hi - 1);
    }
}
```