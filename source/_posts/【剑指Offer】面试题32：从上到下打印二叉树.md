---
title: 【剑指Offer】面试题32：从上到下打印二叉树
date: 2018-04-04 10:07:32
categories:
- 剑指Offer
---

> 题目：从上往下打印出二叉树的每个节点，同层节点从左至右打印。

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

import java.util.*;

public class Solution {
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<>();

        // 特殊输入的检查
        if (root == null)
            return res;

        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while (!q.isEmpty()) {
            TreeNode n = q.remove();
            res.add(n.val);
            if (n.left != null)
                q.add(n.left);
            if (n.right != null)
                q.add(n.right);
        }

        return res;
    }
}
```