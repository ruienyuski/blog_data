---
title: JS 獲取子節點、父節點和兄弟節點的幾種方式
date: 2020-10-27 10:16:54
categories: JavaScript
tags: 
  - JavaScript
  - HTML
---
整理取得相關節點的方式
<!-- more -->
## 獲取子節點的方式

###  Node.childNodes 獲取子節點
使用 `Node.childNodes` 獲取子節點的時候，`Node.childNodes` 回傳的是子節點的集合，是一個數組的格式。他會把換行和空格或是註解也當成是節點信息。
可參考 Kuro 的文章裡面的 [Node.childNodes](https://ithelp.ithome.com.tw/articles/10191765)
文章中也提到「可以透過 `Node.hasChildNodes()` 來檢查某個 `DOM` 節點是否有子節點」

### Node.firstChild 獲取第一個子節點
`Node.firstChild` 來獲取第一個子元素，但是在有些情況下我們打印的時候會顯示 `undefined`，這是因為 `Node.firstChild` 和 `Node.childNodes` 是一樣的，在瀏覽器解析的時候會把他當換行和空格一起解析，其實獲取的是第一個子節點，只是這個子節點是一個換行或者是一個空格而已。

### ParentNode.firstElementChild 獲取第一個子節點
`ParentNode.firstElementChild` 介面會回傳 `ParentNode` 的第一個子元素，如果該節點沒有子節點則回傳 `null`。這就沒有 `Node.firstChild` 的那種情況，他並不會匹配換行和空格信息。

### Node.lastChild 獲取最後一個子節點
`Node.lastChild` 獲取最後一個子節點的方式其實和 `Node.firstChild` 是類似的。同樣的 `ParentNode.lastElementChild` 和 `ParentNode.firstElementChild` 也是一樣的。他並不會匹配換行和空格信息。

## 獲取父節點的方式

### Node.parentNode 獲取父節點
透過 `Node.parentNode` 可以用來取得父元素，回傳值可能會是一個元素節點 (`Element node`)、根節點 (`Document node`) 或 `DocumentFragment` 節點。

### Node.parentElement
如同 [MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/parentElement)提到：
「回傳當前節點的父元素節點，如果該元素沒有父節點，或者父節點不是一個 `DOM` 元素，則回傳 `null`。」

### HTMLElement.offsetParent 獲取所有父節點
直接能夠獲取到所有父親節點， 這個對應的值是 `body` 下的所有節點信息。
如同 [MDN 文件](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement/offsetParent)提到：
「回傳一個指向最近的 (指包含層級上的最近) 包含該元素的定位元素或者最近的 `table`,`td`,`th`,`body` 元素。當元素的 `style.display` 設置為 `none` 時，`offsetParent` 回傳 `null`。
`offsetParent` 很有用，因為 `offsetTop` 和`offsetLeft` 都是相對於其內邊距邊界的」。

## 獲取兄弟節點的方式

### Node.previousSibling 
透過 `Node.previousSibling` 可以取得同層之間的「前一個」節點，如果 `node` 已經是第一個節點，則回傳 `null`。
類似方法還有 `previousElementSibling` 他們的區別是 `Node.previousSibling` 會匹配字符，包括換行和空格，而不是節點。`previousElementSibling` 則直接匹配節點。

### Node.nextSibling
與 `Node.previousSibling` 類似，透過 `Node.nextSibling` 可以取得同層之間的「下一個」節點，如果 `node` 已經是最後一個節點，則回傳 `null`。
同 `Node.previousSibling` 和 `previousElementSibling`，`Node.nextSibling` 和`nextElementSibling` 也是類似的。
如同 [w3schools](https://www.w3schools.com/jsref/prop_node_nextsibling.asp) 提到：
> The difference between this property and nextElementSibling, is that nextSibling returns the next sibling node as an element node, a text node or a comment node, while nextElementSibling returns the next sibling node as an element node (ignores text and comment nodes).

`Node.nextSibling` 會回傳下一個兄弟節點作為元素節點，文本節點或註釋節點
而 `nextElementSibling` 回傳下一個兄弟節點作為元素節點（忽略文本和註釋節點）。

以上內容除了參考 「MDN 文件」外也參考以下文章
[JS 獲取子節點、父節點和兄弟節點的若干種方式](https://blog.csdn.net/laok_/article/details/75760572)
[重新認識 JavaScript: Day 12 透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)

