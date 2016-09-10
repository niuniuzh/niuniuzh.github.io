---

layout: post
title: "Windows下搭建OctoPress"
date: 2016-08-16 22:34:26 +0800
comments: true
categories: web

---

-------------------------------------------------------------------------------

很早就想要搭建一个博客，懒死了。记录一下搭建过程，以作备忘。

Github

申请一个github账号，创建一个仓库，方便代码托管。仓库格式： yourusername.github.io

Ruby

默认安装，添加环境变量，查看Ruby版本。

```
ruby --version
```
DevKit

下载解压到某个目录，shift右键在此处打开命令窗口，执行如下口令。
```
cd DevKit
ruby dk.rb init 
ruby dk.rb install
```
<!-- more -->
Octopress

在安装Octopress之前，确保安装了git，使用下面命令下载Octopress。

```
git clone git://github.com/imathis/octopress.git octopress
cd octopress
gem install bundler
bundle install
rake install
```
安装Octopress主题
```
rake install
```
编写文章
```
rake new_post['title'] 
```
生成一个markdown文件，使用markdown编辑完成之后，执行
```
rake generate
rake preview
```
然后打开http://127.0.0.1:4000/ 看看效果,没有问题就可以发布了。

部署到github上，运行
```
rake setup_github_pages
```
此时会要求输入仓库的url，git@github.com:yourusername/yourusername.github.io，设置成功之后，将本地代码同步到github上面
```
rake deploy 
git add .
git commit -m "comment"
git push origin source
```

$$
\begin{align}
\mbox{Union: } & A\cup B = \{x\mid x\in A \mbox{ or } x\in B\} \\
\mbox{Concatenation: } & A\circ B  = \{xy\mid x\in A \mbox{ and } y\in B\} \\
\mbox{Star: } & A^\star  = \{x_1x_2\ldots x_k \mid  k\geq 0 \mbox{ and each } x_i\in A\} \\
\end{align}
$$

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

```cpp
int main()
{
    int a=10;
    int b=20;
    return 1;
}
```
AT&T
