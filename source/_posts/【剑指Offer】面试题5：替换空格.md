---
title: 【剑指Offer】面试题5：替换空格
date: 2018-03-21 15:31:01
categories:
- 剑指Offer
---

> 题目：请实现一个函数，将一个字符串中的空格替换成 “%20”。例如，当字符串为 We Are Happy，则经过替换之后的字符串为 We%20Are%20Happy。

<!-- more -->

## 实现

```java
public class Solution {
    public String replaceSpace(StringBuffer str) {
    	// 特殊输入检查
        if (str == null || str.length() == 0)
            return "";

        char[] strCharArr = str.toString().toCharArray();

        // 统计空格数量
        int spaceNum = 0;
        for (int i = 0; i < strCharArr.length; i++)
            if (strCharArr[i] == ' ')
                spaceNum++;

        // 构造新字符数组
        char[] repStrCharArr = new char[strCharArr.length + spaceNum * 2];
        int j = 0;
        for (int i = 0; i < strCharArr.length; i++) {
            if (strCharArr[i] == ' ') {
                repStrCharArr[j++] = '%';
                repStrCharArr[j++] = '2';
                repStrCharArr[j++] = '0';
                continue;
            }
            repStrCharArr[j++] = strCharArr[i];
        }

        return String.valueOf(repStrCharArr);
    }
}
```