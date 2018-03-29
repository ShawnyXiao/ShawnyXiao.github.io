---
title: 【剑指Offer】面试题11：旋转数组的最小数字
date: 2018-03-22 18:37:21
categories:
- 剑指Offer
---

> 题目：把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。例如数组 {3, 4, 5, 1, 2} 为 {1, 2, 3, 4, 5} 的一个旋转，该数组的最小值为 1。

## 实现

```java
import java.util.ArrayList;
public class Solution {
    public int minNumberInRotateArray(int[] array) {
        // 特殊输入的检查
        if (array == null || array.length == 0)
            return 0;
        if (array.length == 1)
            return array[0];

        // 如果数组的第一个值小于最后一个值，就返回第一个值
        int lo = 0, hi = array.length - 1;
        if (array[lo] < array[hi]) {
            return array[0];
        }

        // 如果数组的第一个值大于最后一个值，就二分查找
        if (array[lo] > array[hi]) {
            int mid;
            while(lo <= hi) {
                mid = lo + (hi - lo) / 2;
                if (array[mid] > array[mid + 1])
                    return array[mid + 1];
                if (array[mid] <= array[hi])
                    hi = mid;
                else
                    lo = mid;
            }
        }

        // 如果数组的第一个值等于最后一个值，穷举
        int min = Integer.MAX_VALUE;
        for (int i = 0; i < array.length; i++) {
            if (min > array[i])
                min = array[i];
        }
        return min;
    }
}
```