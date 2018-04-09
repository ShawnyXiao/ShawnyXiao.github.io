---
title: 【剑指Offer】面试题36：二叉搜索树与双向链表
date: 2018-04-09 10:23:21
categories:
- 剑指Offer
---

> 题目：输入一个字符串，按字典序打印出该字符串中字符的所有排列。例如输入字符串 abc，则打印出由字符 a, b, c 所能排列出来的所有字符串 abc, acb, bac, bca, cab 和 cba。

<!-- more -->

## 实现

```java
import java.util.*;

public class Solution {
    public ArrayList<String> Permutation(String str) {
        ArrayList<String> res = new ArrayList<>();

        // 特殊输入的检查
        if (str == null || str.length() == 0)
            return res;

        perm(str.toCharArray(), 0, res);
        Collections.sort(res);
        return res;
    }

    private void perm(char[] s, int ind, ArrayList<String> res) {
        // 退出边界
        if (ind == s.length - 1) {
            res.add(String.valueOf(s));
            return;
        }

        Set<Character> set = new HashSet<>();
        for (int i = ind; i < s.length; i++) {
            if (set.contains(s[i]))
                continue;
            set.add(s[i]);
            swap(s, ind, i);
            perm(s, ind + 1, res);
            swap(s, ind, i);
        }
    }

    private void swap(char[] s, int a, int b) {
        // 参数检查
        if (a < 0 || a >= s.length || b < 0 || b >= s.length)
            throw new RuntimeException("超出数组边界");

        char tmp = s[a];
        s[a] = s[b];
        s[b] = tmp;
    }
}
```