---
title: this 調用方式 (1)
date: 2020-10-31 17:03:04
categories: JavaScript
tags:
  - JavaScript
---
`this` 調用方式：
「作為物件方法」和「簡易呼叫」內容
<!-- more -->
## 作為物件方法 (最常運用 `this` 的方法)
 `this` 的指向在物件的方法調用是最常見的形式，以下為兩個重點：

>*  `this` 與函式如何宣告**沒有關聯性**，僅與呼叫方式有關
>*  物件的方法調用時，僅需要關注**是在哪一個物件**下呼叫

假設在一個物件下去呼叫一個函式，那這個 `this` 的指向就是前面的物件，只要掌握這個觀念，就可運用最常見的 `this` 調用方式，如下圖
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-5.png)
這邊也提供範例參考
要注意的是不管是這個函式是如何定義的，只要了解是在哪個物件下來呼叫這個 `this`

```sh
var item = '茶壺';
var data = {
  item:'杯子',
  num: count,
}
function count() {
  console.log(this.item); // 杯子
}
data.num();
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-6.png)

## 簡易呼叫
下方的範例為「簡易呼叫」(`simple call`) 
`simple call` 的 `this` 都指向 `window`
```sh
var num = 10;
function count() {
  console.log(this, this.num); 
}
count();
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-7.png)

這邊要注意一件事情，我們所理解的全域是掛在 `window` 物件下，所以很多人以為執行 `simple call` 是如下圖圈選的概念 `window.count`
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-8.png)
所以他會調用全域的 `window`
但是 `simple call` 的概念並非是在 `window` 底下執行這個函式，並不是執行函式的概念
像是下圖 11 行的立即函式裡面 `test()` 並不是屬於全域下的變數
所以 `window.test()` 並沒有辦法直接去執行

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-9.png)

> 簡單來說若是看到一個函式，他是直接執行，他就屬於 `simple call`
但是他不是在全域的物件下去執行一個函式