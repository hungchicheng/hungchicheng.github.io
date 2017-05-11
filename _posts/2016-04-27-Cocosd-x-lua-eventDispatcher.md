---
layout: post
title:  "Cocos2d-x Lua eventDispatcher"
date:   2016-04-27 15:22:54
categories: Cocos2d-x
tags: Cocos2d-x Lua
---

* content
{:toc}


## eventDispatcher
```
local function onTouchBegin(touch, event)

	dump( touch:getLocation() )
 	return true -- 事件發派器需要返回true才可以調用move end
end

local function onTouchEnd(touch, event)

end


    local listener = cc.EventListenerTouchOneByOne:create()
    listener:registerScriptHandler(onTouchBegin,cc.Handler.EVENT_TOUCH_BEGAN )
    listener:registerScriptHandler(onTouchBegin,cc.Handler.EVENT_TOUCH_MOVED )
    listener:registerScriptHandler(onTouchBegin,cc.Handler.EVENT_TOUCH_CANCELLED )
    listener:registerScriptHandler(onTouchEnd,cc.Handler.EVENT_TOUCH_ENDED )
    local eventDispatcher =  self.m_uiLayer:getEventDispatcher()
    eventDispatcher:addEventListenerWithSceneGraphPriority(listener,  self.m_uiLayer)
```