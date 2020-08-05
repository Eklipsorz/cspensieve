---
title: "Another Point of View： Heap Structure"
date: 2020-08-05T20:25:08+08:00
author: "Eklipsorz"
description : "另種觀點來看待Heap結構"
keywords:
- heap
- data structure
tags : [
    "heap",
    "tree",
]
categories : [
    "Data Structure",
]

markup: "mmark"

draft: true
---

本文會嘗試用Heap的意思來重新介紹Heap結構以及它的概念是如何被實作的。

## Heap 概略

1.  Structure Property：它是一種特殊的資料結構，其結構如同字面上的意思一樣，結構上的每個物件$Obj_i$會堆放在其他物件上：

2.  Heap Order Property：根據物件所儲存的資料來堆放其他物件上，比如以每個物件所儲存的數值來比較大小，數值比較小的節點會
堆放數值較大的節點上。

3. 每當從這個結構取出物件時，會優先從結構頂端來取。

4. 通常使用樹狀結構來實現，在這實現上不能夠違背前面三個提到的性質，實現上會有Initialization、Insert、Delete等Method。

5. 應用：Priority Queue、Sorting。
