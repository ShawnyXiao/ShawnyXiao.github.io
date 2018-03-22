---
title: 【剑指Offer】面试题9：用两个栈实现队列
date: 2018-03-22 18:33:10
categories:
- 剑指Offer
---

> 题目：用两个栈来实现一个队列，完成队列的 Push 和 Pop 操作。 队列中的元素为 int 类型。

## 实现

```java
import java.util.Stack;

public class Solution {
    Stack<Integer> stack1 = new Stack<Integer>(); // 入
    Stack<Integer> stack2 = new Stack<Integer>(); // 出

    public void push(int node) {
        stack1.push(node);
    }

    public int pop() {
        if (!stack2.empty())
            return stack2.pop();

        while(!stack1.empty()) {
            stack2.push(stack1.pop());
        }

        return stack2.pop();
    }
}
```