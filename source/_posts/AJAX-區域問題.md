---
title: AJAX 區域問題
date: 2020-10-24 21:05:26
categories: JavaScript
tags: 
  - JavaScript
---
若要按鈕觸發 `AJAX` 事件需注意區域問題
<!-- more -->
透過 `XMLHttpRequest` 物件跨瀏覽器撈資料時候會有要觸發按鈕事件的狀況
例如透過按鈕來登入和註冊等事件
可參考這個 [codepen 範例](https://codepen.io/HexSchool_yuko/pen/OJXWwrG)
裡面的 11-16 和 46-51 行放在全域後，第二次按下註冊按鈕或第二次按下登入按鈕會出現下面的錯誤訊息
「Uncaught InvalidStateError: Failed to execute 'send' on 'XMLHttpRequest': The object's state must be OPENED. 」

`xhr.open` 和 `xhr.setRequestHeader` 需在按鈕監聽事件內
如果放在全域其實就已經執行 `AJAX` 行為，因此第一次可以從遠端接到回應
但第二次按下並沒有開啟 `AJAX` 行為，因為第一次全域觸發後就結束，所以就會跳出錯誤訊息
所以每一次的 `AJAX` 行為都要重新建立，也就是要把 `xhr.open` 和 `xhr.setRequestHeader`放在按鈕監聽事件內

