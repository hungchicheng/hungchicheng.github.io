---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Blogger
tags:  Google Blogger blogspot Facebook Page m=1 同步留言 自動分享貼文 IFTTT 部落格 博客 教程 教學 懶人包
date:  2017-06-10
last_modified_at: 2018-07-17
title: "Blogger教學》Facebook留言同步 手機版?m=1也可同步 (2018/2月已失效)"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="/image/2017-06-10-post-blogger-automatically-facebook-sync-comments/facebook-comments-in-blogger.png" alt="google search logo" width="500" itemprop="image">
</center><br>
!!!FB已經於2018的2月關閉此功能!!!
本篇講如何用Google Blogger(blogspot)與Facebook的留言同步, 相信這對想用Facebook來做宣傳, 或是想自動同步留言到粉絲團 自動分享貼文都非常有幫助.<br>我這次突然換成Blogger的教學, 是因為幫朋友弄Blogger主題時, 發現這個好玩的全部自動化功能, 也讓我開始當起新手前端工程師了, 從修改html+css到現在弄了一些JavaScript, 自己也學到了不少= =+. <br><br>
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2017/06/10/post-blogger-automatically-facebook-sync-comments/" id="link" target="_blank">
	https://hungchicheng.github.io/2017/06/10/post-blogger-automatically-facebook-sync-comments/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 申請Facebook開發人員及使用留言板
