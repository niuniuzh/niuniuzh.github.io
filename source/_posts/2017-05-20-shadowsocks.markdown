---
layout: post
title: "在ubuntu上安装shadowsocks"
date: 2017-05-20 12:15:42 +0800
comments: true
categories: web
<!--categories: web-->
---
## ubuntu安装shadowsocks
1.通过PPA源安装，设置PPA源
```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt update
sudo apt install shadowsocks-qt5
```

shadowsocks配置

1.打开界面，依次填入server address,server port,password,等等。。。

2连接，把程序启动自动连接勾上，每次启动就会自动连接了

配置全局代理

1.安装GenPAC
```
sudo pip install genpac
sudo pip install --upgrade genpac
```
<!-- more -->
2.下载gfwlist
```
genpac -p "SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" --output="autoproxy.pac" --gfwlist-url
```
3.设置代理

点击网络，选择代理，method为automatic,然后设置文件路径
file:///home/missnote/vpnPAC/autoproxy.pac,大工告成.

安装proxychains

1.安装
```
sudo apt install proxychains
```
2.编辑配置
```
gvim /etc/proxychains.conf
socks4 127.0.0.1 9095 ---> socks5 127.0.0.1 1080
```
3.使用方法

需要代理的前面加上proxychains
```
sudo proxychains you-get
proxychains pip install
```
