---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: GitHubPage
tags:  GitHub Jekyll SEO 搜尋優化 Google搜尋 schema.org Microdata 結構化 部落格 博客 索引 教程 教學 懶人包
date:  2017-06-02
last_modified_at: 2017-06-13
title: "Jekyll及GitHub教學4》SEO優化-讓網站更易被搜尋"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="/image/2017-06-02-adding-schema-org-metadata-to-Jekyll/google-search.png" alt="google search logo" width="300" itemprop="image">
</center><br>
本篇教學Jekyll加入Schema.org的SEO優化教程,Schema.org為可擴展schemas中,推的Microdata格式,Microdata也是HTML5的一部份,可以讓搜尋引擎更易了解部落格Blog網站內容,加強在地SEO(搜尋引擎最佳化/優化search engine optimization),進而提升被搜尋引擎檢索的機率. 會做這個其實是一位做前端的朋友看到我Blog後給我的建議,Jekyll架構下實作也不難,如果能多多少少提升一點搜尋量好像也不錯!!就記錄下來了.<br><br>
<!-- more -->

之前的文章有: 安裝jekyll+放上 GitHub Page的方法:<br>
[Jekyll及GitHub Page教學(一)20分鐘建立免費部落格](http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/), <br>
,再來 更換主題及安裝插件的方法:<br>
[Jekyll及GitHub Page教學(二) 更換主題及安裝插件](http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/)<br>
,還有讓百度抓Coding.net鏡像:<br>
[Jekyll及GitHub Page教學進階-讓百度搜尋Github部落格](http://hungchicheng.me/2017/05/14/2017-05-14-how-to-let-baidu-search/)<br>

<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="http://hungchicheng.me/2017/06/02/adding-schema-org-metadata-to-Jekyll/" id="link" target="_blank">
	http://hungchicheng.me/2017/06/02/adding-schema-org-metadata-to-Jekyll/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

## Microdata
[Wiki](https://en.wikipedia.org/wiki/Microdata_(HTML))
>Microdata is a WHATWG HTML specification used to nest metadata within existing content on web pages. Search engines, web crawlers, and browsers can extract and process Microdata from a web page and use it to provide a richer browsing experience for users. Search engines benefit greatly from direct access to this structured data because it allows search engines to understand the information on web pages and provide more relevant results to users.

=>簡單來說就是在網頁中附加Microdata可以讓搜尋引擎更好抓取內容,例如:
```
<!-- 告訴搜尋引擎 name 是HungChi's Blog -->
<meta itemprop="name" content="HungChi's Blog">
```
上面只是範例的一小段...要跟接下來的[Schema.org](/#Schema.org)一起使用

## Schema.org
[原文站](http://schema.org)<br>
[中文站](http://schema.org.cn/docs/getstarted.html)
>Schema.org 提供了一份共享的词汇表，站长可以使用它来标记网页，而这些标记则被主要的搜索引擎： Google， Microsoft， Yandex 和 Yahoo! 所支持。
你将 schema.org 词汇表与 微数据 microdata 结合起来使用，为你的 HTML 内容添加额外信息。我们长远的目标是支持更多的格式，但目前我们将专注于微数据 Microdata。 本指南将帮助你更快地熟悉微数据和 schema.org，之后你便可以为你的网页添加标记。<br>

=>可以說在HTML中加入一些屬性，讓搜尋引擎更容易了解網站內容，現在Google也建議用Schema.org，而且測試工具也會記錄頁面上的結構化Microdata資料，SEO優化中當然就推薦用它啦。

### 方法1
例如我 [index.html](http://hungchicheng.me) 中直接加入一段script部落格的Type就是"Blog".
```
<script type="application/ld+json">
{ "@context": "http://schema.org", 
 "@type": "Blog",
 "keywords": "Cocos2d-x Lua C++ Object-C C# Unity Senior Software Engineer International Games System Master's degree National Taipei University. ", 
 "url": "{{ site.url }}",
 "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "{{ site.url }}"
  },
 "author": {
    "@type": "Person",
    "name": "Hung-Chi Cheng (程弘錡)",
    "sameAs": [
        "https://github.com/hungchicheng/",
        "https://www.linkedin.com/in/hungchicheng/"
    ]
  }
 }
</script>
```
但是其他post文章要這樣一篇篇加也太麻煩了,所以請繼續看做法2.

### 方法2
直接在layout版面樣式裡面的post.html, 插入schema直接套用全部post文章,
```
div中itemscope itemtype="http://schema.org/種類"
itemprop="屬性"
以此類推...
```

種類跟屬性可以到[Schema官網](http://schema.org/docs/schemas.html)裡面找, 我這裡用[Schema BlogPost](http://schema.org/BlogPosting)來做範例:<br>(請注意綠框的itemscope itemtype itemprop, 下面也有完整程式碼連結.)<br>
<img src="/image/2017-06-02-adding-schema-org-metadata-to-Jekyll/jekyll schema sample.png" alt="jekyll schema sample" width="900"><br>
連結:[Github完整程式碼](https://github.com/hungchicheng/hungchicheng.github.io/blob/1c0381729c6e9421d51fc221f4d709618a607b0b/_layouts/post.html)(打開連結用CTRL+F搜尋"itemprop"會更清楚)

### 結構化測試工具
最後就可以進入網站[Google測試結構化資料](https://search.google.com/structured-data/testing-tool) 貼上網址 或是程式碼片段, 就可以執行測試了!!!
<img src="/image/2017-06-02-adding-schema-org-metadata-to-Jekyll/jekyll github & Structured Data Testing Tool.png" alt="jekyll github & Structured Data Testing Tool" width="900"><br>
[我的Blog測試結果](https://search.google.com/structured-data/testing-tool#url=http%3A%2F%2Fhungchicheng.me%2F2017%2F05%2F11%2Fhow-to-make-blog-on-github%2F)

## 參考網址
<http://veithen.github.io/2014/11/17/jekyll-schema-org-metadata.html><br>
<http://getschema.org/index.php?title=BlogPosting><br>
<https://webmasters.googleblog.com/2013/05/using-schemaorg-markup-for-organization.html><br>