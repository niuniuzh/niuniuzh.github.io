---
layout: post
title: "webpack install"
date: 2018-05-15 20:32:33 +0800
comments: true
categories: webpack
---

webpack是js项目的一个打包工具，可以分割代码，按需加载，提高启动速度。

webpack产生背景：

* 多js文件下全局对象的冲突；
* 模块的加载顺序问题；
* 解决模块或者库的依赖问题；
* 模块过多难以管理；

<!--more-->

webpack的作用：

* 将所有的依赖拆分成块且按需加载
* 首屏加载耗时少
* 所有的静态文件都是一个模块（css和图片等静态文件）
* 第三方库也可以作为一个模块被加载
* 自定义程度高，你可以按需自定义打包的整个流程
* 适用于大project的开发场景

## 安装

webpack使用npm安装，
```
npm install -g webpack
npm install webpack --save-dev
```

## 配置

webpack默认使用当前目录下的webpack.config.js,也可以通过命令指定自定义配置文件。
```
webpack --config webpack.my.config.js
webpack --config webpack.config.js
```

## 配置简介

webpack配置文件大致上分几个部分，entry,output,loaders,plugins,mode。

### entry
entry用来指定打包的入口，可以有多个入口。
```
module.exports = {
    entry:'./index.js'
    output:{
        filename:'bundle.js',
        path:__dirname
        }
}
```
### output
output用来指定打包后文件名字和保存的位置，也可以有多个。
```
module.exports = {
    entry:['./index.js','./a.js']
    output:{
        filename:'[name].js',
        path:__dirname
        }
}
```

### loaders
loaders可以将任意类型的模块转换为js代码的模块，然后在打包，拆分，加载。
比较常用的有css-loader,style-loader.使用之前要先安装，
npm install --save-dev css-loader style-loader.
test:正则表达式，loaders加载解析要用的loaders.
```
module.exports = {
    entry:['./index.js','./a.js']
    output:{
        filename:'[name].js',
        path:__dirname
        },
    module:{
        loaders:{
            test:/\.css$/,
            loaders:['style','css']
        }
    }
}
```

### plugins
plugins可以满足，loaders不可以实现的功能，或者不合适在loaders中实现。
plugins的配置超级简单，在plugins数组中引入要使用的插件，加上配置就ok了。
```
const HtmlWebpackPlugin = require('html-webpack-plugin'); //installed via npm
const webpack = require('webpack'); //to access built-in plugins

const config = {
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};

module.exports = config;
```

### mode
mode有三种模式可以设置，development,production,none.默认设置是production.
```
module.exports = {
  mode: 'production'
};
```
参看[webpack中文文档](https://webpack.docschina.org/concepts "webpack")
