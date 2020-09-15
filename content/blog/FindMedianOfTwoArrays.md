---
title: "Another point of view: how to find median of two sorted arrays"
date: 2020-09-15T16:38:44+08:00
author: "Eklipsorz"
description : "從另種觀點來看待如何找尋中位數(Median)"
keywords:
- Median of two sorted array
- Median
- LeetCode
tags : [
    "Algorithm",
    "LeetCode",
]
categories : [
    "Algorithm",
]

markup: "mmark"

draft: true
---

![](/img/FindMedianOfTwoArrays/cover.jpg)


假設我們給你兩個已經排序好的序列(如下圖)並且要求你想像這兩個序列按照數字大小重新排列成一個大序列，然後從這個序列中求得中位數(Median)
，那麼你會如何解決這件事情呢？

1. 按照數字大小重新將這兩個序列上的數字排列成一個較大的序列，再得到中位數。
2. 不排列一個較大序列，而是直接從這兩個序列的關係來得到中位數。

若選擇第一個解法，勢必會花上$O(n)$的時間和空間成本來重新排列，比如說

(舉一個算法以及附圖)

但若我們想讓成本降下來，那麼或許可以使用第二個方法來解，本文將以第二個方法來說明

## 解法


### 使用遞增/遞減來解決


### 使用Binary search來解決


## 效能

### 效能：使用遞增/遞減


### 效能：使用Binary search


## 總結

## 參考文獻

