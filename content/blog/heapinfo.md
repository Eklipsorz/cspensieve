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

#### 以Binary Heap以及它帶有的Method來更清楚地介紹Heap

根據Structure Property談到的定義：當我們指定被堆放的物件數時，我們會稱之為k-ary Heap，在這裡如果我們要堆放的物件數是2個時，我們會稱之為Binary Heap
，我們可以透過Binary Tree(BT)的左右子樹節點就能表示，換言之，每個節點能夠連接兩個相同型態的節點。在Binary Tree下的Structure Property和Heap Order 
Property 這兩個性質會在保持著Heap的原有性質的情況下更加強調Binary Tree的實作。

### BT: Structure Property

在Structure Property上，會為了更加簡單地透過Array來實作Binary Tree而強調該樹狀結構必須是Complete Tree為原則，換言之，除了最後一層的節點之外，每層的
節點數都必須是$2^k$個節點，而$k$是表示第$k$個階層，而最後一層的節點數可以少於 $2^m$ ($m$為最後一層的階層第次) 個，舉例來說，我們會預期最後一層的節
點位置會是下圖，這些白圈並沒有節點而只是代表著預期位置，

{{< CenterImage
src="/img/heapinfo/expectedNodes.png"
alt="最後一層的預期節點位置" >}}


當指定該樹狀結構為Complete Tree時，節點位置$A1$至$AM$之間必須是都不存在節點或者節點$A1$至某個節點之間都存在著節點，若是後者的話，會像是下圖左右兩邊，
左邊代表著$A1$至某個節點之間都存在著節點，而右邊會是全部的位置都被節點填滿。

{{< CenterImage
src="/img/heapinfo/continuousNodes.png"
alt="最後一層的預期節點位置" >}}

然而中間沒有任何節點可以保持連續性。

{{< CenterImage
src="/img/heapinfo/discontinuousNodes.png"
alt="表示Complete Tree" >}}



當我們依照這樣實作規則製作出Complete Binary Tree並且由上層來依序給予序號(如下圖)，會發現每個節點$i$的子節點會是節點$2i$或者節點$2i+1$，這時我們就可以

{{< CenterImage
src="/img/heapinfo/completeTree.png"
alt="表示Complete Tree" >}}

直接宣告一個固定大小的陣列來實作Binary Tree，並且利用節點與其子節點的序號關係來存取，index為1的記憶體空間為root節點，而root節點的子節點就是index為2~3的
記憶體空間，當我們想存取某節點$i$的子節點時，便直接朝著index為$2i$以及$2i+1$的記憶體空間來存取。


### BT: Heap Order Property

Heap Order Property在這裡會以數值系統來比較並且採用以Min Heap為主的基準來建立Heap，也就是說會拿每個物件所儲存的數值來將每個節點堆積到另外兩個數值比較大的
節點上。


### BT: How to get object from the structure

而當我們要從Heap結構取出物件時，便是拿Binary Tree上的root節點，並且從剩餘節點中挑出適當的節點來頂替root節點以維持Structure Property和Heap Order Property這
兩個性質。
