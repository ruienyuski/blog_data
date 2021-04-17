---
title: for 迴圈
date: 2020-10-12 11:21:26
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`for 迴圈`常見問題及用法
<!-- more -->
## 為何下方全域結果是 3
```sh
for(var i=0; i<3; i++) {
  console.log(i)
}
console.log("外層",i) //3
```
流程如下
```sh
3>0 成立，跑完 {} 內容後，i++ 後，i 變成1
3>1 成立，跑完 {} 內容後，i 變成2
3>2 成立，跑完 {} 內容後，i++，i 變成 3
3>3 不成立，到這 i 還是等於 3
```
所以 當 `i=2` 成立跑完後， 進行 `i++`，會變成 3，這樣 3 才能在下個迴圈判斷是否有成立條件哩


因為當 `i` 跑到 3 時候，3 不小於 3 所以跳出迴圈
但在迴圈中用 `var` 宣告 `i` 會把 `i` 添加到 `window` 底下變成全域變數，
所以 `i` 最後的值是 3 

## for 迴圈 length 的宣告與不宣告變數

```sh
var data = [5, 8, 15];
var len = data.length;
for(var i=0; i<len; i++) {
  console.log(i);
}
```
宣告變數給 `length`，需注意如果迴圈並非取的是陣列內容，而是自定義數字
在迴圈執行階段記憶體還沒釋放，所以還是舊內容
所以在此是建議直接用 `length` 隨時抓取長度，缺點是效能就會明顯不好

```sh
var data = [5, 8, 15];
for(var i=0; i<data.length; i++) {
  console.log(i);
}
```
若直接使用 `data.length` 每跑一次 `for 迴圈`他就還必須偵測陣列長度一次
因為重複計算長度而導致資料量大時，效能就會明顯不好
而使用變數儲存 `data.length` 因直接取得數量，所以相較之下效能會比較好

## for 迴圈的 length 全域和區域宣告
如果在 `for` 迴圈內宣告區域變數的話，他每次只要跑一次 `for 迴圈`裡面的區域變數都會被歸零，也就導致不會累加，所以抓到的內容就只會是最後一筆資料，也就是 140
因此要在外層全域宣告變數才能夠累加結果

```sh
var farms = [
  {
    name: "艾文",
    feild: 6,
    chick: 120
  },
  {
    name: "史考特",
    feild: 10,
    chick: 30
  },
  {
    name: "約翰",
    feild: 6,
    chick: 140
  }
];
// 區域變數
for(var i=0; i<farms.length;i++) {
  var totalchick = 0;
  totalchick += farms[i].chick;
}
console.log(totalchick); //140

// 全域變數
var totalchick = 0;
for(var i=0; i<farms.length;i++) {

  totalchick += farms[i].chick;
}
console.log(totalchick); //290
```

**關於 `+=`**
```sh
totalchick += farms[i].chick;
```
若有內容要加上去，又不影響原本的字串，那就可以用
```sh
totalchick = totalchick + 'abc' 
```
而 `totalchick+='abc'`，就是一種縮寫方式，此種方式等同於
```sh
totalchick = totalchick+ 'abc'
```

## for 迴圈 - i++ 寫法
下面都是同樣內容，不同的表達方式
```sh
    i = i + 1;
    i += 1;
    i++;
```
`i++`，他先回傳數值，所以回傳 1，接著再度呼叫時候再加上 1 
另外也有一種 `++i`
`++i`，他本身加 1，所以回傳 2 ，接著再度呼叫時候再回傳加總後的數值
兩種差別可參考這個[範例](https://codepen.io/HexSchool_yuko/pen/ymeNeV)


## for 迴圈與 break 運用
`break` 和 `if` 以及 `for 迴圈`，這是要看使用狀況而定，在此做個[小範例](https://codepen.io/HexSchool_yuko/pen/OejrLM)

如果單使用 `if`，在此範例只能判斷是否有撈到陣列資料如 JS 第 23 行所顯示一樣
會使用迴圈是因為要從陣列去撈資料出來顯示
 JS 第 28 行，如果只是想撈一筆農夫資料就在迴圈中直接加上 `break`，讓他只跑一次迴圈
 JS 第 37 行，想知道哪些農場的小雞有 100 隻以上，就在迴圈中加入 `if 判斷`讓他跑出相應的資料
 JS 第 48 行，只列出 1 筆有符合有養 100 隻小雞以上的農場
這些都是依照使用情境狀況而去設計的程式
下面這篇文章在敘述使用 `break` 的狀況，裡面有說為何需要 `break`
[https://blog.csdn.net/XXJ19950917/article/details/78310346](https://blog.csdn.net/XXJ19950917/article/details/78310346)
「如果一個循環的終止條件非常複雜，那麼使用 `break` 語句來實現某些條件比用一個循環表達式所有的條件容易得多。」

## splice 刪除和更新 for 迴圈資料的情況

這個 [Codepen 裡面的範例](https://codepen.io/HexSchool_yuko/pen/JjKeBvw)有出現無法刪除的錯誤狀況

因為 `len` 和 `str` 需要放在 `updateList ()` 內

```sh
 var len=listarea.length;
 var str='';
```
也就是刪除資料時， `listarea` 的資料會變更


但 `var len=listarea.length;` 放在全域環境下
所取得的資料長度是一開始的 3 筆資料
因此導致刪除出錯


而 `var str='';` 放在全域則會累加全域的 `listarea` 資料
所以建議這兩行都要放在 `updateList ()` 內

