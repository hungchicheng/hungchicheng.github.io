---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: DesignPattern
tags:  Lua C++ 教程 教學 
date:  2017-12-07
last_modified_at: 2017-12-07
title: "Design Pattern - Factory Pattern in C++ and Lua"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<center><br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ee/Factory_Method_pattern_in_LePUS3.png/300px-Factory_Method_pattern_in_LePUS3.png" width="300" itemprop="image">
</center><br>
[Factory Pattern Wiki](https://en.wikipedia.org/wiki/Factory_pattern)<br>
>In object-oriented programming (OOP), a factory is an object for creating other objects – formally a factory is a function or method that returns objects of a varying prototype or class from some method call, which is assumed to be "new". More broadly, a subroutine that returns a "new" object may be referred to as a "factory", as in factory method or factory function. This is a basic concept in OOP, and forms the basis for a number of related software design patterns.
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2017/12/07/Design-Patterns-Factory-Pattern-in-lua-and-C++/" id="link" target="_blank">
	https://hungchicheng.github.io/2017/12/07/Design-Patterns-Factory-Pattern-in-lua-and-C++/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## What is Factory Pattern


## Example in C++

```cpp
#include <iostream>
#include <unordered_map>
#include <functional>
#include <vector>

// Base
class Monster {
public:
    virtual void appear() = 0;
};

// Factory
class MonsterFactory {
public:
    typedef std::unordered_map<std::string, std::function<Monster*()>> registry_map;
    
    // use this to instantiate the proper Derived class
    static Monster * instantiate(const std::string& name)
    {
        auto it = MonsterFactory::registry().find(name);
        return it == MonsterFactory::registry().end() ? nullptr : (it->second)();
    }
    
    static registry_map & registry(){
        static registry_map impl;
        return impl;
    }
    
};

template<typename T> struct MonsterFactoryRegister
{
    MonsterFactoryRegister(std::string name)
    {
        MonsterFactory::registry()[name] = []() { return new T; };
        std::cout << "Registering class '" << name << "'\n";
    }
};
//------------------

class Ogre : public Monster {
public:
    void appear() {  std::cout << "appearing an Ogre " <<std::endl;  }
private:
    static MonsterFactoryRegister<Ogre> AddToFactory_;
};

MonsterFactoryRegister<Ogre> Ogre::AddToFactory_("Ogre" );
//------------------

class Demon : public Monster {
public:
    void appear() {  std::cout << "appearing a Demon " <<std::endl;  }
private:
    static MonsterFactoryRegister<Demon> AddToFactory_;
};

MonsterFactoryRegister<Demon> Demon::AddToFactory_("Demon" );
//------------------


class Troll : public Monster {
public:
    void appear() {  std::cout << "appearing a Troll " <<std::endl;  }
private:
    static MonsterFactoryRegister<Troll> AddToFactory_;
};

MonsterFactoryRegister<Troll> Troll::AddToFactory_("Troll" );
//------------------

int main(int argc, char *argv[])
{
    std::vector<Monster*> Monsters;
    
    Monsters.push_back( MonsterFactory::instantiate("Ogre") );
    Monsters.push_back( MonsterFactory::instantiate("Demon") );
    Monsters.push_back( MonsterFactory::instantiate("Troll") );
    
    for (auto& Monster: Monsters){
        Monster->appear();
    }
    
    return 0;
}

```
Output:
```console
Registering class 'Ogre'
Registering class 'Demon'
Registering class 'Troll'
appearing an Ogre 
appearing a Demon 
appearing a Troll 
appearing a Troll 
Program ended with exit code: 0
```
[Download - Source Code](https://github.com/hungchicheng/DesignPattern/blob/master/C%2B%2B/Factory.cpp)<br>
<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Example in Lua

```lua
function FuncNew( obj ) -- for Inheritance 
    function obj:new( o )
        o = o or {}
        setmetatable( o, self )
        self.__index = self
        return o
    end
    return obj
end

--
Monster = {}
function Monster:create()
    return FuncNew( Monster ):new()
end
function Monster:appear() -- virtual
    -- do nothing
end

--
Ogre = Monster:create() -- inheritance Monster
Ogre.name = "Ogre"
function Ogre:create()
    return FuncNew( Ogre ):new()
end
function Ogre:appear() -- override
    print( "appearing an " .. Ogre.name )
end

Demon = Monster:create() -- inheritance Monster
Demon.name = "Demon"
function Demon:create()
    return FuncNew( Demon ):new()
end
function Demon:appear() -- override
    print( "appearing a " .. Demon.name )
end

Troll = Monster:create() -- inheritance Monster
Troll.name = "Troll"
function Troll:create()
    return FuncNew( Troll ):new()
end
function Troll:appear() -- override
    print( "appearing a " .. Troll.name )
end

--
MonsterFactory = {}
MonsterFactory.registryTable = {}
function MonsterFactory:create()
    return MonsterFactory
end
function MonsterFactory:instantiate( name )
    for k,v in pairs(self.registryTable) do
        if v.name == name then
            return v:create()
        end
    end
    return nil
end
function MonsterFactory:registry( monster )
    print( "Registering class '" .. monster.name .. "'" )
    table.insert( self.registryTable, monster )
end

--
MonsterFactory:registry( Ogre )
MonsterFactory:registry( Demon )
MonsterFactory:registry( Troll )

------------------------------------------------------
local monsters = {}

table.insert( monsters, MonsterFactory:instantiate( "Ogre" ) )
table.insert( monsters, MonsterFactory:instantiate( "Demon" ) )
table.insert( monsters, MonsterFactory:instantiate( "Troll" ) )

for k,v in pairs(monsters) do
    v:appear()
end
```
Output:
```console
Registering class 'Ogre'
Registering class 'Demon'
Registering class 'Troll'
appearing an Ogre
appearing a Demon
appearing a Troll
[Finished in 0.0s]
```
[Download - Source Code](https://github.com/hungchicheng/DesignPattern/blob/master/Lua/Factory.lua)<br>