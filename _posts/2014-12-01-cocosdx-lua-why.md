---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Cocos2d-x
tags:  Cocos2d-x Lua 腳本 遊戲開發 遊戲引擎 反編譯 編輯器 跨平台 輔助開發軟體 教程 教學 
date:  2014-12-01
last_modified_at: 2017-06-19
title: "Cocos2d-x教程教學》為什麼用Cocos2d-x來開發跨平台遊戲"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

我剛進入公司時...<br>
新的專案成立+想開始用Cocos2dx製作中國市場遊戲,<br>
我這個閒閒沒事的新人就被叫來學習+整理+報告Cocos2dx了= ="<br>
(新人報告還流傳到公司其他各組手上...又是另一個故事了)<br>
本篇文章就是憑著印象重新編寫而來的<br>
也給自己當做筆記記錄用= =+<br>

<!-- more -->
<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy;  著作權聲明: <br>
<a href="http://hungchicheng.me/2014/12/01/cocosdx-lua-why/" id="link" target="_blank">
	http://hungchicheng.me/2014/12/01/cocosdx-lua-why/
</a><br>
歡迎分享轉載,  並請註明連結<br>
一一一一一一一一一一一一一一一一一一一一一一一一
<br><br></b></center>
<!-- 著作權end -->
<!-- end -->

## 引擎的優點
Cocos2dx想必是有相當多的優點才會變成現在這樣熱門的遊戲引擎拉<br>
例如以下的優點:
* 跨平台：支援Windows、MAC、Linux、iOS、Android、Web…等等
* 安全性：最終成品是二進位檔案，免除被反編譯的風險。
* 支援腳本：可透過Lua、JavaScript腳本語言言來開發遊戲。
* 眾多輔助工具：地圖編輯、字體編輯、動畫編輯、地圖編輯、粒子特效編輯…等等。
* 豐富的範例檔：[http://www.cocos2d-x.org/hub](http://http://www.cocos2d-x.org/hub)

## 不同平台的開發語言支援表
<table border="1">
	<tr>
		<td></td>
		<td>Object-C</td>
		<td>C++</td>
		<td>Lua</td>
		<td>JavaScript</td>
		<td>C#</td>
	</tr>
	<tr>
		<td>iOS</td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td></td>
	</tr>
	<tr>
		<td>Android</td>
		<td></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td></td>
	</tr>
	<tr>
		<td>Windows XP/7/8</td>
		<td></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
	</tr>
	<tr>
		<td>Linux</td>
		<td></td>
		<td><center>✓</center></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Mac OS</td>
		<td><center>✓</center></td>
		<td><center>✓</center></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Web Browers</td>
		<td></td>
		<td></td>
		<td></td>
		<td><center>✓</center></td>
		<td></td>
	</tr>
</table>


## Cocos2dx 的特點
Cocos2d-x 具備 Cocos2d 的所有特點, 再加上跨平台的特性.
1. 流程控制
輕鬆管理不同畫面之前的切換(切換Scene)
2. 精靈與動作
動畫處理方式相當豐富
3. 圖層及動作
把畫面上的各個元素放到不同圖層上, 方便控制每層的互動及變化
4. 特效
可利用3D 繪圖引擎的部分, 來製作圖層變化.
5. 地圖
支援地圖檔案:如 TiledMap
6. 選單/文字/輸入
支援文字, 圖片, 選擇框, 方便是做互動操作.
7. 多媒體
支援播放不同形式的音樂及音效.
8. 網路連線
支援http 等等網路連線功能



## Cocos2dx 的輔助開發軟體
* [Cocos Studio](http://www.cocos2d-x.org/wiki/Cocos_Studio) -最重要- 
>是Cocos2d-x引擎配套的跨平台遊戲開發工具，幫助開發者快速構建遊戲場景、編輯UI、編輯動畫等遊戲資源，支持第三方的資源導入。
* CocosBuilder<br>
MAC only軟體開發，SpriteBuilder為現在的升級版本的新名稱http://www.spritebuilder.com/
* 71squared的 Particle designer <br>
MAC only特效編輯 & USD 8.00 https://71squared.com/particledesignermapeditor.org的Tiled map editor (地圖編輯器 free, easy to use and flexible tile map editor http://www.mapeditor.org/)
* Texture Atlas –TexturePacker<br>
可用於製作動畫自動產生plist，Creating and using Sprite Sheets in Cocos2D-X with Texture Packer https://www.codeandweb.com/texturepacker
* Texture Atlas –Zwoptex<br>
Mac only. Use Zwoptex to create sprite sheets in just a couple of clicks. https://zwopple.com/zwoptex/ 
* SpriteHelper & LevelHelper <br>
用於創建一個簡單的Platformer game