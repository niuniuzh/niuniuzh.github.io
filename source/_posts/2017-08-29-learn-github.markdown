---
layout: post
title: "Learn Github"
date: 2017-08-29 20:02:01 +0800
comments: true
categories: github
---
## 在ubuntu上安装git
1.打开终端输入
```
sudo apt install git
git
```
如果是在windows上安装，使用[msysgit](https://git-for-windows.github.io "msysgit")

<!-- more -->
2.配置用户信息
```
git config --global user.name 'Your name'
git config --global user.email 'email@gmail.com'
git config --global core.editor emacs || gvim
```

3.检查配置信息
```
git config --list
git config <key>
```

4.使用帮助
```
git help <verb>
git <verb> --help
man git-<verb>
git help config
```

5.初始化仓库
```
mkdir test && cd test
git init
git clone <url> ~/test
```

6.修改和提交
```
git status
git diff
git add -A -v
git add .
git add <file>
git mv <old> <new>
git rm <file>
git rm --cached <file>
git commit -m "message"
git commit --amend
```

7.忽略文件
```
.gitignore规则
空行#开头会被忽略
glob正则匹配
[abc],*,?[0-9],a/**/z
!取反

*.a
!lib.a
/TODO
build/
doc/*.*
doc/**/.*
```

8.查看历史
```
git log
git log -p -n
git log --stat
git log --pretty=oneline
git log --pretty=format:""
git log --graph
```

9.GIT撤销操作
```
git commit --amend
git reset HEAD <file>
git checkout --<file>
```

10.ssh-key
```
ssh-keygen -t rsa -C "youremail@example.com"
git remote -v    查看远程仓库
git remote add something git@github.com:xxxx/xxxx
git push -u origin master
git remote show origin
git remote rename xx  yy
git remote rm xx
```

11.添加tag
```
git tag    --列出所有tag
git tag -a v1.1 hashkey
git show v1.1    --显示v1.1
git push origin tagname
git push origin --tags
git tag -d v1.1    --删除tag
git push origin --delete tag v1.1
git push origin :refs/tags/v1.1
git checkout -b [branchname] [tagname]    --检出
```

12.alias配置别名
```
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.cm commit
git config --global alias.br branch
git config --global alias.unstage 'reset HEAD'
git config --global alias.last 'log -1'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

13.创建合并分支
```
git branch haha    --创建分支haha
git checkout haha    --切换分支haha
git checkout -b haha    --创建并切换分支haha
git merge haha    --合并分支haha
git branch -d haha    --删除分支haha
git mergetool    --解决冲突
git push (remote) (branch)
git push origin --delete haha
git rebase [basebranch] [topicbranch]
```

14.其他git命令
```
git stash    --储藏
git stash pop
git stash apply
git commit --amend    --修改最后一次提交
git rebase -i HEAD~3    --最近n次提交
```

[gitbook](https://git-scm.com/book/zh/v2/ "gitbook")
