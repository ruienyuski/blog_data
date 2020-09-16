---
title: innerhtml
date: 2020-09-12 15:51:09
categories: JavaScript
tags:
  - JavaScript
  - HTML
---
`innerHTML` 在處理迴圈或是字串會遇到常見的問題，如下文所示：
<!-- more -->
## innerHTML 組字串的引號問題

如果外層是單引號，裡層包起來就要是雙引號，因為如果同樣是單引號，他不知道結束點在哪，會以為是在圈選處結束，如下圖，而出現紅色底線
![](https://ruienyuski.github.io/photo/hexo_img/20200912_innerhtml/innerhtml-1.png)

更改如下
![](https://ruienyuski.github.io/photo/hexo_img/20200912_innerhtml/innerhtml-2.png)

innerHTML 可以累加
![](https://ruienyuski.github.io/photo/hexo_img/20200912_innerhtml/innerhtml-3.png)

結果如下，會出現兩次
![](https://ruienyuski.github.io/photo/hexo_img/20200912_innerhtml/innerhtml-4.png)

## innerHTML 與 for 運用
`list.innerHTML` 的位置是否可以放在 `for 迴圈`裡面呢？
```sh
    function updateList(e){
        var selected=e.target.value;
        var str="";
        for(var i=0;i<country.length;i++){
             if(selected===country[i].place){
                 str+="<li>農夫名字是："+country[i].farmer+"</li>";
                 list.innerHTML=str;
             };
         };
     };
```
邏輯上雖是可行，但是程式執行時，會屢次向網頁進行渲染，也就是不斷的重複寫入
所以比較好的方式是在放在 `for 迴圈`後面 (如下) ，當字串累加後，後面再執行 `innerHTML`
```sh
    function updateList(e){
        var selected=e.target.value;
        var str="";
        for(var i=0;i<country.length;i++){
             if(selected===country[i].place){
                 str+="<li>農夫名字是："+country[i].farmer+"</li>";
             };
         };
        list.innerHTML=str;
     };
```
## += 說明用法
當在寫 `var str='hi'` 時，裡面就被賦予字串，
而若有內容需要加上去，又不能影響原本的字串，
那就可以用

```sh
str( 原變數 ) = ( 重新賦予值 )  str( 原變數內容 )+ 'Sue' 字串
str = str +  'Sue' 
```
而 `str+='Sue'`，就是一種縮寫方式，此種等同於 `str = str+ 'Sue'`
如果不習慣這樣的縮寫，可直接用 `str = str + 'Sue'` 這種寫法
