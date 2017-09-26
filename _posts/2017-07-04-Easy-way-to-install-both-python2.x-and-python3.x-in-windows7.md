---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Python
tags:  Python Script
date:  2017-07-04
last_modified_at: 2017-07-04
title: "Easy way to install both Python2.x and Python3.x in Windows"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="/image/2017-07-04-Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/python-check-version.png" alt="python check version" width="500" itemprop="image">
</center><br>
This document aims to give an easy way to install both Python 2 &3. Python is a useful script programing language, but I never use it before. This is the first time I used. Recently, my manager wants me to write a tool to convert in game xml string table to Excel file. We must use Python3 (Unicode support) to deal with multi-language, and sadly our game compiler is based on Python 2... So, it's also my first problem to face with.
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="http://hungchicheng.me/2017/07/04/Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/" id="link" target="_blank">
	http://hungchicheng.me/2017/07/04/Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Install Python2 &3
Go to the Python download page and download Python<br>
<https://www.python.org/downloads/>
1. Firstly, install python 2.x<br>
For example, install in C:\Python27
2. Install python 3.x<br>
For example, install in C:\Python36-32

<img src="/image/2017-07-04-Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/install-python-example.png" alt="install python example" width="500" itemprop="image"><br>

## Rename Python3
Go to python3 folder C:\Python36-32
rename python to python3
<img src="/image/2017-07-04-Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/rename-python3.png" alt="rename python3" width="500" itemprop="image"><br>

## Add System Environment Variables
add system environment back for Python2. (Because Python3 is installed)
```console
Path
C:\Python27\;C:\Python27\Scripts\;
```
Check Python3 is corrently set.
```console
Path
C:\Python36-32;C:\Python36-32\Scripts;
```

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Test
Just Open CMD and check both python is correctly install.
```console
python --version
python3 --version
```
<img src="/image/2017-07-04-Easy-way-to-install-both-python2.x-and-python3.x-in-windows7/python-check-version.png" alt="python check version" width="500" itemprop="image"><br>
Done!!!

## P.S. Use pip with python3
A sample to use pip install xlrd(excel read).
```console
python3 -m pip install xlrd 
```