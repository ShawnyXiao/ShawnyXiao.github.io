---
title: 【剑指Offer】面试题26：树的子结构
date: 2018-04-03 21:35:58
categories:
- 剑指Offer
---

> 题目：输入两棵二叉树 A，B，判断 B 是不是 A 的子结构。（ps：我们约定空树不是任意一个树的子结构）

<!-- more -->

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
    public boolean HasSubtree(TreeNode root1,TreeNode root2) {
        // 特殊输入的检查
        if (root1 == null || root2 == null)
            return false;

        return recursiveVisitTree(root1, root2);
    }

    // 先序遍历
    private boolean recursiveVisitTree(TreeNode n, TreeNode m) {
        // 退出边界
        if (n == null)
            return false;

        boolean result = false;
        if (n.val == m.val) {
            result = hasSameStructure(n, m);
        }

        return result || recursiveVisitTree(n.left, m) || recursiveVisitTree(n.right, m);
    }

    private boolean hasSameStructure(TreeNode n, TreeNode m) {
        if (m == null)
            return true;
        if (n == null)
            return false;

        return (n.val == m.val) && hasSameStructure(n.left, m.left) && hasSameStructure(n.right, m.right);
    }
}
```