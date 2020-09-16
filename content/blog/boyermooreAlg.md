---
title: "Introduction: Boyer-Moore majority vote algorithm"
date: 2020-08-21T16:17:45+08:00
author: "Eklipsorz"
description : "利用+1和-1來尋找佔多數的元素"
keywords:
- majority element
- Boyer Moore
- Algorithm
tags : [
    "algorithm",
    "math",
]
categories : [
    "algorithm",
]

markup: "mmark"

draft: true
---

![](/img/boyermooreAlg/cover.jpeg)

## Overview


## Proof: why the algorithm works

根據演算法給予的條件，我們可以總結二個觀察結果：
(利用一些簡單的例子從同位所支持的候選者到增加一些反對者的數量來說明)


1. 當探訪某個區間內的投票者並且$k$值是等於0時，那就代表下一個投票者將會決定何人是較多人支持的。
2. 當探訪某個區間內的投票者並且$k$值是大於0時，那就代表較多人支持的人會是目前候選人或者下一個投票者所支持的候選人。


那麼當出現超過半數支持的候選者時，$k$值勢必會在所有投票者中會是大於0，並且也代表著程式最後的執行結果會是該候選者，但若

利用前面提到的觀察結果，若出現超過半數支持的候選者時，勢必會讓$k$值大於0，並且判定候選者為最多人支持。

## Performance


## Conclusion

