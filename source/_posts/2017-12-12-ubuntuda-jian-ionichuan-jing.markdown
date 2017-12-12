---
layout: post
title: "ubuntu搭建ionic环境"
date: 2017-12-12 21:50:53 +0800
comments: true
categories: ionic
---

----------------------------------

首先需要安装node,但是我们要先安装一个nvm,一个管理node版本的神器.
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.7/install.sh | bash
sudo gvim .bashrc
cp -->
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
:wq
source .bashrc
```

<!-- more -->
安装好了,执行一下nvm --version,输出版本号就算成功了.下一步，我们来安装并使用node.
```
nvm install node
nvm use node
nvm ls  --显示安装的版本
nvm ls-remote  --显示可以安装的版本
nvm alias default node  --设置默认node
```
更多参考[github](https://github.com/creationix/nvm "github/nvm")


接下来我们就可以使用npm,安装ionic,cordova啦.
```
npm install -g cordova ionic
```
安装的过程有点漫长,好在还可以安装成功.

创建一个APP,使用命令,ionic会自动生成一个项目
```
ionic start myApp tabs/blank/sidemenu
```

然后切换到项目目录,开启服务.在浏览器就可以看到了.
```
cd myApp
ionic serve
```
更多ionic可以参考[ionic](https://ionicframework.com/getting-started/ "ionic doc")
