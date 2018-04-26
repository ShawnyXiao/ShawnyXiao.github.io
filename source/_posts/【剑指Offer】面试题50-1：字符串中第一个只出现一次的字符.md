---
title: 【剑指Offer】面试题50-1：字符串中第一个只出现一次的字符
date: 2018-04-26 09:32:26
categories:
- 剑指Offer
---

> 题目：在字符串中找出第一个只出现一次的字符。如输入“abaccdeff”，则输出‘b’。

<!-- more -->

## 思路 1：从左到右判断每个字符其后是否还有出现过

最直接的思路是：**对于字符串，从左到右扫描每个字符，判断该字符之后的字符是否还出现过，输入第一个之后没有出现过的字符**。这种思路简单而直观，但是对 n 个字符扫描，并判断其后的 O(n) 个字符是否重复，这需要 $O(n^2)$ 的时间复杂度，我们需要思考更快的算法。

## 思路 2：哈希表

我们可以使用某种数据容器记录每个字符出现的次数，把字符映射成数字的数据容器，哈希表正是这种数据容器。这个思路是：**第一次扫描字符串记录每个字符出现的次数，第二次扫描字符串找出第一个次数为 1 的字符**。只用扫描两次字符串就能达到目的，该算法的时间复杂度是 $O(n\,log\,n)$。

## 实现

```java
import java.util.*;

public class Solution {
    public int FirstNotRepeatingChar(String str) {
        // 特殊输入的检查
        if (str == null || str.length() <= 0)
            return -1;
        if (str.length() == 1)
            return 0;

        // 哈希表存次数
        Map<Character, Integer> m = new HashMap<>();
        for (int i = 0; i < str.length(); i++) {
            if (m.containsKey(str.charAt(i))) {
                m.put(str.charAt(i), m.get(str.charAt(i)) + 1);
                continue;
            }
            m.put(str.charAt(i), 1);
        }

        // 遍历数组取第一个只出现一次的字符
        for (int i = 0; i < str.length(); i++)
            if (m.get(str.charAt(i)) == 1)
                return i;
        return -1;
    }
}
```