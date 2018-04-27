---
title: 【剑指Offer】面试题55-2：平衡二叉树
date: 2018-04-27 10:03:38
categories:
- 剑指Offer
---

> 题目：输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左、右子树的深度相差不超过 1，那么它就是一棵平衡二叉树。

<!-- more -->

## 思路 1：遍历节点的同时计算左右子树的深度

根据上一题的思路，我们可以**在遍历二叉树的节点的同时计算左右子树的深度，如果所有的左右子树都满足深度相差不超过 1，那么它是平衡的；否则它是不平衡的**。这个算法的缺陷在于，有很多重复遍历的节点，这样会造成时间效率的损失。

## 思路 2：后序遍历

为了不重复遍历节点，我们可以采用**后序遍历**的方式。在计算该节点的深度之前，我们已经计算出了左右子树的深度，并且可以判断该子树是否平衡。

## 实现

```java
public class Solution {
    public boolean IsBalanced_Solution(TreeNode root) {
        // 特殊输入的检查
        if (root == null)
            return true;

        return calDepth(root) != -1;
    }
    private int calDepth(TreeNode n) {
        // 退出边界
        if (n == null)
            return 0;

        // 后续遍历，自底向上
        int leftDepth = calDepth(n.left);
        if (leftDepth == -1)
            return -1;

        int rightDepth = calDepth(n.right);
        if (rightDepth == -1)
            return -1;

        return Math.abs(leftDepth - rightDepth) <= 1 ? Math.max(leftDepth, rightDepth) + 1 : -1;
    }
}
```