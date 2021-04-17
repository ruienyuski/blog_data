---
title: 按鈕 type 設定
date: 2020-10-25 11:10:05
categories: JavaScript
tags: 
  - JavaScript
  - HTML
---
紀錄按鈕的 `type` 會出現的狀況
<!-- more -->

`type = "submit"` 類型會被視為提交按鈕，點選的話就透過 `action` 把表單提交到伺服器。
在 `HTML` 裡面的 `form action` 如果有寫上 `index.html`
是指提交資料送出到 `index.html` 如果沒有這個網頁就可能會出錯
一般來說都會讓 `form action` 空著，有需求才寫送出的位址。
`type = "button"` 表示這是按鈕，並不會將表單提交出去到伺服器。
或者是加上 `preventDefault()` 也可以取消預設行為

以下為參考文件
[W3school 對 form action 的解釋](http://www.w3school.com.cn/tags/att_form_action.asp)

[MDN 解釋 type 類型 submit](https://developer.mozilla.org/zh-TW/docs/Web/HTML/Element/input/submit)