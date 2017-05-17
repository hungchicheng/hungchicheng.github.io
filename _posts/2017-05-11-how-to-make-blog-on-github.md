---
layout: post
categories: GithubPage
tags:  Github Jekyll Plugin SiteMap Jekyll-sitemap Jekyll-admin Html 非痞客邦 部落格 博客 教程 教學 懶人包
date:  2017-05-11 21:22:54
title: "10分鐘建立自己的無廣告免費部落格Jekyll + Github Page快速教學"
---
<!--                 Title 的建議最大長度                    -->

* content
{:toc}

<br>
<!-- 文章概要 -->
想弄一個Blog來記錄之前存下來的各種Code，<br>
看到Jekyll竟然可以用Github來架自己管理的Blog...<br>
這真的是太方便了，<br>
這篇就是記錄Jekyll部落格的特點，<br>
以及我架Blog的方法及教學。<br>

<!-- more -->
<center><b>
<HR>一一一一一一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy;著作權聲明: <br>
<a href="http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/" id="link" target="_blank">
	http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/
</a><br>
歡迎分享轉載， 並請註明連結<br>
一一一一一一一一一一一一一一一一一一一一一一一一一一一一一<HR>
</b></center>
<!-- end -->

## 第一步- GitHub Page
[GitHub Page](https://pages.github.com/) 可以幫你或你的開發專案提供網頁，直接由它來幫你免費的Host託管以及發佈網站，
只需要將你的專案存在 [Github](https://github.com/) 的儲存庫 (Repository) 中，
不需自己建伺服器，没有麻烦的設定，就可以做個人的網站，
更可以綁定自己的網域名城，
就不用再費其他心思處理各種麻煩事了。<br>
<br>

安裝方式如下:<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/1.png"><br>
先建立網站的專案， 名稱必須是username.github.io<br>
username就是Github賬號，<br>
像我的就是hungchicheng.github.io<br>
再上傳個 index.html 上去， 就可以嘍!!<br>
<br>
如果不會用的話...可以開啟電腦的記事本直接複製貼上以下內容:<br>
```
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>
```
在儲存檔名為: index.html 這樣就可以嘍!!!<br>
<br>
瀏覽器打開後<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/2.png"><br>
把它直接傳上Github，<br>
打開網址 <https://hungchicheng.github.io> 
(hungchicheng記得要換成你的賬號)<br>
一個網站就這樣完成了!!! 接著下段~~~~~<br>

<!-- 手動放廣告 -->
<br>
{% include ad.html %}
<br>
<!-- 手動放廣告 -->

## 第二步-安裝Jekyll
[Jekyll](https://jekyllrb.com/) 是一個部落格平台，
主要功能就是能使用者可以個 [Github]<https://github.com/> 上使用靜態的 HTML 頁面建置部落格。使用者使用 Markdown 語法撰寫部落格文章，Jekyll 則會透過樣板 (Template) 將文章轉為 HTML 網頁。
<img src="http://jekyllrb.com/img/octojekyll.png"><br>
<br>
安裝步驟如下:<br>
MAC可在終端機下直接輸入<br>
```
gem install jekyll bundler
jekyll new mysite
cd mysite
bundle exec jekyll serve
```
打開網頁<br>
[http://localhost:4000](http://localhost:4000)<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/3.png" width="200"><br>
到這裡其實就裝好了!!!<br>
再上傳到 github， 就可以嘍!!<br>
<br>

## 最後- 總結特點：
GitHub Pages ＋ Jekyll
優點
* 免費
* 流量無限制
* 架設容易
* 彈性極高
* 支援 markdown
* 支援 git 版本控制 (廢話XD)
* 可在離線狀態下寫，並在本機上預覽
* 中國也可以瀏覽
缺點
* 靜態網頁限定， 無資料庫 (其實對一般部落格沒什麼影響)

如何新增文章/換皮膚...就下集待續