---
title: createElement
date: 2020-09-16 17:18:31
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`createElement` 與 `innerHTML` 都是插入 `HTML` 標籤的兩種方法
這邊整理 `createElement` 內容
<!-- more -->
## createElement 寫法
先使用 `createElement` 建立元素，以下將內容放到 [Codepen](https://codepen.io/HexSchool_yuko/pen/poyZxEX)
```sh
var li = document.createElement('li');
li.textContent = 'item 1';
```
再使用 `appendChild` 用新增子節點的方式去新增
```sh
document.querySelector('ul').appendChild(li);
```
以上可參考 JS 第 1-3 行註解內容
若要大量增加，可使用 `for 迴圈`，可參考 JS 第 5-24 行內容
```sh
var data = [
  {
    student: 'joe',
    age:10,
  },
  {
    student: 'bill',
    age:9,
  },
  {
    student: 'kevin',
    age:11,
  },    
];
var len = data.length;
for(var i=0; i<len; i++) {
  var li = document.createElement('li');
  li.textContent = data[i].student;
  document.querySelector('ul').appendChild(li);
}
```
## appendChild 放 for 迴圈裡面
`appendChild` 放 `for 迴圈` 裡面是每個產生一個元素，就將該元素寫入到對應位置。
但放外面的話，他就只會放最後一筆資料到裡頭。


## 迴圈內宣告 createElement
迴圈內宣告 `createElement` 代表每跑一次迴圈都會宣告並產生一個新的 `li` 元素
把 `document.createElement("li")` 放在迴圈外
他會導致每次迴圈在執行，都會替換「同一個」之前宣告好的 `li` 文字內容
也就是每次新增都是取代前一個
所以要能產生多筆內容，建議把他放在迴圈內

## appendChild 放在迴圈內
`appendChild` 它的特性是會在後面做累加動作
放在迴圈外，他就只會放最後一筆資料到裡頭