---
layout: post
categories: GitHubPage
tags:  GitHub Jekyll 百度 Coding.net 部落格 博客 索引 教程 教學 懶人包
date:  2017-05-14 21:22:54
last_modified_at: 2017-05-22 19:00:00
title: "[Jekyll及GitHub Page進階教學] 讓百度抓Coding.net鏡像"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<img src="http://www.baidu.com/img/bd_logo1.png" alt="baidu logo" width="200" align="left"><br>
上上一篇講了我 安裝jekyll+放上 GitHub Page的方法:  [Jekyll及GitHub Page教學(一)20分鐘建立免費部落格](http://hungchicheng.me/2017/05/11/how-to-make-blog-on-github/), <br>
上一篇講了我 更換主題及安裝插件的方法:  [Jekyll及GitHub Page教學(二) 更換主題及安裝插件](http://hungchicheng.me/2017/05/13/how-to-make-jekyll-plugin/)<br>
<br>
這次我發現中國最大的搜尋引擎百度並不會自動抓 Github Page 的內容,<br>
但我會有一部分的文章寫跟 cocos2d-x 有關的文章,<br>
少了百度搜尋好像就少了什麼(有時候我也會到百度搜尋看看cocos遇到的問題啦...)<br>
所以找到了這個方法作鏡像,讓百度蜘蛛可以直接爬這裡,就不用怕 Github 拒絕百度了.

<!-- more -->
<center><b>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
<font color="#2684E8" size="3">&copy;  </font>著作權聲明: <br>
<a href="http://hungchicheng.me/2017/05/14/how-to-let-baidu-search/" id="link" target="_blank">
	http://hungchicheng.me/2017/05/14/how-to-let-baidu-search/
</a><br>
歡迎分享轉載,  並請註明連結<br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- end -->

## 第一步- 網域名稱
先弄一個網域名城, 網路上這部分的資料相當多, 這裡就不在敘述了,<br>
我是直接到 [godaddy](http://godaddy.com/) <br>
<img src="https://upload.wikimedia.org/wikipedia/en/thumb/6/6c/GoDaddy.svg/1200px-GoDaddy.svg.png" alt="godaddy logo" width="400"><br>
去買一個我喜歡的網址 [hungchicheng.me](http://hungchicheng.me) 就是我的英文名+.me非常好記.


## 第二步- Coding.net
>Coding 是一個面向開發者的雲端開發平台，目前提供代碼託管，運行空間，質量控制，項目管理等功能。Coding 提供社會化協作功能，包含了社交元素，為開發者提供技術討論和協作平台。

=> 不用想那麼多... 簡單來說就是中國的Github啦= =+

### 註冊
在Coding.net上註冊一個新的賬號，新的賬號跟你的 github 名稱相同，例如我的: hungchiheng, 再建立一個同名專案hungchicheng,
將本地端的github page (也就是jekyll專案)建立與coding.net的關聯

### 鏡像
```
# 專案目錄下
git remote add mirror git@git.coding.net:hungchicheng/hungchicheng.git
```
如果不小心弄錯的話... <br>
可以到目錄底下的.git資料夾的config文件,<br>
用文字編輯器直接修改 mirror 的網址.

### 上傳程式碼

```
git add --all
git commit -m "first commit"
git push                      # 送交到github
git push mirror master        # 送交到coding.net
```

上傳完成後,登錄 coding.net <br>
進入pages設定頁設定網頁服務位置到master並開啟服務.<br>
在填入你的網域名稱綁定即可.<br>
經過以上的操作後, 可以進入 [hungchicheng.coding.me](http://hungchicheng.coding.me)就可以看到你鏡像的網站了

## 第三步- CloudXns智能解析DNS
這裡我是利用中國免費的 DNS 網域名城伺服器,<br> 
將百度的 ip 重新導入coding.net其他的導入回github.<br>
首先申請好賬號,並且把裡面的"網域名稱伺服器"設定回godaddy.
```
lv3ns1.ffdns.net
lv3ns2.ffdns.net
lv3ns3.ffdns.net
lv3ns4.ffdns.net
```
填到godaddy裡面等個10分鐘左右, 就會看到你的網域已經成功被CloudXns接管,
<img src="/image/2017-05-14-how-to-let-baidu-search/CloudXNS state.png" alt="CloudXNS state" width="800"><br>
就可以進入設定"全网默认" 指定回 github<br>
"百度" 指定到 coding.net<br>
如下圖:<br>
<img src="/image/2017-05-14-how-to-let-baidu-search/CloudXNS Cname.png" alt="CloudXNS Cname" width="800"><br>
這樣就搞定嘍!!<br> 
回去[百度站長工具](http://zhanzhang.baidu.com/)抓取診斷+登錄網站吧