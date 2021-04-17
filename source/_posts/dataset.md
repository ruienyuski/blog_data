---
title: dataset 
date: 2020-10-23 09:34:05
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`HTML` 在設定 `data-*` 會遇到的情況如下
<!-- more -->
以這個[刪除 todo 項目範例](https://codepen.io/HexSchool_yuko/pen/wvWoVJG)來說
在 JS 第 10 行的 `data-num` 中有設定刪除
```sh
<a href="#" data-num='+ i +'><span>刪除<span></a>
```
但是卻發生只會刪除第一項的錯誤狀況
這是因為他點的是 `<a>` 裡面的 `<span>`，也就是 `list.addEventListener` 裡面的 `console` 顯示 `SPAN`
在 `<span>` 上並沒有設定 `data-num` 因此會出錯
要避免這個錯誤就需要把 `data-num='+ i +'` 放到 `<span>` 
或者是 `<a>` 和 `<span>` 一起加上 `data-num` 就不會出錯

另外也有人會在 `<a>` 加上 `/` 如第 20 行的
```sh
<a href="#" data-num='+ i +'/>刪除</a>
```
出錯是因為斜線放到後面是代表該標籤自帶結尾標籤
`<a>` 的結束標籤應是後方的 </a> ，加上斜線會導致取值錯誤，只會刪除第一筆資料

而且 `dataset`也可用 `[]`來讀取數值
```sh
data.splice(e.target.dataset['num'], 1);
```
如同 [MDN 文件](https://developer.mozilla.org/zh-TW/docs/Web/API/HTMLElement/dataset)裡面的「存取數值」」提到
「 資料屬性也可以經由物件屬性 `[]` 語法的方式設定或讀取，如 `element.dataset[keyname]`。」