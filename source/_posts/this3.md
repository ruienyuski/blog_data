---
title: this 調用方式 (2)
date: 2020-10-31 17:07:21
categories: JavaScript
tags:
  - JavaScript
---
`this` 調用方式：
「`bind`、`apply`、`call` 方法」內容
<!-- more -->
現在先定義另外一個函式，裡面帶兩個參數，並使用 `console` 來顯示 `this` 
以及「參數 1 」、「參數 2」

「`bind`、`apply`、`call`」這三個方法觀念相近，只是呼叫方式會有點不同 
在此會先介紹這三個方法的呼叫方式，以及他跟 `this` 的關係
這三個都會影響函式的呼叫方式，只不過在運作方面會有些許的不同

首先執行函式會如下圖 `count ()` 接下來帶「參數 1 」、「參數 2」
接下來就可執行這段函式，這種方式是屬於 `simple call` 
因此 `this` 會調用全域的物件，因此 `this` 是全域的 `window` 
接著後面也帶「參數 1 」、「參數 2」
```sh
var num = 10;
function count(a, b) {
  console.log(this);
  console.log(a,b)
}
count(10, 20);
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-10.png)


## Call
接著改用 `call` 的方式來執行這段函式
使用 `count.call` 接著第一個帶入的是 `this` 的物件
把 `item` 給帶進去，接著帶入 10 和 20
可參考 [MDN 文件](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

現在是使用 `call` 方式執行時，第一個參數是 `this` ，後面的參數就會以函式本身的參數依序帶入，所以第 2 行的 `item` 會替代掉原本這個函式的 `this`

```sh
var num = 10
var item = {
  num: 100
}
function count(a, b) {
  console.log(this,a,b)
}
count.call(item,10, 20);
```
可看到下圖目前執行的結果
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-11.png)

原本全域的 `window` 就會被替換成 `item` 這個物件，因此 `num` 就是 100
後面帶上 10 跟 20 的數字

當我們在使用 `call` 要注意，他是立刻執行，跟我們一般呼叫函式是非常接近
只不過他可透過這種方式將 `this` 給替換掉

## apply
`apply` 也是類似的觀念，後方也一樣可帶入 `this`
在此與 `call` 就有不同點
`call` 是將參數依序帶入，`apply` 是將參數以陣列呈現，如下圖結果 
這兩者運用上是非常接近的，只不過在調用參數有點不同
```sh
var num = 10
var item = {
  num: 100
}
function count(a, b) {
  console.log(this,a,b)
}
count.apply(item,[10, 20]);
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-12.png)

## bind

`call` 在調用時，會立刻執行，但是 `bind` 是不會立刻執行這段函式
因此在用 `bind` 時候可先宣告一個變數，並且使用 `bind` 的方法
注意這段 `bind` (下圖圈選處) 是不會立刻執行
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-13.png)

把參數傳入的方式與 `call` 是一樣的
在此把 `item` 與其他內容傳入
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-14.png)

我們在去調用他的時候，他才會執行，使用 `temp()` 
接著他就會立刻去執行這段函式

```sh
var num = 10
var item = {
  num: 100
}
function count(a, b) {
  console.log(this,a,b)
}
var temp = count.bind(item,10, 20);
temp();
```

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-15.png)

下圖這段程式在調用時，他就會自動把 `this` 給替換掉，並且把「10」「20」也一起傳進去

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-16.png)


在執行 `temp()` 時候，這個參數就不用另外帶入，如果在這個階段想要另外帶入參數是否可行，如下圖，把參數另外帶進去是不會有任何變化的

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-17.png)


在使用 `bind` 時候就會強制把參數寫進去
在寫入參數時候也可以使用部分寫入的方式，也就是 `bind` 的地方
第一個參數是寫「10」，但第二個參數先不要帶入

結果如下，第一個參數是「10」，第二個是 `temp()` 執行的第一個參數
也就是他一樣會依序執行

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-18.png)