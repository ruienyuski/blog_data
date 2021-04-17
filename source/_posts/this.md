---
title: this 簡介
date: 2020-10-31 13:28:32
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`this` 觀念整理
<!-- more -->
## this 簡介

不管是在全域的環境下，或是在特定的函式，都可調用 `this` 這個關鍵字
那麼 `this` 因為在每個執行環境都存在，所以 `this` 很容易被誤認為指向函式
函式本身這個物件所能提供的屬性非常有限，通常來說不會使用函式調用 `this` 本身
`this`  通常是指向可以被運用的物件，所以不要誤認為函式中的 `this` 就指向該函式

`this` 是在執行函式時候就自然產生，不需要去宣告他，他是個關鍵字
如下圖 `Chrome` 的 `Source` 按下 `debug` 工具，按下圖中的按鈕
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-1.png)

重整之後來進入這個函式的執行堆疊
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-2.png)
並連續兩次按下圖片上的按鈕
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-3.png)
接下來會發現，`Local` 會自動帶上 `this`
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-4.png)
而這個 `this` 目前是指向 `window` 而這個 `this` 他實際指向跟我們如何去呼叫這個函式有很大的關連性

## this 基本觀念
*   每個執行環境都有屬於自己的 `this` 關鍵字
*   `this` 與函式如何宣告**沒有關聯性**，僅與呼叫方式有關
*   **嚴格模式**下，簡易呼叫會有很大的改變

## 常見的調用方式
`this` 的指向與怎麼呼叫他關係並不大，主要原因在怎麼去調用他
以下為常見的調用方式，這些調用方式就影響 `this` 的指向

>*   作為物件方法 (最常運用 `this` 的方法)
>*   簡易呼叫 (絕大多數的呼叫方式)
>*   `bind`，`apply`，`call` 方法
>*   `new`
>*   `DOM` 事件處理器
>*   箭頭函式 (`ES6`)

關於 this 的文章是紀錄 [六角學院 JavaScrip 核心篇](https://www.hexschool.com/courses/js-core.html) 上課筆記內容
接著則繼續說明 `this` 調用方式