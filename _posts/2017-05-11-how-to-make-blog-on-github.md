---
layout: post
title:  "如何用Jekyll在Github來建立部落格"
date:   2017-05-11 21:22:54
categories: Jekyll
tags: Github Jekyll Plugin SiteMap Jekyll-sitemap Jekyll-admin
---

* content
{:toc}

想弄一個Blog來記錄之前存下來的各種Code,<br>
看到Jekyll竟然可以用Github來架Blog...這真的是太方便了<br>
這篇就是記錄我架Blog的方法<br>
<!-- more -->
## 第一步-GitHub網頁
先從Github的網頁功能講起<br>
如同字意,就是可以再Github網站上放入自己的網頁<br>
[原網址-英文](https://pages.github.com/)<br>
<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/1.png"><br>
先建立網站的專案名字必須是username.github.io<br>
username就是Github賬號,像我的就是hungchicheng.github.io<br>
上傳個 index.html 上去,就可以嘍<br>
index.html 可以像這樣:
```
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>
```
打開後<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/2.png"><br>
<br>
把它傳上github,就會看到相同的結果.
## 第二步-安裝Jekyll
[原網址-英文](https://jekyllrb.com/)<br>
在終端機下輸入<br>
```
gem install jekyll bundler
jekyll new mysite
cd mysite
bundle exec jekyll serve
```
打開網頁<br>
[http://localhost:4000](http://localhost:4000)<br>
<img src="/image/2017-05-11-how-to-make-blog-on-github/3.png"><br>
到這裡其實就裝好了!!!<br>
如何新增文章/換皮膚...就下集待續