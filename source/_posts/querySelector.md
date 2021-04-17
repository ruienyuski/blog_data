---
title: querySelector
date: 2020-10-20 10:12:59
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`querySelector` 和 `querySelectorAll` 選取元素用法介紹
<!-- more -->
## querySelector 選取單一元素
```sh
var el = document.querySelector('.box');
var el_id = document.querySelector('#boxid');
```

括號內接 `class` 或是 `id` 
`class` 為 `.`
`id` 為 `#`
與 `CSS` 寫法一樣

## querySelectorAll - 可重複選取多個元素
下方的 `.box` 若用 `querySelector` 則只會選到第一個 `.box`
```sh
<div class="box"></div>
<div class="box"></div>

var el = document.querySelector('.box');
```
所以需改用 `querySelectorAll` 才能選到所有的 `.box` 

```sh
<div class="box"></div>
<div class="box"></div>

var el = document.querySelectorAll('.box');
```
若要讓 `.box` 加上內容可跑 `for 迴圈`
```sh
var el = document.querySelectorAll('.box');
for(var i = 0; i < el.length; i++) {
  el[i].textContent = '項目'+ i;
};
```
這邊有個地方要注意 `querySelectAll` 取出的值為 `NodeList` 也是類陣列
也就是代表選取到所有符合條件的元素，是一個集點的集合 `NodeList`
可參考 [MDN 文件](https://developer.mozilla.org/zh-TW/docs/Web/API/NodeList)
因此他無法使用陣列型別的 `method` ，但仍可使用索引存取內容
類陣列轉為陣列常見方式可透過「展開」、「`Array.from`」
另外 `el.length` 可以看成是被選取到的元素數量
所以 `for 迴圈` 也是可以使用的

## querySelector & getElementByXX 的差別

`querySelector` 是屬於靜態結果， 而 `getElementByXX` 是屬於動態結果
如同這篇[鐵人賽文章範例](https://ithelp.ithome.com.tw/articles/10230686?sc=rss.qu)
```sh
<ul id="myul">
    <li>li 1</li>
    <li>li 2</li>
    <li>li 3</li>
</ul>

// 使用 getElementBy 系列取得 li 清單
var ulbyid = document.getElementById('myul');
var libytag = ulbyid.getElementsByTagName('li');

// 使用 querySelector 取得 li 清單
var ulqs = document.querySelector('ul');
var ulqsa = ulqs.querySelectorAll('li');

// 輸出取得的清單長度都是 3
console.log(libytag.length); // 3
console.log(ulqsa.length); // 3

// 在 ulbyid 加入新的 li 元素
ulbyid.appendChild(document.createElement('li'));

// 再次輸出清單長度
console.log(libytag.length); // 4
console.log(ulqsa.length); // 3

// 在 ulqsa 加入新的 li 元素
ulbyid.appendChild(document.createElement('li'));

// 再次輸出清單長度
console.log(libytag.length); // 5
console.log(ulqsa.length); // 3

```
文章中提到
「`getElementBy...` 系列都能抓到當前所有項目(有點像自動更新的功能), 而 `querySelector` 在取得後不管加了多少新元素, 都只有取得當下的清單內容而已」