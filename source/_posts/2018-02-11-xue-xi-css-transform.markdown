---
layout: post
title: "学习CSS Transform"
date: 2018-02-11 00:30:09 +0800
comments: true
categories: css
---


Transform变换，是css动画里扮演一重要角色。Transform只对block元素有效。使用它，元素可以translate,rotate,scale,skew。

```
img0{width:100px;border-color:red;}
img1{width:100px;border-color:yellow;transform:rotate(20deg);}
img2{width:100px;border-color:green;transform:translate(20px,20px);}
img3{width:100px;border-color:blue;transform:scale(1.2,0.8);}
img4{width:100px;border-color:rebeccapurple;transform:skew(20deg,30deg);}
```
<div style="display:flex;justify-content: space-around;padding-bottom:30px;">
    <img src="/images/github.png" style="width:100px;border-color:red;">
    <img src="/images/github.png" style="width:100px;border-color:yellow;transform:rotate(20deg);">
    <img src="/images/github.png" style="width:100px;border-color:green;transform:translate(20px, 20px);">
    <img src="/images/github.png" style="width:100px;border-color:blue;transform:scale(1.2,0.8)">
    <img src="/images/github.png" style="width:100px;border-color:rebeccapurple;transform:skew(20deg,30deg)">
</div>

<!-- more -->

第一个图片没有任何改变，原本的样式。第二个图片加上一个rotate旋转，从原点(由 transform-origin 属性指定)开始安装顺时针方向旋转元素一个特定的角度。
第三个图片加上一个translate平移，在x方向和y方向移动指定的距离。第四个图片加上一个缩放scale,在x方向和y方向放大缩小指定倍数。第四个图片加上一个skew
倾斜，与x轴或者y轴转动设置的角度。
