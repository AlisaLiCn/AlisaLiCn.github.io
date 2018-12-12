---
title: 【算法】CodingInterview 10 - 斐波那契数列
date: 2018-12-11 23:10:12
category: Tech
tags: JavaScript
---

最近在看剑指Offer，就整理一下算法面试题吧~

斐波那契数列在我之前的面试中遇到过，所以先来总结下它吧~

> 原著源码：[Github](https://github.com/zhedahht/CodingInterviewChinese2/tree/master/10_Fibonacci)  
> 本文源码：[Github](https://github.com/AlisaLiCn/Algorithm/tree/master/10_fibonacci)

#  CodingInterview 10 - 斐波那契数列

>问题描述：求斐波那契数列的第n项。
>
>写一个函数，输入n，求斐波那契（Fibonacci）数列的第n项。
>斐波那契数列：1,1,2,3,5,8,13,21...

## 方法1：递归法
递归法的优缺点：
- 优点：简单直观，根据公式f(n) = f(n-1) + f(n-2)即可实现。
- 缺点：虽然是上学时课本上的经典递归案例，但由于实际的重复计算次数太多，导致时间复杂度高，效率很低。

JS代码：
```javascript
function fibonacci_1(n) {
  if (typeof n !== 'number' || Number.isNaN(n)) {
    throw Error('Invalid param n, n should be a valid number')
  }
  if (n <= 0) return 0
  if (n === 1) return 1
  return fibonacci_1(n - 1) + fibonacci_1(n - 2)
}
```


## 方法2：循环法
循环法避免了递归法的重复计算，从计算前两项开始，依次算出后面的各项，直到第n项。

时间复杂度为：O(n)

JS代码
```javascript
function fibonacci_2(n) {
  if (typeof n !== 'number' || Number.isNaN(n)) {
    throw Error('Invalid param n, n should be a valid number')
  }
  if (n <= 0) return 0
  if (n === 1) return 1
  let fibNMinusOne = 1
  let fibNMinusTwo = 0
  let fibN = 0
  for (let i = 2; i <= n; ++i) {
    fibN = fibNMinusOne + fibNMinusTwo // f(n) = f(n-1) + f(n-2)
    fibNMinusTwo = fibNMinusOne
    fibNMinusOne = fibN
  }
  return fibN
}
```

书中还有复杂度最低的一种矩阵乘法方式，但不够实用，可以参考[作者的源码(C++版)](https://github.com/zhedahht/CodingInterviewChinese2/blob/master/10_Fibonacci/Fibonacci.cpp)












