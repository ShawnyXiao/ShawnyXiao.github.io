---
title: 【剑指Offer】面试题34：二叉树中和为某一值的路径
date: 2018-04-07 19:01:06
categories:
- 剑指Offer
---

> 题目：输入一颗二叉树和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。

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

import java.util.ArrayList;

public class Solution {
    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root, int target) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();

        // 特殊输入的检查
        if (root == null)
            return res;

        recursiveFindPath(root, target, 0, new ArrayList<Integer>(), res);

        return res;
    }

    private void recursiveFindPath(TreeNode n, int t, int sum, ArrayList<Integer> path, ArrayList<ArrayList<Integer>> res) {
        // 退出边界
        if (n == null)
            return;

        sum += n.val;
        path.add(n.val);

        // 检查是否是叶子节点
        if (n.left == null && n.right == null) {
            if (sum == t) {
                res.add(new ArrayList(path));
            }
        }

        recursiveFindPath(n.left, t, sum, path, res);
        recursiveFindPath(n.right, t, sum, path, res);
        path.remove(path.size() - 1);
    }
}
```
