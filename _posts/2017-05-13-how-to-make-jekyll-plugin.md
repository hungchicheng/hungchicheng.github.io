---
layout: post
categories: GitHubPage
tags:  GitHub Jekyll Plugin SiteMap Jekyll-sitemap Jekyll-admin HTML 部落格 博客 教程 教學 懶人包
date:  2017-05-13 21:22:54
last_modified_at: 2017-05-18 19:00:00
title: "Jekyll及GitHub Page教學(二) 更換主題及安裝插件"
---
<!--                 Title 的建議最大長度                    -->

* content
{:toc}

<!-- 文章概要 -->
上一篇講了我安裝jekyll+放上 GitHub Page的方法
[Jekyll及GitHub Page教學(一)20分鐘建立免費部落格](http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/)
基本上沒有安裝主題還是可以使用啦,

<!-- more -->
<center><b>
<HR>一一一一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy;著作權聲明: <br>
<a href="http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/" id="link" target="_blank">
	http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/
</a><br>
歡迎分享轉載,  並請註明連結<br>
一一一一一一一一一一一一一一一一一一一一一一一一一一一<HR>
</b></center>
<!-- end -->


## 一. 換主題
[官網說明](http://jekyllcn.com/docs/themes/)
>Jekyll 包含有一个强大的主题系统，因此您可以使用社区的模板和样式来定制自己的站点。Jekyll 主题打包了布局文件、包含文件及样式表。同时您也可以使用自己站点的内容去覆盖它们的默认内容。

=> 其實可以一行指令都不用打... 直接站在巨人的肩膀上吧!!<br>
最簡單的方法就是, 進去下面網址直接挑選, 下載下來, 貼到你 Github 資料夾中再上傳就搞定了...<br>
某些主題的作者會希望你去他的 Github 上按個 fork, 記得去按一下啦!!

<http://jekyllthemes.org/><br>
<https://jekyllthemes.io/><br>
<http://themes.jekyllrc.org/><br>
<img src="http://img.sur.ly/thumbnails/620x343/j/jekyllthemes.org.png" width="600"><br>


## 二. 插件
[官網說明](http://jekyllcn.com/docs/plugins/)
>在 GitHub Pages 使用插件, GitHub Pages 是由 Jekyll 提供技术支持的，考虑到安全因素，所有的 Pages 通过 --safe 选项禁用了插件功能，因此如果你的网站部署在 Github Pages ，那么你的插件不会工作。 不过仍然有办法发布到 GitHub Pages，你只需在本地做一些转换，并把生成好的文件上传到 Github 替代 Jekyll 就可以了。

=>都是中文但是我卻看不太懂上面寫什麼... 回去看[原文](https://jekyllrb.com/docs/plugins/)才知道他再說插件在Github 上,因為安全政策的關係不一定完全支援.

### 推薦的插件
* [jekyll-paginate](https://github.com/jekyll/jekyll-paginate)
* jekyll-sitemap
* jekyll-admin
* jekyll-multiple-languages

### 安裝
前置作業需要先安裝bundler,終端機下個等他跑完吧<br>
[如果Ruby版本太舊, 請先更新](https://www.ruby-lang.org/zh_tw/documentation/)
```
sudo gem install bundler
```

在 Gemfile 檔案中加入，例如：<br>
(如果沒有Gemfile可直接用記事本新增)

```
 group :jekyll_plugins do
   gem "jekyll-paginate"
   gem "jekyll-sitemap"
 end
```
儲存後,到終端機輸入就可以開始安裝
```
sudo gem install bundler
```
輸入就可以啟動了
```
bundle exec jekyll server
```