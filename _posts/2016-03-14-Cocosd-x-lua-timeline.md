---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Cocos2d-x
tags:  Cocos2d-x Lua 教程 教學 
date:  2016-03-14
last_modified_at: 2018-07-17
title: "Cocos2d-x教程教學》Lua動畫事件"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}


## add timeline
```lua
-- 新UI 動畫
local actionTmp = cc.CSLoader:createTimeline("csb/battleDescription2.csb")
csbNode:runAction(actionTmp)
actionTmp:gotoFrameAndPlay(0,false)
```

## timeline event
```lua
-- 動畫事件
local function onFrameEvent(frame)
    if nil == frame then
        return
    end
    local str = frame:getEvent()
    if str == "end" or  str == "END" then
      print("123")
    end
end

actionTmp:play("start", true)
actionTmp:setFrameEventCallFunc(onFrameEvent)
```