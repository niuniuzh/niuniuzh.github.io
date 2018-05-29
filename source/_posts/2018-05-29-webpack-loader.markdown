---
layout: post
title: "webpack loader"
date: 2018-05-29 09:09:52 +0800
comments: true
categories: webpack
---

## loaders
webpack 可以使用 loader 来预处理文件。这允许你打包除 JavaScript 之外的任何静态资源。

loader 通过在 require() 语句中使用 loadername! 前缀来激活，或者通过 webpack 配置中的正则表达式来自动应用。

<!--more-->

使用实例：
```
module.exports = {
  module: {
    rules: [
      { test: /\.css$/, use: 'css-loader' },
      { test: /\.ts$/, use: 'ts-loader' }，
      exclude: /(node_modules|bower_components)/,
      include: /(src)/
    ]
  }
};
```

{ test: Condition }：匹配特定条件。一般是提供一个正则表达式或正则表达式的数组，但这不是强制的。

{ include: Condition }：匹配特定条件。一般是提供一个字符串或者字符串数组，但这不是强制的。

{ exclude: Condition }：排除特定条件。一般是提供一个字符串或字符串数组，但这不是强制的。

{ and: [Condition] }：必须匹配数组中的所有条件

{ or: [Condition] }：匹配数组中任何一个条件

{ not: [Condition] }：必须排除这个条件

参考[webpack loaders 文档](https://webpack.docschina.org/loaders/ 'loaders')
