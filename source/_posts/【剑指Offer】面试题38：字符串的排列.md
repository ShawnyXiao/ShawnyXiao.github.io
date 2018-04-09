---
title: 【剑指Offer】面试题38：字符串的排列
date: 2018-04-09 10:23:42
categories:
- 剑指Offer
---

> 题目：输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。

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
    private TreeNode head;
    private TreeNode curNode;

    public TreeNode Convert(TreeNode pRootOfTree) {
    	// 退出边界
        if (pRootOfTree == null)
            return null;

        inorder(pRootOfTree);
        return head;
    }

    private void inorder(TreeNode n) {
        if (n == null)
            return;

        inorder(n.left);
        if (curNode == null) {
            head = n;
            curNode = n;
        } else {
            curNode.right = n;
            n.left = curNode;
            curNode = n;
        }
        inorder(n.right);
    }
}
```