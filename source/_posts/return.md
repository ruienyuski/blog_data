---
title: return
date: 2020-10-20 10:51:58
categories: JavaScript
tags:
  - JavaScript
---
整理 `function` 的 `return` 觀念和用法
<!-- more -->
關於 `function` 的 `return` 比較好理解的方式是
`function` 就是一個計算機，當要執行 `function` 時，就表示要拿起計算機開始算了，
此時按下 `100 * 10`，希望可以結束運算並回傳資料時，就會按計算機的「`=`」符號來顯示運算結果，
進而得到想知道的計算結果。
而 `return` 就是計算機的「`=`」，按下去就會顯示運算結果了
因此 `return` 之後是不會再執行後面的程式了，直接結束，相當於 `break`
所以除了回傳值，還可以當中斷點

而且其實 `function` 都要回傳值，若是沒有用 `return` 回傳，他預設會顯示 `undefined`
可參考 `stackoverflow` 的 [「console.log(myFunction()) returns undefined」討論內容](https://stackoverflow.com/questions/48362507/console-logmyfunction-returns-undefined)

關於 `return` 用法可參考[這篇文章](https://blog.csdn.net/yulei_qq/article/details/45317579)
他下方總結就有說明
`retrun true`： 返回正確的處理結果。
`return false`：返回錯誤的處理結果、終止處理、阻止提交表單、阻止執行默認的行為。
`return`：把控制權返回給頁面。