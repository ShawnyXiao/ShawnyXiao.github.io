---
title: 【剑指Offer】面试题40：最小的k个数
date: 2018-04-15 12:48:35
categories:
- 剑指Offer
---

> 题目：输入 n 个整数，找出其中最小的 k 个数。例如，输入 4、5、1、6、2、7、3、8 这 8 个数字，则最小的 4 个数字是 1、2、3、4。

<!-- more -->

## 思路 1：排序

最直接的思路是：**将这个输入的数组使用排序算法排序，然后前 k 个数字就是最小的 k 个数字**。但是这种方法的时间复杂度是 O(nlogn)，比较高，而且需要修改输入的数组，并且不适用于海量数据（海量数据无法一次性读入内存中）。

## 思路 2：Partition

我们一定要将整个数组彻底的排序才能找到最小的 k 个数字吗？不一定，这个算法的思路灵感来源于快速排序。

思路是：

- **挑选数组中的一个数字，调整数组的顺序，使得比选中的数字小的数字排在它的左边，比选中的数字大的数字排在它的右边**
- **查看这时选中的数字的索引是否等于 k 或者 k+1。如果等于 k，那么这时选中的数字与它左边的数字就是最小的 k 个数；如果等于 k+1，那么这时选中的数字的左边的数字就是最小的 k 个数；否则继续对右边的部分进行递归的搜索**

这个算法不需要将整个数据进行彻底的排序，只需要局部的排序就能达到目的。时间复杂度为 O(n)，但是需要修改输入的数组，并且不适用于海量数据。

## 思路 3：堆和红黑树

这个算法的思路其实很自然，就是**使用一个数据容器装着最小的 k 个数**。具体是：

- **从头到尾遍历数组**
- **如果数据容器没有装满，就将数字装入数据容器中；如果数据容器装满了，就选出数据容器中最大的数字，拿当前数字与这个最大的数字进行比较，如果当前数字大则抛弃它，如果当前数字小则替换掉最大的数字**

当数据容器选择堆或者红黑树时，对数据容器中的元素进行增删查只需要 O(logk) 的时间复杂度，然后我们需要遍历整个数组，因此这个算法的时间复杂度是 O(nlogk)。这个算法不需要修改输入数组，而且可以使用流的方式处理海量数据。

## 实现

```java
import java.util.ArrayList;
import java.util.PriorityQueue;

public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int[] input, int k) {
        ArrayList<Integer> res = new ArrayList<>();

        // 特殊输入的检查
        if (input == null || input.length == 0 || k == 0)
            return res;
        if (k > input.length)
            return res;

        // 最大堆的思路
        PriorityQueue<Integer> q = new PriorityQueue<>(k, (o1, o2) -> o2 - o1);
        for (int i = 0; i < k; i++)
            q.offer(input[i]);
        for (int i = k; i < input.length; i++) {
            if (input[i] > q.peek())
                continue;
            q.poll();
            q.offer(input[i]);
        }

        for (int a: q)
            res.add(a);

        return res;
    }
}
```