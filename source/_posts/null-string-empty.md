---
title: 「null」與「空字串」的差別
date: 2020-09-21 22:34:21
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
關於「`null`」與「空字串」的差別，簡單分辨如下：
<!-- more -->
null 和 空字串(`''`) 的意思，可參考[這篇文章](https://dotblogs.com.tw/gra/2018/06/10/121512)
文章內用裝水的容器來做比喻
空字串：本來裝水的容器今天沒裝水。
`null` ：一個是連裝水的容器都沒有。
`null` 常用在判斷這個變數是否為 `null`，接著去做執行下一步動作
而有些開發者不希望變數設置成 `let a = ''` 或是 `let a = {}` 
就會使用 `let a = null`