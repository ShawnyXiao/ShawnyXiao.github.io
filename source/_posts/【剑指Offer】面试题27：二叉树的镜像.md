---
title: 【剑指Offer】面试题27：二叉树的镜像
date: 2018-04-03 21:36:17
categories:
- 剑指Offer
---

> 题目：操作给定的二叉树，将其变换为源二叉树的镜像。
输入描述:
二叉树的镜像定义：
源二叉树：
&nbsp;&nbsp;&nbsp;&nbsp;8
&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;\\
&nbsp;&nbsp;6&nbsp;&nbsp;10
&nbsp;/&nbsp;\&nbsp;&nbsp;&nbsp;/&nbsp;\\
5&nbsp;7&nbsp;9&nbsp;11
镜像二叉树：
&nbsp;&nbsp;&nbsp;&nbsp;8
&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;\\
&nbsp;10&nbsp;&nbsp;6
&nbsp;/&nbsp;\&nbsp;&nbsp;/&nbsp;\\
11&nbsp;9&nbsp;7&nbsp;5

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
    public void Mirror(TreeNode root) {
    	// 特殊输入的检查
        if (root == null)
            return;

        TreeNode tmp = root.left;
        root.left = root.right;
        root.right = tmp;

        Mirror(root.left);
        Mirror(root.right);
    }
}
```