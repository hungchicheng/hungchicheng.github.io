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
<br>
## 第一步-GitHub網頁
先從Github的網頁功能講起<br>
如同字意,就是可以再Github網站上放入自己的網頁<br>
[原網址-英文](https://pages.github.com/)<br>
<br>
<img src="https://thumbnail0.baidupcs.com/thumbnail/0d6d69ae2e963ebf507cdb22ad20de1b?fid=548529631-250528-760901278449231&time=1494579600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-ceQyJL2WW2Zb5A6XOeL330mjCoY%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=3055174279743183023&dp-callid=0&size=c710_u400&quality=100" alt=""  border="0" itemprop="image" class="img-circle"><br>
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
<img src="https://thumbnail0.baidupcs.com/thumbnail/4ab40c06f222474f9d15c11ddf027510?fid=548529631-250528-71612917865432&time=1494579600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-0zcqePdYApWxbwQVXw0rsJobWsQ%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=3055160955109122626&dp-callid=0&size=c710_u400&quality=100" alt=""  border="0" itemprop="image" class="img-circle"><br>
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
<img src="https://thumbnail0.baidupcs.com/thumbnail/191ecc2a6b624f7d8a8f6322e8c74abf?fid=548529631-250528-835105290149673&time=1494579600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-BTDY9HkSxKdc2Z7FPsXuN8SE9V4%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=3055526683595565487&dp-callid=0&size=c710_u400&quality=100" alt=""  border="0" itemprop="image" class="img-circle"><br>
到這裡其實就裝好了!!!<br>
如何新增文章/換皮膚...就下集待續