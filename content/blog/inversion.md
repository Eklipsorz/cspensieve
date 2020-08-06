---
title: "The releation between sorting and inversion"
date: 2020-08-06T16:18:40+08:00
author: "Eklipsorz"
description : "從Inversion觀點看待排序"
keywords:
- inversion
- sorting
- algorithm
tags : [
    "inversion",
    "sorting",
]
categories : [
    "algorithm",
]

markup: "mmark"
draft: true
---



在此章節中，將會先介紹Inversion所擁有的特性，接著再另開一個章節從它的角度去看待每個常見的排序算法。

直觀上，每個排序演算法的目的是將不符合順序的元素序列轉換成符合預期順序的元素序列，比如轉換成由小排到大的序列或者由大排到小的序列。
然而我們要如何轉換成我們想要的順序或者這些演算法該以什麼作為核心來處理序列呢？

仔細想想，每個序列中或多或少會存在著一種序列對是不符合我們想要的順序：由小排到大或者由大排到小，在這裏我們先拿前者標準做舉例，並
拿$3, 5 ,1$當作上述提到的序列，那麼$(5,1)$就是其中一個不符合由小排到大規則的序列對，而這種序列對在這裏稱之為Inversion或者顛倒序列對，
相反地，考慮著$1,3,5$這序列時，你便透過前者規則來得到0個顛倒序列對數。


## 顛倒序列對的基本消去方法

