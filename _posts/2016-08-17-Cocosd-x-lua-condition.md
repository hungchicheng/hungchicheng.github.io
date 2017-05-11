---
layout: post
title:  "Cocos2d-x Lua a == true ? A :B"
date:   2016-08-17 15:22:54
categories: Cocos2d-x
tags: Lua
---

* content
{:toc}


## print("blah: " .. (a == true ? "yes" : "no"))
```
print("blah: " .. (a == true ? "yes" : "no"))

print("blah: " .. (a and "yes" or "no"))
```