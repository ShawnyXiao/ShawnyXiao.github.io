---
title: 【剑指Offer】面试题31：栈的压入、弹出序列
date: 2018-04-04 10:07:14
categories:
- 剑指Offer
---

> 题目：输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列 1, 2, 3, 4, 5 是某栈的压入顺序，序列 4, 5, 3, 2, 1 是该压栈序列对应的一个弹出序列，但 4, 3, 5, 1, 2 就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）


<!-- more -->

## 实现

```java
import java.util.ArrayList;
import java.util.Stack;

public class Solution {
    public boolean IsPopOrder(int[] pushA, int[] popA) {
        // 特殊输入的检查
        if (pushA == null || pushA.length == 0 || popA == null || popA.length == 0 || pushA.length != popA.length)
            return false;

        Stack<Integer> s = new Stack<>();
        for (int i = 0, j = 0; i < pushA.length; i++) {
            s.push(pushA[i]);
            while (j < popA.length && s.peek() == popA[j]) {
                s.pop();
                j++;
            }
        }
        return s.empty();
    }
}
```