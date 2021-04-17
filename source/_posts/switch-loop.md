---
title: switch (true) 代替 if / else
date: 2020-10-14 10:06:41
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`switch` 常見問題
<!-- more -->
## switch case
![](https://ruienyuski.github.io/photo/hexo_img/20201014_switch/switch-1.png)
上面結果為何不是哪一個例子進入哪一個的舉例式判斷嗎 ? 為何全部列印出來 ?
`switch` 是從哪邊開始執行
也就是從上面案例中 `weekDay = 3` ，是從 `3` 開始，所以依序往下執行，連同 `default` 也執行
所以 `switch` 不只是判斷式，他也有進入點的控制
依照這邊的內容`(weekDay)`，去控制程式碼要從哪邊開始

如果要像是 `if else` 的判斷式，就要加入 `break`;
![](https://ruienyuski.github.io/photo/hexo_img/20201014_switch/switch-2.png)

缺點是：
1.程式碼冗長
2.`switch()` 括號裡的參數 `weekDay` 的狀態要很清楚，才能`handle` 全部

如果 `case` 的內容一樣可以合併
![](https://ruienyuski.github.io/photo/hexo_img/20201014_switch/switch-3.png)

## switch (true) 代替 if / else

因為 `switch` 的 `case` 需要有明確的值
所以如果要判斷是否為某個區間範圍的值
可將 `switch(weight){ }` 裡面的 `weight` 改 `true` ，修改後如下

```sh
var weight = 45;
switch(true){
  case (weight < 40):
  console.log('有點過瘦唷！');
  break;
  case (weight >=40 && weight <=60):
  console.log('很適當！');
  break;
  case (weight >=60 && weight <= 100):
  console.log('過重囉');
  break;
}
```