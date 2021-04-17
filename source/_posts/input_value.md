---
title: input.value 取值狀況
date: 2020-09-11 16:28:32
categories: JavaScript
tags: 
  - JavaScript
  - HTML
---
`input value` 會有取值的狀況，如下文所示：
<!-- more -->
## 全域與區域設定 input value 差異
全域設定 `input.value` 時，如果 `HTML` 沒有設 `value` 網頁載入時候會是空值
可參考這個[範例](https://codepen.io/HexSchool_yuko/pen/QXXPvm)

## 清空 input.value 
```sh
function addTodo() {
var txt = document.querySelector('.text').value;
txt = '';
}
```
因為 `txt` 是儲存 `input` 元素的值
換句話說是新增記憶體 ( 變數 `txt`) 來存放 `document.querySelector('.text').value`
並非取得當下的 `input` 元素的值
所以會建議直接使用 `txt.value`
因此改為 `var txt = document.querySelector('.text');`
並用 `txt.value` 就能清空當下的 `input.value`

```sh
function addTodo() {
var txt = document.querySelector('.text');
txt.value = '';
}
```

## 限制 input 輸入長度
限制字數可使用 `maxlength` 若 `type="number"` 是無法使用這個語法，需改為 `type="tel"` 
可參考這篇[文章](https://www.itread01.com/articles/1498672640.html)

## input 欄位如不輸入內容會是 "" ，如轉為數字則會是 NaN
可參考 [stackoverflow 討論](https://stackoverflow.com/a/44264395)
裡面提到沒輸入 `value` 就會是 `""` 
但該欄位如果有轉型為 `Number`
則會得到 `NaN`

