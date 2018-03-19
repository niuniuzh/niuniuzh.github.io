---
layout: post
title: "CSS Transition介绍"
date: 2018-02-15 13:48:20 +0800
comments: true
categories: css
---

CSS3 transition属性,其实就是动画。平滑的改变CSS的值。
大部分属性都可以使用CSS transition，[Animatable CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)

<!-- more -->

transition CSS 属性是一个简写属性，用于 transition-property, transition-duration, transition-timing-function, 和 transition-delay。 

transition-property:指定过渡的属性值，多个属性值可以逗号隔开。
```
transition-property: width, height, background-color, transform;
```

transition-duration:指定这个过渡的持续时间,如果两个数量不匹配，就截取少的那一个。
```
transition-property: width, height, background-color, transform;
tansition-duration: 2s, 1s, 3s, 5s;
```

transition-delay:延迟过渡时间,属性改变到变换开始之间的间隔时间
```
transition-delay: 5s
```

transition-timing-function:指定过渡动画缓动类型，有ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(),函数改变的变换过程，不会改变结果。
```
transition-timing-function: ease;
transition-timing-function: linear;
```

更多讯息[CSS Transtions](https://www.w3.org/TR/css-transitions-1/)
