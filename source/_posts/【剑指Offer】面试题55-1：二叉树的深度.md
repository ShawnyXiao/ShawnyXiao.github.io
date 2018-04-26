---
title: 【剑指Offer】面试题55-1：二叉树的深度
date: 2018-04-26 17:30:19
categories:
- 剑指Offer
---

> 题目：输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点一次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

<!-- more -->

## 思路：左右子树的最大深度加一

我们递归来求解二叉树的深度，思路如下：**如果一棵树只有一个节点，那么它的深度为 1；如果一棵树不止一个节点，那么它的深度等于左、右子树中的深度的最大值加一**。

## 实现

```java
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;
    public TreeNode(int val) {
        this.val = val;
    }
}
*/
public class Solution {
    public int TreeDepth(TreeNode root) {
        // 退出边界
        if (root == null)
            return 0;

        return Math.max(TreeDepth(root.left), TreeDepth(root.right)) + 1;
    }
}
```