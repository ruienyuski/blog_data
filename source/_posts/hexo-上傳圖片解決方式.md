---
title: hexo 上傳圖片解決方式
date: 2020-09-12 17:12:00
categories: hexo
tags:
  - hexo
---
這邊紀錄 `hexo 需要附上圖片的處理方式
<!-- more -->
## 本地上傳圖片
在 `hexo` 根目錄的 `_config.yml` 裡面有個
```sh
post_asset_folder: false
```
改設定值為 true
```sh
post_asset_folder: true
```
可使用 `hexo cl` 清除之前建立的靜態檔案和 `hexo s`重啟網站
接著執行 `hexo new 新文章名稱` 建立新文章
`source/_post` 裡面就會出現除了新文章外還有新文章名稱的資料夾
可將圖片放在該資料夾中
並依照[官網文件](https://hexo.io/zh-cn/docs/asset-folders.html)用標籤方式來設定

```sh
{% asset_img slug 圖片名稱.png %}
```
只改上面程式碼內的 `圖片名稱.png` 即可
最後執行 `hexo cl` 清除之前建立的靜態檔案和 `hexo s` 重啟網站就可看到圖片

## 利用 GitHub 來當圖床，並引用其網址
首先可先參考這個 [youtube 影片](https://youtu.be/0UKyACaKMC4) 新增 `GitHub` 和上傳圖片到 `GitHub`

接著在文章內使用 `Markdown` 語法
```sh
![](https://帳號名稱.github.io/repo 名稱/xxx.png)
```