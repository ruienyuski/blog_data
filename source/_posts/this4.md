---
title: this 調用方式 (3)
date: 2020-10-31 18:05:59
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`this` 調用方式：
「`new`」和「`DOM` 事件處理器」內容
<!-- more -->
## new
[MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)提到 `new 運算子`會產生一個新的空白物件，並且連結原本的建構物件，如下面範例的 `bottle function`
並且把新產生物件的 `this` 綁定到這個函式之上
所以在這建構函式所使用的 `this` 就會綁定到新物件上面

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-19.png)

```sh
function bottle (name,color,size) {
  this.name = name;
  this.color = color;
  this.size = size;
}
var drinkbottle = new bottle('寶特瓶', '藍色','500 ml')
```

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-20.png)

## DOM 事件處理器
這邊主要介紹操作 `DOM` 元素 `this` 會有甚麼不同，主要有兩個部分

### 把方法寫在元素上面
如下圖使用 `console.dir`，顯示結果為單純的物件
就可了解 `this` 會直接綁定在這個元素
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-21.png)

### 監聽器
使用 `querySelectorAll` 把所有的 `BUTTON` 取出來，並且為所有的 `BUTTON` 補上監聽器
監聽的方法是 `click` ，所以點所有的 `BUTTON` 都會觸發事件，觸發的時候會執行 `fn()`
```sh
<button>1</button>
<button>2</button>
<button>3</button>


var fn = function () {
  console.dir(this);
  this.style.color = 'green';
}
var els = document.querySelectorAll('button');
for (var i=0; i<els.length; i++) {
  els[i].addEventListener('click', fn, false);
}
```

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-22.png)

點 `BUTTON` 下方會出現 `DOM 物件` 點開來看就可看到相關的屬性
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-23.png)

第 3 行 `this` 
```sh
this.style.color = 'green';
```
也會受到第 7 行監聽器影響
```sh
els[i].addEventListener('click', fn, false);
```
讓這個 `this` 指向我們所點擊的物件
這也有助於開發上可正確取得我們所點擊的物件