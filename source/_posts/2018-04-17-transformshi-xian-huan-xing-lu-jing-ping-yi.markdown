---
layout: post
title: "transform实现环形路径平移"
date: 2018-04-17 10:20:11 +0800
comments: true
categories: css
---

在上一篇中，介绍了css动画。这一篇介绍transform怎么实现环形平移。

旋转动画，用transform-origin定义圆心的位置，然后用rotate()进行旋转。
```
@keyframes spin {
    0% {
        transform: rotate(-90deg);
    }
    25% {
        transform: rotate(0deg);
    }
    50% {
        transform: rotate(90deg);
    }

    75% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(-90deg);
    }
}
.avatar{
    animation: spin 10s infinite linear;
    transform-origin: 50% 150px;
}
```

<style>
@keyframes spin {
    0% {
        transform: rotate(-90deg);
    }
    25% {
        transform: rotate(0deg);
    }
    50% {
        transform: rotate(90deg);
    }

    75% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(-90deg);
    }
}
@keyframes spin-reverse {
    0% {
        transform: rotate(90deg);
    }
    25% {
        transform: rotate(0deg);
    }
    50% {
        transform: rotate(-90deg);
    }

    75% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(90deg);
    }
}
.d-div{
    animation: spin-reverse 10s infinite linear;
}
.avatar{
    animation: spin 10s infinite linear;
    transform-origin: 50% 150px;
}
</style>
<div style="height:150px;border:solid 1px #888;position:relative;width:100%;">
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg" style="position:absolute;width:100%;">
         <circle cx="50%" cy="150" r="100" stroke="green" fill="transparent" stroke-width="2"></circle>
    </svg>
    <img src="/images/github.png" class='avatar' style="width:100px;height:100px;border-radius: 50%; margin: 0 auto; display: block;">
</div>


这是一个旋转动画，元素在沿着环形路径移动的同时，自身也会围绕圆心发生旋转。这并不是我们想要的平移效果。


利用多元素的变形相消

假如有一个应用了旋转变换函数的元素是：
```
<div style="transform:rotate(45deg) rotate(-45deg)"></div>
```
这个元素其实是没有旋转的，因为两个旋转变换函数刚好抵消。它等同于：
```
<div style="transform:rotate(45deg)">
    <div style="transform:rotate(-45deg)"></div>
</div>
```

<div style="height:150px;border:solid 1px #888;position:relative;width:100%;">
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg" style="position:absolute;width:100%;">
         <circle cx="50%" cy="150" r="100" stroke="green" fill="transparent" stroke-width="2"></circle>
    </svg>
    <div class='avatar'>
      <img src="/images/github.png" class='d-div' style="width:100px;height:100px;border-radius: 50%; margin: 0 auto; display: block;">
    </div>
</div>


只使用单个元素

一个元素的多个变换函数可以分散给多层元素。反过来，多层元素的变换函数，也可以集中到单个元素。
这个思路是可行的，只不过，有一个必须解决的问题，就是transform-origin。

* 从一个单位矩阵（identity matrix）开始

* 根据transform-origin的x、y、z坐标值，进行平移（translate）

* 从左向右依次对transform里的变换函数执行乘法

* 根据transform-origin的x、y、z坐标值，进行反向平移

transform-origin在这里被表述为两次方向相反的平移，也就是说，transform-origin并不是什么特别的东西，它可以被translate()替代。

举个栗子
```
.avatar{
    transform: rotate(30deg);
    transform-origin: 200px 300px;
}
```
等效于
```
.avatar{
    transform: translate(200px, 300px) rotate(30deg) translate(-200px, -300px);
    transform-origin: 0 0;
}
```

利用前面的原理，我们把前面两个元素的transform-origin的差异抹去（全部变为transform-origin: 0 0;的等效），转移到transform上：

