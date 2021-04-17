---
title: VueCli 上傳到 GitHub 相關流程
date: 2020-11-07 15:31:48
categories: GitHub
tags: 
  - Vue
  - GitHub
---
這邊整理 `VueCli` 原始檔案上傳到 `GitHub` 流程
<!-- more -->
## GitHub 新增 Repository
要把網站上傳到 `GitHub` 除了要在電腦安裝 `Git` 和註冊 `GitHub` 外
( 安裝 `Git` 可參考[「六角學院線上問答會 Git 安裝流程」](https://youtu.be/VufCg58gysE))
也需要新增數據庫 (`repository`)，如下圖設定
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-1.png)
這邊只要設定數據庫名稱 (`Repository name`)，也就是上圖 Repository name
綠色打勾代表可以用這個名稱來建立 `repository`，接著按下綠色按鈕進行下一步
接著會跑出 `Quick setup` 畫面，這邊就需要紀錄 `.git` 的連結，方便我們把資料上傳
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-2.png)

## 本地端設定要傳送到 GitHub 的資料
這邊要把 `VueCli 2` 上傳到 `GitHub` 需要先在建立本地數據庫
也就是 `git init` 
接著把全部檔案新增索引，就使用 `git add .`
```sh
git init
git add .
```
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-3.png)
因為 `Git` 是版本控制，所以需要有文字說明這次更新內容，因此需要執行
```sh
git commit -m '編輯記錄'
```
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-4.png)
然後上傳到遠端數據庫，先添加一個遠端數據庫 `git remote add`
之後才用 `git push`
```sh
git remote add <name> <url>
git push <name> master
// name 為數據庫名稱
// url 為 .git 連結位址
```
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-5.png)

上傳到 `GitHub` 後再重新整理網頁，就看到資料已經都上傳
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-6.png)