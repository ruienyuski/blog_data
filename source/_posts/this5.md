---
title:  this 調用方式 (4) 和 Vue.js 的 this 
date: 2020-10-31 20:24:56
categories: JavaScript
tags:
  - JavaScript
  - HTML
  - Vue
---
`this` 調用方式：「箭頭函式 (`ES6`)」內容
以及 `Vue.js` 的 `this` 指向
<!-- more -->
## 箭頭函式 (ES6)
箭頭函式有以下幾個特點：

### 箭頭函式與傳統函式最大不同處是在 this 綁定是不一樣的

1.  範例 1
「箭頭函式」是沒有自己的 `this`，如下方範例

```sh
var data = {
  item:'杯子',
  num: () => {
    console.log(this)
  }
}
data.num();
```
`num` 用「箭頭函式」則會指向 `Window` 
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-28.png)

改用「傳統函式」就可以正確指向 `data` 物件
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-29.png)

2.  範例 2
`setTimeout` 是屬於簡易呼叫，簡易呼叫的情況下， `this` 就會指向 `window` 
若用「傳統函式」則會指向 `Window` 

```sh
var data = {
  item:'杯子',
  num: function() {
    setTimeout(function(){
      console.log(this)
    },1000)
  }
}
data.num();
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-30.png)

但若改用「箭頭函式」則會指向 `data` 物件

```sh
var data = {
  item:'杯子',
  num: function() {
    setTimeout(() =>{
      console.log(this)
    },1000)
  }
}
data.num();
```
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-31.png)


> 所以當看到「箭頭函式」裡面有 `this` 時候，可以先當「箭頭函式」不存在，這個 `this` 就用外層他作用域的 `this`


### this 不同，導致 DOM 的 this 也會指向不同位置

這邊要注意，因為箭頭函式的 `this` 指向位置是不一樣的，所以使用 `this` 要注意使用的是「傳統函式」還是「箭頭函式」，下方範例是透過 `click` 方式把 `DOM` 位置給取出

```sh
<p>項目 1</p>

var el = document.querySelector('p');
el.addEventListener('click', function(){
  console.log(this)
},false)
```

點擊畫面的文字內容後，`console` 就顯示點擊的位置
也就是 `console.log(this)` 指的是 `el` 這個 `DOM 元素`

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-32.png)


改為「箭頭函式」，存檔後一樣點文字，會發現他指向 `Window`
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-33.png)

因為「箭頭函式」沒有屬於他自己的 `this` 所以改為「箭頭函式」，他的 `this` 就會指向全域
也因為「箭頭函式」沒有自己的 `this` 當然也無法透過 `call`、`apply`、`bind` 的方式重新給予 `this`
此為「箭頭函式」指向是不一樣的，所以也無法作為建構函式使用

## Vue.js this 的指向

如同六角學院講師 卡斯伯所寫的[文章](https://wcc723.github.io/javascript/2019/03/18/JS-THIS/)提到：
> `Vue` 實際運作時，元件內的物件、函式等等均會被向上拉，`methods`, `computed` 等等均不會存在，所以並非以原始碼而是以實際運行的狀態為主
`methods` 內的 `function` 及 `data` 內的內容均在元件物件頂層。
元件下的函式的 `this` 就會直接指向該元件，所以 `methods` 內的 `function` 的 `this` 自然就能夠使用元件內的 `text` 資料。

但若是 `method` 或是 `computed` 裡面的 `function` 有使用其他 `function` 需注意 `this` 指向

```sh
<div id="app">
  <div v-for=" item in filterArray"> {{item.name}}</div>
</div>

var app = new Vue({
  el: '#app',
  data: {
    arrayData: [
      {
        name: '小明',
        age: 16
      },
      {
        name: '漂亮阿姨',
        age: 24
      },
      {
        name: '杰倫',
        age: 20
      }
    ],
    filterText: '杰倫',
  },
  computed: {
    filterArray: function (){
      # var vm = this;
      return this.arrayData.filter(function(item){
        return item.name.match(this.filterText)
      })
    }
  },
});
```
結果如圖
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-24.png)

這是因為原本的 `this` 指的是 `Vue` 這個物件，在經過 `filter` 後，此時的 `this` 已
經不是一開始的 `this`，而是 `Window` 

如下圖在 `filter` 用 `console.log(this)` 就可看到指向 `Window`

![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-26.png)

若改用 `console.log(vm)` 則指向 `Vue`
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-27.png)

而且也能正確顯示資料
![](https://ruienyuski.github.io/photo/hexo_img/20201031_this/this-25.png)