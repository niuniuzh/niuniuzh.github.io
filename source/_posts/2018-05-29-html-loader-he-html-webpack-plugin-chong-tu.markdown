---
layout: post
title: "html-loader 和 html-webpack-plugin 冲突"
date: 2018-05-29 21:51:11 +0800
comments: true
categories: webpack
---

今天在学习webpack的时候，使用html-webpack-plugin的模板，生成的html始终不能解析。
不知道是什么问题，之前还是可以解析的。

后来发现删除掉html-loader以后，可以正常解析了。上网查了一下，这个问题还真不少。
html-webpack-plugin解析模板时使用的是lodash来解析，而配置了html-loader后，
则对html页面会使用html-loader来解析模板文件，因此会导致模板没有解析。

<!--more-->

方法1：亲测,添加exclude排除index.html模板

```
var htmlWebpackPlugin = require('html-webpack-plugin');
var path = require('path');
module.exports = {
    module: {
        rules: [
            {
                test: /\.html$/,
                exclude: path.resolve(__dirname,'index.html'),
                use: {
                    loader: 'html-loader',
                }
            }
        ]
    },
    plugins: [
        new htmlWebpackPlugin({
            filename: 'index.html',
            template: 'index.html',
            inject: 'body',
            title: 'web app test'
        })
    ]
};
```

方法2：去掉webpack.config.js文件中配置的全局html-loader

这样html模版文件就不会被html-loader解析，我们可以使用ejs语法嵌入其他html页面和图片资源。因为没了全局的html-loader解析html文件，使用ejs语法嵌入的资源返回的是ejs代码，还需要使用html-loader来解析成html代码。

（html-loader!）表示引用html-loader这个加载器来解析

<%= require('html-loader!../layout/left.html') %>
