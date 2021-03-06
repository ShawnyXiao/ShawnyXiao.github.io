---
title: 【剑指Offer】面试题46：把数字翻译成字符串
date: 2018-02-27 20:01:48
categories:
- 剑指Offer
---

> 题目：给定一个数字，我们按照如下规则把它翻译成字符串：0 翻译成“a”，1 翻译成“b”，……，11 翻译成“l”，……，25 翻译成“z”。一个数字可能有多个翻译。例如，12258 有 5 种不同的翻译，分别是“bccfi”、“bwfi”、“bczi”、“mcfi”和“mzi”。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

<!-- more -->

## 思路 1：动态规划

这题很明显是一道动态规划的题目，我们可以举例来分析一下：“12258 的翻译种数”=“1225 的翻译种数”；“1225 的翻译种数”=“122 的翻译种数”+“12 的翻译种数”；“122 的翻译种数”=“12 的翻译种数”+“1 的翻译种数”；“12 的翻译种数”=“1 的翻译种数”；“1 的翻译种数=1”。

从以上的分析，我们可以看出，这个问题可以拆分成多个子问题来求解，并且子问题有重叠部分，状态转移方程如下：

$$
f(i) =
\begin{cases}
f(i-1)+f(i-2), & 0 \leq c(i-1,i) \leq 25\\\
f(i-1), & otherwise
\end{cases}
$$

其中，f(i) 表示数字从左往右第 i 个的翻译种数，c(i-1, i) 表示数字从左往右第 i - 1 和第 i 个字符拼接后的数字（例如：12258 的 c(1, 2)=22）。