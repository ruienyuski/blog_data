---
title: onclick 和 addEventListener 綁定事件
date: 2020-10-21 10:12:57
categories: JavaScript
tags:
  - JavaScript
---
綁定事件 `onclick` 和 `addEventListener` 的常見問題
<!-- more -->
## 括號問題

### onclick
`onclick` 在 `HTML 標籤`使用 `onclick` 指令時，請加上括號
在 `JS` 上要使用 `onclick` 時，不需要加上括號，因為會自動執行該 `function`，可以想像他會在該函式自動幫你加上 `()`

### addEventListenter 中間函數不能用 () 帶參數狀況
在這個[範例](https://codepen.io/HexSchool_yuko/pen/yLNPoKM)
`addEventListener` 第 2 行的 `addArea`
在沒有點按鈕的狀況下，就會立刻執行 `addArea` 內容
如果要讓 `addArea()` 在按鈕觸發時候帶參數
可參考 [MDN 文件中的「匿名函數的事件監聽」](https://developer.mozilla.org/zh-TW/docs/Web/API/EventTarget/addEventListener)
因此 `addArea` 可改寫如下，也就是範例第 9 行內容
以上可參考[stackoverflow 討論](https://stackoverflow.com/a/16588082)

```sh
    btn.addEventListener('click', function() {
      addArea("苓雅區")
    }, false)
```

## 綁定事件語法差異
`onclick` 只能綁定單一事件，如同這個[範例](https://codepen.io/HexSchool_yuko/pen/gOMwjzV) JS 欄位 1-7 行，雖然按鈕綁定兩個事件，但按鈕只會觸發最後一個事件

`addEventListener`則可綁定多個事件，在範例 JS 欄位 9-15 行裡面，兩個事件都有被綁定

## addEventListener 冒泡和捕捉事件
針對 `addEventListenter` 後方的 `false` 做說明，可參考這個[範例](https://codepen.io/HexSchool_yuko/pen/ZEWpmzw)

```sh
false (事件氣泡 - event Bubbling) - 從指定元素往外找
true (事件捕捉 - event capturing) - 從最外面找到指定元素
```

所以選擇 `false` 會比較合乎邏輯，點擊最近元素觸發事件
可是有時會希望由外往內，所以會需要 `true`
不寫的話預設為 `false`

也可參考這篇 [DOM 的事件傳遞機制：捕獲與冒泡](https://blog.techbridge.cc/2017/07/15/javascript-event-propagation/)
文中敘述也有提到 `addEventListener` 的第三個參數解釋
「其實，一樣是用大家所熟悉的 `addEventListener`，只是這函數其實有第三個參數，
`true` 代表把這個 `listener` 添加到捕獲階段，`false` 或是沒有傳就代表把這個 `listener` 添加到冒泡階段。」