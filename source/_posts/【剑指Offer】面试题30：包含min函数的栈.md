---
title: 【剑指Offer】面试题30：包含min函数的栈
date: 2018-04-04 10:06:57
categories:
- 剑指Offer
---

> 题目：定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。

<!-- more -->

## 实现

```java
import java.util.Stack;

public class Solution {
    private Stack<Integer> s = new Stack<>();
    private Stack<Integer> min = new Stack<>();

    public void push(int node) {
        if (min.empty()) {
            s.push(node);
            min.push(node);
            return;
        }

        s.push(node);
        min.push((node < min.peek()) ? node : min.peek());
    }

    public void pop() {
        s.pop();
        min.pop();
    }

    public int top() {
        return s.peek();
    }

    public int min() {
        return min.peek();
    }
}
```