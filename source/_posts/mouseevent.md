---
title: mouse 滑過事件差異
date: 2020-10-15 10:34:54
categories: JavaScript
tags:
  - JavaScript
  - jQuery
  - HTML
---
整理一些 `mouse` 滑過事件差異
<!-- more -->
## 事件解釋
- `mouseover` : 當滑鼠移動到被選元素和被選元素的子元素時，`mouseover` 事件就會被觸發。
[mouseover MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/mouseover_event)

- `mousemove` : 當滑鼠移動到被選元素內後，`mousemove` 事件被觸發。
[mousemove MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/mousemove_event)

- `mouseenter`: 當滑鼠移動到元素上時就會觸發 `mouseenter` 事件，類似 `mouseover`，它們兩者之間的差別是 `mouseenter` 不會冒泡（bubble），也就是說當游標從它的子層物理空間移到它的物理空間上時不會觸發
[mouseenter MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/mouseenter_event)


## 相關討論文章
- `jQuery` 的 `mouseover()` 與  `hover()` 差異可參考 [stackoverflow 討論](https://stackoverflow.com/questions/17589420/when-to-choose-mouseover-and-hover-function)
 + `mouseover()`：將事件綁定在「`mouseover`」 `JavaScript`事件，或在元素上觸發該事件。
 + `hover()`：將一個或兩個處理程序綁定到匹配的元素，以在滑鼠游標進入和離開元素時執行。



- `CSS hover` 與 `JavaScript mouseover` 討論可參考 [stackoverflow 討論](https://stackoverflow.com/questions/608788/css-hover-vs-javascript-mouseover)
 + 討論中有人提到 CSS 比較好維護，也有提到 `CSS hover` 在 `IE6` 雖可支援，但因為後來的 `IE7` 對 `CSS2` 的支持程度約為`50%` 所以不支援 `div：hover`


- `javascript` 中 `mouseenter` 與 `mouseover` 差異也可看下面的文章
 + [javascript 中 mouseenter 與 mouseover 的異同](https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/236517/)
 裡面也提供[範例](https://qianlongo.github.io/zepto-analysis/example/event/mouseEnter-mouseOver.html)來顯示其差異
 
 + [Difference between mouseover, mouseenter and mousemove events in JavaScript](https://www.geeksforgeeks.org/difference-between-mouseover-mouseenter-and-mousemove-events-in-javascript/)
 裡面提供 `mouseover`、`mouseenter`、`mousemove` 簡單說明
