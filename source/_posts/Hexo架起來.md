---

title: Hexo 架起來
subtitle: Hexo 輕鬆架
date: 2019-12-26 11:30:19
tags:
    - Hexo
clearReading: true 
autoThumbnailImage: true
metaAlignment: center
comments: false
meta: false
actions: false

---

<!-- more -->


<!-- toc -->

## 此篇尚在測試中，請小心服用

### 用 Mac 架設 Hexo


參考連結：
[hexo安装详细教程](https://dmxiaoshen.com/2018/12/12/hexo%E5%AE%89%E8%A3%85%E8%AF%A6%E7%BB%86/)
[我的第一篇 Hexo 文章：使用 hexo-admin 後台管理工具](https://ed521.github.io/2019/08/hexo-admin/)
[Hexo主题换成Tranquilpeak](https://www.jianshu.com/p/d4294d83b709)
[在Github上使用Hexo搭建博客并配置tranquilpeak主题](https://blog.csdn.net/u010961631/article/details/79279401#5%E4%B8%BB%E9%A2%98config%E7%9A%84%E5%85%B6%E4%BB%96%E9%85%8D%E7%BD%AE)

如果電腦內已裝過 Node.js、Git
可直接輸入下列此指令後，跳到 [5.安裝 Hexo](#installhexo) 的步驟
如果沒有，就乖乖按下面步驟一步一步來

詳情請看：[ Hexo 官方 ](https://hexo.io/zh-tw/docs/index.html)

```
$ npm install -g hexo-cli
```


## 1.安裝 nvm

```
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
```



## 2.編輯 ./zshrc 檔案裡放入下列程式碼
```
$ vim ./zshrc
// 編輯 ./zshrc
```

:::success
```
 export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
  [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
:::


記得存檔後，重開 terminal



## 3.用 nvm 安裝 node

```
$ nvm install node
```

## 4.安裝自動發佈到github的npm套件hexo-deployer-git
```
$ npm install hexo-deployer-git --save
```
:::success
顯示的狀況

```
npm WARN saveError ENOENT: no such file or directory, open '/Users/Shiva/package.json'
npm WARN enoent ENOENT: no such file or directory, open '/Users/Shiva/package.json'
npm WARN Shiva No description
npm WARN Shiva No repository field.
npm WARN Shiva No README data
npm WARN Shiva No license field.

+ hexo-deployer-git@2.1.0
added 71 packages from 371 contributors and audited 89 packages in 2.721s
found 0 vulnerabilities
```
:::

 ## <span id = "installhexo"> 5.安裝 Hexo</span>
 
 ```
 $ npm install -g hexo-cli
 
 $ hexo deploy
 
 $ hexo init 要新建的部落格名稱
 
 $ cd 建置好的部落格名稱
 // 前往創建的部落格資料夾
 $ npm install 
 // 安裝相關套件
 ```
 
 ## 6.將 Hexo 配置到 GitHub 上
 
 在自己的 GitHub 新增一個 Repositories
 名稱需綁定爲 `自己GitHub的帳號.github.io`
 
 在建置好的 Hexo 專案文件夾，找到 `_config.yml` 檔，將文件最下方的 deploy 新增程式碼：
 
 ```
 deploy: 
  type: git
  repository: https://github.com/shiva1010/shiva1010.github.io.git
  branch: master
 
 ```
 冒號一定要空格
 
 上面的 repository 網址，可查看剛剛在 github 建的 repository 所屬 git clone 網址，參考下圖找尋 git clone 位置 
 
 ![](https://i.imgur.com/NbracWY.png)

 ## 7.生成部落格內容檔案
 
 方法兩種，擇一即可
 ```
 方法一 $ hexo g
 方法二 $ hexo generate
 ```
 
 參考指令
 
```
$ hexo s # server 啟動伺服器
$ hexo g # generate 生成靜態頁面
$ hexo d # deploy 將靜態頁面佈署到 github

$ hexo g -d # 生成靜態頁面，立即佈署網站
$ hexo d -g # 在佈署網站前，先生成靜態網頁

$ hexo clean # 清除快取檔案與已產生的靜態頁面
```
 
 
## 8.新增文章

新增一個文章檔案
```
$ hexo new 要新增的Hexo文章檔名   
```

檔案會產生在此路徑下：Hexo專案文件夾/source/_posts


查看檔案內文狀態
```
$ vim 文章檔名.md
```

內容會像下列這樣
```
---
title: test3               # 文章標題
date: 2019-12-20 10:05:41  # 自動產生日期與時間
tags:                      # 自定義標籤
---

內文

```

## 9.啓動 Hexo Server ，本地測試

分簡寫跟全寫版，擇一即可
```
$ hexo s
$ hexo server
```

## 10.測試 OK ，佈署上線
```
$ hexo g -d
```
