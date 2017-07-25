---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: GitHubPage
tags:  GitHub Jekyll Plugin SiteMap Jekyll-paginate Jekyll-sitemap Jekyll-admin HTML 部落格 博客 教程 教學 懶人包
date:  2017-05-13
last_modified_at: 2017-06-19
title: "Jekyll及GitHub教學2》更換主題及安裝插件"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="http://img.sur.ly/thumbnails/620x343/j/jekyllthemes.org.png" alt="jekyllthemes webpage" width="300" itemprop="image">
</center><br>
Jekyll安裝好後, 就可以在GitHub上使用部落格了, 所以也可以開始換個漂亮的主題(theme)了哦!! 這篇教學就用記下換主題及利用插件教程,包含Jekyll-paginate Jekyll-sitemap Jekyll-admin.<br><br>
<!-- more -->

上上一篇講了我 安裝jekyll+放上 GitHub Page的方法:<br>
[Jekyll及GitHub Page教學(一)20分鐘建立免費部落格](http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/)<br>

<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/" id="link" target="_blank">
	http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 一. 換主題
[官網說明](http://jekyllcn.com/docs/themes/)
>Jekyll 包含有一个强大的主题系统，因此您可以使用社区的模板和样式来定制自己的站点。Jekyll 主题打包了布局文件、包含文件及样式表。同时您也可以使用自己站点的内容去覆盖它们的默认内容。

=> 其實可以一行指令都不用打... 直接站在巨人的肩膀上吧!!<br>
最簡單的方法就是, 進去下面網址直接挑選, 下載下來, 貼到你 Github 資料夾中再上傳就搞定了...<br>
某些主題的作者會希望你去他的 Github 上按個 fork, 記得去按一下啦!!
<img src="http://img.sur.ly/thumbnails/620x343/j/jekyllthemes.org.png" alt="jekyllthemes webpage" width="600"><br>
<http://jekyllthemes.org/><br>
<https://jekyllthemes.io/><br>
<http://themes.jekyllrc.org/><br>

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 二. 插件
[官網說明](http://jekyllcn.com/docs/plugins/)
>在 GitHub Pages 使用插件, GitHub Pages 是由 Jekyll 提供技术支持的，考虑到安全因素，所有的 Pages 通过 --safe 选项禁用了插件功能，因此如果你的网站部署在 Github Pages ，那么你的插件不会工作。 不过仍然有办法发布到 GitHub Pages，你只需在本地做一些转换，并把生成好的文件上传到 Github 替代 Jekyll 就可以了。

=>都是中文但是我卻看不太懂上面寫什麼... 回去看[原文](https://jekyllrb.com/docs/plugins/)才知道他再說插件在Github 上,因為安全政策的關係不一定完全支援.

### 推薦的插件
* [jekyll-paginate](https://github.com/jekyll/jekyll-paginate)
>Pagination Generator for Jekyll
* [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)
>Jekyll plugin to silently generate a sitemaps.org compliant sitemap for your Jekyll site
* [jekyll-admin](https://github.com/jekyll/jekyll-admin)
>A Jekyll plugin that provides users with a traditional CMS-style graphical interface to author content and administer Jekyll sites.

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