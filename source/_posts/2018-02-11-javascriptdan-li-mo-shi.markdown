---
layout: post
title: "JavaScript单例模式"
date: 2018-02-11 22:55:01 +0800
comments: true
categories: javascript
---


单例模式顾名思义，就是只有一个实例。是最简单的一种设计模式，在开发当中经常会使用到。今天简单梳理一下。


单例模式的优点有
```
可以全局访问
避免共享资源多重占用
内存中只有一个实例，节约内存空间
避免频繁创建销毁，提高性能
```

单例模式实现方式

1.使用闭包
```js
var Singleton = (()=>{
  var instance;
  var _this = this;
  return {
      getInstance: function(){
          if(typeof instance !== "object"){
              instance = _this;
          }
          return instance;
      }
  }
})()
```

<!-- more -->

2.通用的惰性单例模式
```js
var Dog = function(){
}
var SingleDog = ((fn)=>{
var instance;
return function(){
  return instance || (instance = fn.apply(this, arguments));
}
})();

var dog1 = SingleDog(Dog);
var dog2 = SingleDog(Dog);
console.log(dog1===dog2);
```

3.使用全局变量
```js
var instance;
function SingleDog(){
    if(typeof instance === 'object'){
        return instance;
    }
    instance = this;
}
var dog1 = new SingleDog();
var dog2 = new SingleDog();
console.log(dog1 === dog2);
```