要使用 FB 的功能第一步, 要先成為FB的開發人員+申請應用<br>
[facebook for developers](https://developers.facebook.com/apps?locale=zh_TW)<br>
照著填就好, 再新增應用程式,<br>
填入應用程式名稱+認證號碼就申請成功了,<br>
<img src="/image/2017-06-10-post-blogger-automatically-facebook-sync-comments/facebook-app-id.png" alt="facebook app id" width="900" itemprop="image"><br>
<br>
並且馬上就可以看到我們所需要的應用程式編號(fb:app_id)!!<br>
確認無誤之後記得到應用程式審查裡的第一項發佈.<br>
<img src="/image/2017-06-10-post-blogger-automatically-facebook-sync-comments/facebook-app-release.png" alt="facebook app id" width="900" itemprop="image"><br>
(我當初就沒注意到這個步驟... 想說弄了老半天怎麼留言都出不來...)

申請好後就可以設定到你的blog中,<br>
進入[blogger後台](https://www.blogger.com/)>主題>編輯HTML.<br>
(第一次使用或是不熟的人記得先按"右上角備份)<br>
搜尋<head>,並且在"下方"加入
```html
<!-- [ Social Media meta tag ] -->
<meta content='259238854555058' property='fb:app_id'/>
<meta content='115653692364277' property='fb:admins'/>
```
fb:app_id 就是前面講的應用程式編號<br>
fb:admins 可以到[Lookup-ID](https://lookup-id.com/)這個用網站搜尋, 直接貼上自己/粉絲團的網址就可以查到了.

### 安裝留言板
這個部分我是參考<br>
[Facebook 留言框最簡單快速的安裝方式 + 常見問題整理](http://www.wfublog.com/2017/01/fb-comment-box-v2-faq.html)<br>
這部分跟參考網站懶人包不同的地方, 是我也想讓手機版同步, 所以在elem.setAttribute 做了修改.
搜尋</body>,並且"下方"加入
```js
<!-- FB 留言框安裝懶人包 V2 -->
<b:if cond='data:blog.pageType == &quot;item&quot;'>
<div class='fb-comments' data-colorscheme='light' data-href='' data-numposts='5' data-width='100%' id='fb-comments'>
</div>
<script>
//<![CDATA[
(function() {
var targetId = "comments", // 留言框出現的位置 id
ver = "2.9", // API 版本可以自行設定需要的版本
url = "//connect.facebook.net/zh_TW/sdk.js#xfbml=1&version=v" + ver,
script = document.createElement("script"),
elem = document.getElementById("fb-comments"),
target = document.getElementById(targetId);
elem.setAttribute("data-href", "https://" + location.hostname + location.pathname.split("?")[0]); 
// https 可以改回用http, location.hostname就是網站的網址,詳細請看下一段網址調整
if (target) {
target.parentNode.insertBefore(elem, target);
}
script.src = url;
document.getElementsByTagName("head")[0].appendChild(script);
})();
//]]>
</script>
</b:if>
<!-- Designed by WFU BLOG -->
```
做到這裡就已經可以進入你的blog看到FB的留言了!!

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

### 開啟FB同步化
進入[FB開發者留言工具](https://developers.facebook.com/tools/comments/)
<img src="/image/2017-06-10-post-blogger-automatically-facebook-sync-comments/facebook-comment-mirror.png" alt="facebook comments mirror" width="900" itemprop="image"><br>
最後一項打勾"是, 鏡像到"開啟鏡像功能. 其他選項設定就看自己的需求使用了.

## 網址調整
[Blogger](https://www.blogger.com)有個麻煩的地方就是手機版也會在網址自動加上+?m=1, 或是自動跳轉到符合使用這地區的網域, 如台灣就會跳轉回.tw的網址了, 就會被 FB 判定成不同的網站了,以下是解決方法.

### 解決手機版?m=1
(上面的"FB留言框安裝懶人包V2", 是我已經改好的版本了, 這段可忽略)<br>
如果使用[官網教學](https://developers.facebook.com/docs/plugins/comments/)/或是其他教學做的話, 就會遇到手機版跟電腦版留言無法同步的問題, 這是因為 Blogger 手機版會自動帶入參數?m=1, 導致網址不同的問題...只要把"?m=1"去掉即可.
```js
elem.setAttribute("data-href", "https://" + location.hostname + location.pathname.split("?")[0]); 
```
所以我直接更改懶人包成setAttribute, 並且把網址"?m=1"的參數砍掉. <br>

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

### 解決區域化導向
<h4>方法1: 直接禁止導向</h4>
這部分是我看到這篇討論, 
[關於 Blogger 網域導向（Country-Specific URLs）與強制恢復 .com](http://whclive.blogspot.tw/2012/06/prevent-your-blogger-blog-from.html)<br>
使用方法就是搜尋<head>底下貼入以下內容
```js
<!-- 禁止自動跳轉 -->
<script type='text/javascript'>
var blog = document.location.hostname;
var slug = document.location.pathname;
var ctld = blog.substr(blog.lastIndexOf(&quot;.&quot;)); 
if (ctld != &quot;.com&quot;) {
var ncr = &quot;http://&quot; + blog.substr(0, blog.indexOf(&quot;.&quot;)); // 可改 https
ncr += &quot;.blogspot.com/ncr&quot; + slug;
window.location.replace(ncr);
}
</script>
```

<h4>方法2: 直接設定Comment的網址</h4>
如果你想保留區域化導向, 可以改用這個我後來發現的方法, 給需要用到的人.<br>
做法就是直接更改懶人包的code的這一段.
```js
elem.setAttribute("data-href", "https://" + location.hostname + location.pathname.split("?")[0]); 
```
location.hostname 刪除在 https:// 直接改成你的網址也行,例如:
```js
elem.setAttribute("data-href", "https://fishfish615.blogspot.com/" + location.pathname.split("?")[0]); 
```

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## 自動分享貼文 
懶得手動分享, 想自動化處理, 記得看一下這裡!!<br>
我自己是已經試過好幾種方式都不能用了...<br>
才找到這個免費+簡單+好用的<br>
[IFTTT](https://ifttt.com/)<br>
用FB登錄+搜尋 Share your blog posts to your Facebook page(粉絲團)<br>
(Share your blog posts to your Facebook個人頁面)<br>
設定好以後, 在 blogger 發表新文章就會自動同步過去了!

## 實際範例
新增一篇文章, 並且用你的 FB 分享網址,<br>
在文章就會看到這個畫面, 恭喜安裝成功了!!<br>
Your comment may also appear on 魚兒愛旅遊's Facebook Page.<br>
<img src="/image/2017-06-10-post-blogger-automatically-facebook-sync-comments/facebook-comments-in-blogger.png" alt="google search logo" width="600" itemprop="image"><br>
如果想測試留言, 以下都可以任意使用<br>
<br>
[Blogger測試區](https://fishfish615.blogspot.com/2017/06/Post-Blogger-Automatically-to-Facebook-and-Sync-Comments_9.html)<br>
<br>
[Facebook測試區](https://www.facebook.com/fishfish615/posts/116371305625849)
