---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: GitHubPage
tags:  GitHub Jekyll Pages 網站 HTML 部落格 博客 教程 教學 懶人包
date:  2017-05-11
last_modified_at: 2018-07-17
title: "Jekyll及GitHub教學1》快速20分鐘建立免費部落格"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="http://jekyllrb.com/img/octojekyll.png" alt="Jekyll Logo" width="250" itemprop="image">
</center><br>
最近用Jekyll在Github架本部落格Blog, 本篇教學用Jekyll + Github Pages架設部落格Blog的方法教程,及簡介Jekyll(可參考Jekyll官網教學),下篇教學2再講Jekyll Theme及Jekyll Plugin. 實際裝完Jekyll部落格Blog後,發現HTML跟CSS都可以依照喜好更改,而且不用受限部落格Blog平台,真的是太方便了!!!我決定把它拿來存放以前存下來的各種Code,也希望開始有個部落格Blog筆記給未來的自己,我的部落格Blog就這樣誕生了!!.<br>
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2017/05/11/how-to-make-blog-on-github/" id="link" target="_blank">
	https://hungchicheng.github.io/2017/05/11/how-to-make-blog-on-github/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 各部落格平台
1. 痞客邦
* 廣告一大堆
* 還有VIP制
* 中國看不到(我比例重的是 Cocos2d-x 的文章, 這樣好像少了什麼...)
2. Blogger
* google 的 blog 平台, 看起來相當方便
* 中國一樣看不到...
3. WordPress
* 等於自己架站
* 要考慮到網站託管問題...

=>最後就看到了Jekyll + GitHub Page, 這根本就是我需要的, 就來嘗試看看了, 先說一下個人背景[About Me](/about)頁面裡面也有, 資工畢業程式底, 做過 iOS/ 遊戲開發, GitHub也是初次使用, 前端開發經驗0, HTML 忘光了, css/JS/Markdown也邊寫邊學, 都輕鬆建起來了哦!!<br>
<br>
個人認為...沒寫過程式, 但有興趣學一些的人也可以加入啦= =+ <br>
其他樣式主題(Theme)等等套用現成的就可以了

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 第一步- GitHub Page
[GitHub Page](https://pages.github.com/) 可以幫你或你的開發專案提供網頁, 直接由它來幫你免費的Host託管以及發佈, 
只要將你的網頁專案檔存在 [GitHub](https://github.com/) 的中, 
不需自己建伺服器, 不用特別的的設定, 就可以製作個人的網頁, 更可以綁定自己的網域名城, 
不需要再費心思處理各種麻煩事了.<br>
<br>
<img src="http://jekyllrb.com/img/octojekyll.png" alt="Jekyll Logo" width="300"><br>
### 安裝方法<br>
1. 申請 GitHub賬號 <https://github.com/> (賬號username就會是你未來的網址)
2. 下載安裝 GitHub Desktop <https://desktop.github.com/> 桌面版本 並且輸入你的賬號密碼
3. 建立網站的專案,  名稱必須是 username.github.io
<img src="/image/2017-05-11-how-to-make-blog-on-github/1.png" alt="GitHub page username guild" width="600"><br>
("username"就是GitHub賬號, 像我的就是hungchicheng.github.io)<br>
4. 按下專案上的 "Set up in Desktop" 按鈕, 複製鏈接下來
5. 建立一個 index.html 放到裡面 (p.s.下面有範例)
6. 輸入log (例如: first commit) 再點 "commit to master" 
7. 點 "Sync" 就可以上傳上去嘍!!<br>
<img src="https://pages.github.com/images/sync-mac.png" alt="GitHub Desktop sync guild"><br>
8. 打開網址 <https://hungchicheng.github.io> ("hungchicheng"記得要換成你自己的賬號)<br>

網站就這樣完成了!!!<br>

### P.S.
第5. 如果index.html不會用的話...可以開啟電腦的記事本直接複製貼上以下內容:<br>
```html
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>
```
在儲存檔名為: index.html 這樣就可以嘍!!!<br>
瀏覽器打開可以直接預覽<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/2.png" alt="index.html guild" width="200"><br>
再繼續做6.即可<br>

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 第二步- Jekyll
下面是[Jekyll中文版](http://jekyll.com.cn/)：
>将纯文本转化为静态网站和博客.<br>
>简单 – 无需数据库、评论功能, 不需要不断的更新版本——只用关心你的博客内容.<br>
>静态 – 只用 Markdown (或Textile)、Liquid、HTML & CSS 就可以构建可部署的静态网站.<br>
>博客形态 - 自定义地址、分类、页面、博客内容 以及 自定义的布局设计 都是系统中的一等公民.<br>

=>簡單來說就是部落格平台, 讓使用者可以用 [GitHub](https://github.com/) 免費託管自己的靜態HTML部落格.<br>
使用者就可以用 Markdown 語法來寫文章, Jekyll 會自動將你的文章自動編譯為Jekyll 規範的 HTML 網頁.<br>
<br>
### 安裝方法<br>

* Windows- [請先參考官方的前置作業教學](https://jekyllrb.com/docs/windows/)<br>
* MAC- [如果跟我一樣Ruby版本太舊, 請先更新](https://www.ruby-lang.org/zh_tw/documentation/installation/#homebrew)<br>

1. 接著在終端機下直接輸入
```console
gem install jekyll
jekyll new mysite
cd mysite
jekyll serve
```
第一行 安裝 jekyll
第二行 新建一個jekyll網站
第三行 進入網站資料夾
第四行 開始運行
2. 打開網頁<br>
[http://localhost:4000](http://localhost:4000)<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/3.png" alt="jekyll sample page" width="800"><br>
到這裡其實就裝好了~~<br>
3. 再上傳到 GitHub,  (同:第一步- GitHub Page 6-8的安裝方式)就可以嘍!!<br>

### 新增文章<br>
直接進入網站資料夾用文字編輯器(我個人喜歡[SublimeText](https://www.sublimetext.com/))開啟<br>
_posts資料夾中的檔案, 新增文章也在這裡, <br>
喜歡圖形化編輯的朋友可以安裝插件詳情請看[第二段教學](https://hungchicheng.github.io/2017/05/13/how-to-make-jekyll-plugin).

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 總結
GitHub Pages ＋ Jekyll使用上的特點：

優點-
* 免費
* 無限流量
* 架設容易
* 無廣告 (也可自己+進去)
* 彈性極高
* 支援 markdown
* 支援版本控制 (就是git)
* 可在離線編輯/預覽
* 中國可瀏覽

缺點-
* 完全開源 (也是優點啦)
* 靜態網頁限定
* 無資料庫 

(以上缺點其實對一般部落格都沒什麼影響)