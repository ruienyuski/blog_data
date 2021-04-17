---
title: event.target
date: 2020-10-30 10:10:51
categories: JavaScript
tags: 
  - JavaScript
  - HTML
---
`event.target` 相關內容整理
<!-- more -->
## event 簡介 
`function` 小括號裡面帶入隨意參數 `a`，若用按鈕觸發這個 `function` 則會取得
`MouseEvent`，如下圖
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-1.png)

`MouseEvent` 點開後可看到各種資訊，像是 `clineX`、`clineY`，如下圖
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-2.png)

## event.target

往下會看到 `target` 的屬性，裡面有 `innerHTML` 和 `innerText`
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-3.png)
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-4.png)

可以將 `function` 裡面用  `a.target.innerHTML = 'BTN'` 來變更按鈕上的文字
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-5.png)

若是在 `button` 裡面增加 `value` 屬性，使用 `event.target.value` 就可以取得其值
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-6.png)

但剛取名的參數建議改用 `e` 或是 `event` 可以較明白這個參數是為了取得 `event` 事件內容

## 不用參數 e 與直接使用 event 差異

若不用參數也是可以直接使用 `event` ，如圖
![](https://ruienyuski.github.io/photo/hexo_img/20201030_event_target/event_target-6.png)

但也會因為如此可讀性就較差，因為明明沒宣告任何值，就突然冒出一個可用的 `event` 值，閱讀直覺相對來說就比較差。

所以基於可讀性來說，建議還是要自訂傳入參數名稱

## event.target 與 this 差異
而另外 `event.target` 也與 `this` 用法也有所差異
>event.target 指的是當下滑鼠事件的目標
this 會指向綁定這個事件的元素