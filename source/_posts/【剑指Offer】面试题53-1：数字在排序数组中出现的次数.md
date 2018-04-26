---
title: 【剑指Offer】面试题53-1：数字在排序数组中出现的次数
date: 2018-04-26 14:26:14
categories:
- 剑指Offer
---

> 题目：统计一个数字在排序数组中出现的次数。例如，输入排序数组 {1, 2, 3, 3, 3, 3, 3, 4, 5} 和数字 3，由于 3 在这个数组中出现了 4 次，因此输出 4。

<!-- more -->

## 思路 1：遍历

最直观的思路是：**从左到右遍历整个数组，对需要统计的数字计数**。这样的算法的时间复杂度是 O(n)。我们应该在思考一下。

## 思路 2：二分查找

对于在排序数组中查找数字，我们第一时间应该想到二分查找。假设我们要找的数字是 k，这个算法的思路是：**找到第一个和最后一个等于 k 的数字**。

找第一个等于 k 的数字：使用二分查找算法找到数组中位于中间的数字，拿该数字与 k 比较，如果 k 大于该数字，说明 k 在右边的部分，对右边继续使用二分查找算法。如果 k 小于该数字，说明 k 在左边的部分，对左边继续使用二分查找算法。如果 k 等于该数字，比较一下该数字前面的数字是不是等于 k，如果不等于 k，说明该数字就是第一个等于 k 的数字；如果前面的数字等于 k，说明第一个数字在左边的部分，继续对左边使用二分查找算法。找最后一个等于 k 的数字是同样的道理。

找第一个和最后一个等于 k 的数字的操作所需要的时间复杂度是 $O(log\,n)$，因此整个算法的时间复杂度也是 $O(log\,n)$。

## 实现

```java
public class Solution {
    public int GetNumberOfK(int[] array, int k) {
        // 特殊输入的检查
        if (array == null || array.length == 0)
            return 0;
        if (k < array[0] || k > array[array.length - 1])
            return 0;

        // 二分查找：第一个和最后一个的索引
        int firstInd = binarySearchFirst(array, k);
        int lastInd = binarySearchLast(array, k);

        return firstInd == -1 ? 0 : lastInd - firstInd + 1;
    }

    private int binarySearchFirst(int[] a, int k) {
        int lo = 0;
        int hi = a.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (a[mid] == k && (mid - 1 < lo || a[mid - 1] < k))
                return mid;
            else if (a[mid] < k)
                lo = mid + 1;
            else
                hi = mid - 1;
        }
        return -1;
    }

    private int binarySearchLast(int[] a, int k) {
        int lo = 0;
        int hi = a.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (a[mid] == k && (mid + 1 > hi || a[mid + 1] > k))
                return mid;
            else if (a[mid] > k)
                hi = mid - 1;
            else
                lo = mid + 1;
        }
        return -1;
    }
}
```