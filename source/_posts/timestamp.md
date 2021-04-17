---
title: UNIX timestamp 整理
date: 2020-10-28 10:05:13
categories: JavaScript
tags: 
  - JavaScript
  - HTML
---
整理日期轉換的方式
<!-- more -->
## 取得日期時間
在 `JavaScript` 若要取得時間可用 `new Date()`
而若要瞭解完整時間可輸入下列程式碼
```sh
var time = new Date()
time.getFullYear()
time.getMonth()               //    回傳數值，取得該日的月份，月份 0 表示 1 月！
time.getDate()                //    回傳數值，取得該日為該月份的幾號
time.getDay()                 //    回傳數值，取得該日為星期幾
time.getSeconds()             //    回傳數值，取得日期物件的秒資訊
time.getMinutes()             //    回傳數值，取得日期物件的分資訊分
time.getHours()               //    回傳數值，取得日期物件的小時資訊
```
## UNIX timestamp 簡介
但因為全球因為有時區問題，所以需要共通自訂時間，稱為 `UNIX 時間`
從 1970 年 1 月 1 日 0 時 0 分 0 秒起至現在的總秒數，不考慮閏秒。 
下面的語法是取得總毫秒，但一般的 `UNIX timestamp` 通常是以秒數為單位
可參考[stackoverflow 討論](https://stackoverflow.com/a/4676213)
```sh
Date.now() //  回傳當前的 timestamp（毫秒）
```
或是
```sh
var time = new Date()
time.getTime()
```

## 取得某個時間
如果想知道某年月日時間資訊可輸入
```sh
new Date('年/月/日')
time.getTime()
```
或是
```sh
new Date('年-月-日') //舊瀏覽器可能不支援
```
得到結果如下
```sh
new Date('2020/1/1')
Wed Jan 01 2020 00:00:00 GMT+0800 (台北標準時間)
```

## UNIX timestamp 轉換當下時間
也可以把 `UNIX timestamp` 秒數轉換當下時間，方法如下

```sh
new Date (UNIX 秒數)
```
結果如下
```sh
new Date(1516008367167) //傳入毫秒
// Mon Jan 15 2018 17:26:07 GMT+0800 ( 台北標準時間 )
```

## UNIX timestamp 轉換
### 轉換日期
但因為一般 `timestamp` 取得的是秒數，但在 `JavaScript` 中要帶入的是毫秒
所以要 `new Date(timestamp * 1000)`：
```sh
// 1513598707 為 timestamp
new Date(1513598707*1000)          // 因為一般 timestamp 取得的是秒數，但要帶入的是毫秒，所以要乘 1000

// 或者
var date = new Date(timestamp * 1000)
dataValues = [
   date.getFullYear(),
   date.getMonth()+1,
   date.getDate(),
   date.getHours(),
   date.getMinutes(),
   date.getSeconds(),
];
console.log(dataValues);
```
### 轉換 timestamp
同樣的要取得 `timestamp` ，也就是總秒數則除以 1000
```sh
var dateTime = Date.now();
var timestamp = Math.floor(dateTime / 1000);
```
或是
```sh
var dateTime = new Date().getTime();
var timestamp = Math.floor(dateTime / 1000);
```
## 轉換成常見日期格式
若要把之前取得的日期，如下
```sh
Mon Dec 18 2017 20:05:07 GMT+0800 (台北標準時間)
```
改為 2017-12-18 這樣的格式
就要改為 ISO 8601 標準時間格式
可以使用 `Date.prototype.toISOString()`
```sh
var a = new Date('Mon Dec 18 2017 20:05:07 GMT+0800 (台北標準時間)')
a.toISOString()
```
他會回傳下方內容
```sh
2017-12-18T12:05:07.000Z
```
接著可用 `split()` 來分割日期和時間內容
```sh
a.toISOString().split('T')
// 回傳陣列結果 ["2017-12-18", "12:05:07.000Z"]
```
若只要取得日期就可用
```sh
a.toISOString().split('T')[0]
//  ["2017-12-18"]
```
以上可參考 [Codepen 範例](https://codepen.io/HexSchool_yuko/pen/VwwvZzG)
上述內容也參考下方文章
[JavaScript Date Time Method 日期時間](https://pjchender.github.io/2017/12/27/js-javascript-date-time-method-%E6%97%A5%E6%9C%9F%E6%99%82%E9%96%93/)
[在 JavaScript 簡單取得 unix timestamp](https://www.jstips.co/zh_tw/javascript/extract-unix-timestamp-easily/)


