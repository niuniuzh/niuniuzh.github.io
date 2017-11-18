---
layout: post
title: "搭建git服务器"
date: 2017-11-18 12:01:08 +0800
comments: true
categories: github
---
## 在ubuntu上搭建git服务器
1.安装git和ssh.
```
sudo apt install git
sudo apt install openssh-server openssh-client
```

2.创建一个git用户，用来管理git服务器,设置密码.
```
sudo adduser git
```
在/home目录下会生成一个git文件夹.
<!--more-->

3.创建ssh证书认证文件,临时修改authorized_keys文件的权限,并把需要访问git服务器的客户端公钥id_rsa.pub的内容复制到authorized_keys文件
```
sudo mkdir /home/git/.ssh
sudo touch /home/git/.ssh/authorized_keys
sudo chmod 777 /home/git/.ssh/authorized_keys
cat xxx >> authorized_keys
```

4.如何生成ssh-keys
```
ssh-keygen -t rsa -C "email address"
```

5.修改authorized_keys文件的权限,修改所属git
```
sudo chmod 700 /home/git
sudo chmod 700 /home/git/.ssh
sudo chmod 600 /home/git/authorized_keys
sudo chown -R git:git /home/git
sudo chown -R git:git /home/git/.ssh
sudo chown -R git:git /home/git/.ssh/authorized_keys
```

6.禁用shell登录.出于安全考虑，第二步创建的git用户不允许登录shell，这可以通过编辑/etc/passwd文件完成.
```
git:x:1001:1001:,,,:/home/git:/bin/bash
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
```

7.初始化Git仓库
```
sudo mkdir /home/xxxx
sudo git init --bare test.git
sudo chown -R git:git /home/xxxx/test.git
```

8.通过git clone命令克隆远程仓库了，在各自的电脑上运行
```
git clone git@192.168.1.100:/home/xxxx/test.git
```

