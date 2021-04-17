---
title: VueCli 編譯後的網站上傳到 GitHub gh-pages 分支
date: 2020-11-07 16:31:20
categories: GitHub
tags: 
  - Vue
  - GitHub
---
這邊整理 `VueCli` 編譯後的檔案上傳到 `GitHub` 流程
<!-- more -->
## 編譯前的設定
以 `VueCli 2` 來說需設定 `config/index.js` 裡面的 `build` 中的 `assetsPublicPath`
改其值為 `/repository 名稱/`
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-7.png)

若為 `VueCli 3` ( 含 ) 以上的版本則在專案根目錄新增 `vue.config.js` 做設定
在 [Vue 官方文件](https://cli.vuejs.org/zh/config/#publicpath)有說明
```sh
module.exports = {
  publicPath: process.env.NODE_ENV === 'production'
    ? '/repository 名稱/'
    : '/'
}
```
如下圖
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-10.png)

設定好後才執行 `npm run build` 編譯網站
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-8.png)

執行後會出現 `dist` 資料夾
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-9.png)

## 進入 dist 資料夾和建立分支
執行 `cd dist` 進入到 `dist` 資料夾，與之前一樣建立數據庫和 `commit`
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-11.png)

接著設置遠端分支使用下面的指令
```sh
git push '遠端 repository' master:gh-pages
```
如下圖
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-12.png)

上傳到 `GitHub` 後再重新整理網頁，就看到已經有 `gh-pages` 分支
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-13.png)

點選進去後可看到 `dist` 資料夾內的檔案，點右上角的 `Settings`，可進入設定畫面
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-14.png)

網頁移到下方可看到 `GitHub pages` 內容已經幫我們設定網頁畫面預覽的 `Source` 為 `gh-pages` 分支
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-15.png)

打開連結可看到網頁內容
![](https://ruienyuski.github.io/photo/hexo_img/20201107_github/vuecli-16.png)