---
title: 【剑指Offer】面试题7：重建二叉树
date: 2018-03-21 15:32:03
categories:
- 剑指Offer
---

> 题目：输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列 {1, 2, 4, 7, 3, 5, 6, 8} 和中序遍历序列 {4, 7, 2, 1, 5, 3, 8, 6}，则重建二叉树并返回。

## 实现

```java
/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

public class Solution {
    public TreeNode reConstructBinaryTree(int [] pre,int [] in) {
        // 特殊输入检查
        if (pre == null || in == null || pre.length == 0 || in.length == 0 || pre.length != in.length)
            return null;

        // 递归的生成树
        return reConstructBinaryTreeRecursive(pre, in, 0, pre.length - 1, 0, in.length - 1);
    }

    private TreeNode reConstructBinaryTreeRecursive(int[] pre, int[] in, int preLo, int preHi, int inLo, int inHi) {
        // 递归退出边界
        if (preLo > preHi || inLo > inHi)
            return null;

        // 首先构造当前节点
        TreeNode n = new TreeNode(pre[preLo]);

        // 然后构造左右子树
        for (int i = inLo; i <= inHi; i++) {
            if (in[i] == pre[preLo]) {
                n.left = reConstructBinaryTreeRecursive(pre, in, preLo + 1, preLo + i - inLo, inLo, i - 1);
                n.right = reConstructBinaryTreeRecursive(pre, in, preLo + i - inLo + 1, preHi, i + 1, inHi);
                break;
            }
        }

        return n;
    }

}
```