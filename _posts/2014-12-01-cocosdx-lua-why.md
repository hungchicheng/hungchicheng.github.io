---
layout: post
categories: Cocos2d-x
tags:  Cocos2d-x Lua 腳本 遊戲開發 遊戲引擎 反編譯 編輯器 跨平台 輔助開發軟體 教程 教學 
date:  2014-12-01 21:22:54
last_modified_at: 2017-05-18 19:00:00
title: "教程教學-為什麼使用Cocos2d-x跨Android&iOS平台來開發遊戲"
---
<!--                 Title 的建議最大長度                    -->

* content
{:toc}

我剛進入公司時...<br>
新的專案成立+想開始用Cocos2dx製作中國市場遊戲,<br>
我這個閒閒沒事的新人就被叫來學習+整理+報告Cocos2dx了= ="<br>
(新人報告還流傳到公司其他各組手上...又是另一個故事了)<br>
本篇文章就是憑著印象重新編寫而來的<br>
也給自己當做筆記記錄用= =+<br>

<!-- more -->
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
</table>


## Cocos2dx 的特點

## Cocos2dx 的輔助開發軟體
* -最重要- Cocos Studio
* CocosBuilder (MAC only軟體開發，SpriteBuilder為現在的升級版本的新名稱http://www.spritebuilder.com/)
* 71squared的 Particle designer (MAC only特效編輯 & USD 8.00 https://71squared.com/particledesigner) mapeditor.org的Tiled map editor (地圖編輯器 free, easy to use and flexible tile map editor http://www.mapeditor.org/)
* Texture Atlas –TexturePacker：(可用於製作動畫自動產生plist，Creating and using Sprite Sheets in Cocos2D-X with Texture Packer https://www.codeandweb.com/texturepacker)
* Texture Atlas –Zwoptex：(Mac only. Use Zwoptex to create sprite sheets in just a couple of clicks. https://zwopple.com/zwoptex/ )
* SpriteHelper & LevelHelper (用於創建一個簡單的Platformer game)