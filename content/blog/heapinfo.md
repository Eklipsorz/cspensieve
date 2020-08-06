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

![](/img/heapinfo/cover.jpg)

## Heap 概略

#### 粗略地介紹Heap的構造、特性、實現

1. Structure Property：它是一種特殊的資料結構，其結構如同字面上的意思一樣，每個物件$Obj_i$會堆放其他物件上，最後形成一
座堆狀物：

{{< CenterImage
src="/img/heapinfo/2kheap.png"
alt="表示某個物件$Obj_i$被堆放在其他物件上" >}}

2.  Heap Order Property：根據物件所儲存的資料來堆放其他物件上，比如以每個物件所儲存的數值來比較大小，數值比較小的節點會
堆放數值較大的節點上。

3. 每當從這個結構取出物件時，會優先從結構頂端來取。

4. 通常使用樹狀結構來實現，在這實現上不能夠違背前面三個提到的性質，實現上會有Initialization、Insert、Delete等Method。

5. 應用：Priority Queue、Sorting。


## Structure Property

#### 定義該結構會是什麼

在這個結構內，每個物件都堆放在其他物件上，進而使整體結構像是堆狀物，當我們指定被堆放的最大物件數時，我們會稱之為$k$-ary Heap，$k$為物件數
，如果$k = 2$就代表著每個物件只能堆放在$0-2$個物件上(如下圖中的左半邊)，而如果$k = 3$就代表著每個物件只能堆放在$0-3$個物件上，不管$k$是為何
，Heap下的每個節點會像下圖中那樣排列著，而圖中的obj指的就是堆放物，而$1-k$指的是被堆放物。


{{< CenterImage
src="/img/heapinfo/2kheapdetail.png"
alt="表示k-ary Heap" >}}

理想狀態下，我們可以透過本性質將每個節點堆成一座小山，最後再將每座小山構成一座大山，比如說在Binary Heap下，原本每個節點構成的小山(下圖左半邊)
會被堆放在一起形成一座大山(下圖右半邊)。

{{< CenterImage
src="/img/heapinfo/makeabigone.png"
alt="表示多個小山組成一座大山" >}}

## Heap Order Property

根據Structure Property提到的內容，這些物件會構成一個堆狀物，但內容卻沒指定這些物件彼此間關係是為何，而且當要從堆狀物取出物件時，取出的物件會在
不確定的情況下變得毫無意義，因爲我們並不能知道每此取出的物件會是什麼，所以為了讓取的物件更加有意義而添加Heap Order Property。

#### 定義這些物件彼此間的關係

我們會根據物件儲存的數值來決定如何堆放，通常會有兩種堆放基準：

1. 物件的數值比其他物件儲存的數值來得小時，就堆放在他們上面
2. 物件的數值比其他物件儲存的數值來得大時，就堆放在他們上面
 

不論選取哪個來堆放物件，該結構上的頂端物件肯定是所有物件裡最小或者最大的，然而如果在這個結構上混用這兩種方式，該頂端物件並不能夠保證其結果的大小
關係。此外，若我們單純使用第一個基準來堆放物件，那麼最後得到的Heap會根據取出的數值是最小的而被稱之為Min Heap；反之，若我們單純使用第二個基準來堆
放物件，那麼最後得到的Heap會被稱之為Max Heap。

對於這兩個基準的實現方式，會使用Tree結構的Parent節點和其所擁有的Child節點來表示堆放物件以及被堆放的物件。


## How to get object from the structure

基本上會先取得該結構上的頂端物件來盡量不破壞Structure Property，同時使用已在Heap的物件來代替頂端物件來維持著兩種特性，另外當我們想從多個物件中找
尋擁有最小值或最大值的物件時，該結構會很有效地幫助我們尋找，因爲頂端物件不是擁有最小值的物件，就是擁有最大值的物件。

## Heap Example
在這個章節會以Binary Heap以及它帶有的Method來更清楚地介紹Heap
