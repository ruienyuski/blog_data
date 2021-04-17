---
title: localStorage
date: 2020-10-23 10:37:31
categories: JavaScript
tags:
  - JavaScript
---
`localStorage` 若用「.」取值會出現以下狀況
<!-- more -->
在 [stackoverflow 討論](https://stackoverflow.com/a/24904863)有提到若是 `localStorage` 用「.」來儲存一個屬性叫做 `length` 名稱
也就是與查詢長度是一樣名稱，導致他以為是要設定 `localStorage` 的長度為 `foo`
造成語法錯誤，所以用 `console.log(localStorage.length)` 會顯示長度為 `0`
```sh
localStorage.length = "foo";
console.log(localStorage.length) // => 0
```
因此若要取得 `localStorage` 的值建議還是用 `getItem` 語法