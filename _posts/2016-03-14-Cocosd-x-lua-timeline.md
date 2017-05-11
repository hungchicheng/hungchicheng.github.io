---
layout: post
title:  "Cocos2d-x Lua Animation Timeline"
date:   2016-03-14 15:22:54
categories: Cocos2d-x
tags: Cocos2d-x Lua
---

* content
{:toc}


## add timeline
```
-- 新UI 動畫
local actionTmp = cc.CSLoader:createTimeline("csb/battleDescription2.csb")
csbNode:runAction(actionTmp)
actionTmp:gotoFrameAndPlay(0,false)Cocosdxlua
```

## timeline event
```
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