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
當然我會建議不放棄它，畢竟你不能夠確定在未來路上不會遇上類似的問題，那麼正式進入正題，如果冷靜思考的話，其實不論哪一個場景，都可以將這些場景轉化成由多個節點所組成的結構：


![](/img/floydCycleDetect/ListAexample.png)
