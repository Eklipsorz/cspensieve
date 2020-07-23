---
title: "Introduction: Floyd Cycle Detection"
date: 2020-07-21T15:05:34+08:00
author: "Eklipsorz"
description : "一個利用兩個Pointer來解決List上的循環問題"
tags : [
    "Algorithm",
    "Cycle Detection",
]
categories : [
    "Algorithm",
]

markup: "mmark"

draft: true
---



當你想解決任何一個需要檢測在多個相互連接的元素是否著環狀結構之場景，比如說  
1. 道路模型。  
2. 由多個有限狀態所組成的數學模型。  
3. 有限輸入下在同一個函式$f(x)$所形成的結果，比如集合為$\\{1,2\\}$，且$f(1)=2$以及$f(2)=1$，在這裏1和2就透過函式關係形成一個環狀結構。  

你會怎麼檢測它？放棄它，反正以後碰不上？  
當然我會建議不放棄它，畢竟你不能夠確定在未來路上不會遇上類似的問題，那麼正式進入正題，如果冷靜思考的話，其實不論哪一個場景，都可以將這
些場景轉化成由多個節點所組成的結構：


![](/img/floydCycleDetect/ListAexample.png)

或者

![](/img/floydCycleDetect/ListBexample.png)


當我們轉換成如此的結構時，我們可以更容易以肉眼看出哪些模型存在著循環，在這裏我們可以知道List A是存在著循環，而List B由於尾巴部分並未跟
前幾個節點相接，所以不構成循環。在這裡你或許會選擇以肉眼來辨識，但現實是當面對大量或者複雜的模型時，肉眼看會顯得效率太差，所以最好由電
腦進行這樣的重複辨識工作。    

可換作是電腦，它要如何辨識呢？畢竟他本身就不存在像人眼那樣的辨識模型，在這裏提供一個方法來幫助電腦辨識：Floyd's Cycle Detection Algorithm，
傳說是由Robert W. Floyd所發明的演算法，所以以它的名字來命名，普遍上會以演算法的特色來稱呼：龜兔賽跑算法。顧名思義，這個算法會假設一隻烏龜和
一隻兔子在這個許多節點構成的List結構進行賽跑，烏龜每次只能走一個節點，而兔子只能走二個節點，他們只要跑下去肯定能到循環裡，最終如果他們能在循
環中碰面或者在同一點會合的話，就表示這個結構上存在著循環。(如下圖所示)

{{< CenterImage
src="/img/floydCycleDetect/CycleExample.png"
alt="擁有循環的List結構" >}}

然而，如果兔子走到結構中的終點卻沒跟烏龜會合的話，那就表示著結構不存著循環。(如下圖)


{{< CenterImage
src="/img/floydCycleDetect/NoCycleExample.png"
alt="沒擁有循環的List結構" >}}

