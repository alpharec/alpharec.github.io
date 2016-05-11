---
layout: post_layout
title: 开始篇
time: 2016.03.05
author: 刘思喆
published: true
excerpt_separator: "///"
---

很高兴为大家搭建了一个群体知识共享的 github 博客, 本博客使用 [jekyll](http://jekyll.bootcss.com/) + [bootstrap](http://v3.bootcss.com) 搭建!

此博客布局参考了 [Monkey Snatch Banana](http://www.monkeysnatchbanana.com/) 博客，个人页面应用了 [resumecard](http://ddbullfrog.github.io/resumecard/) 项目


///

# 博客的本地预览

安装本地ruby之后

	$ gem install jekyll
	$ cd ~/alpharec.github.io
	~/alpharec.github.io 
	$ jekyll serve
    ====> Now browse to http://localhost:4000
	
这时候会在 alpharec.github.io 下新建一个 `_site` 目录，这个就是展示的静态页面。
因为github上已经帮我们做了这一步，所以每次在 `git push` 时，需要ignore这个目录。


# 关于博客撰写

在 `_post` 目录下存放的是博客内容，比如这篇文章的文件名为 `2016-03-04-Getting-Started.md`，
jekyll会自动将文件名转化为标题，以及将md文件转化为html静态文件。

打开文件之后，文档的开头长得这个样子：

	layout: post_layout
	title: 开始篇
	time: 2016.03.05
	author: 李朋飞
	published: false
	excerpt_separator: "|||"

看命名大概就能猜到什么意思，只要按照模板修改即可。需要注意

- published 参数，如果为 false ，文章则不会在博客里展示
- excerpt_separator 参数，表示的是在自定义符号以上，是首页上摘要

# fork 以及 pull request

可以在自己的github上 fork < https://github.com/alpharec/alpharec.github.io.git> 项目，

需要改变这个博客内容时，需要同步代码，这时面临两个问题：

1. 自己 fork 的库修改的代码同步到 alpharec，这时候需要手工提交 pull request。
2. fork 库的 commits behind alpharec 库

第二个问题解决方式是本fork配置一个remote，先查看远程状态：

	$ git remote -v
	origin  https://github.com/sunbjt/alpharec.github.io.git (fetch)
	origin  https://github.com/sunbjt/alpharec.github.io.git (push)

添加一个远程的上游库给fork，并查看是否成功：

	git remote add upstream https://github.com/alpharec/alpharec.github.io.git
	$ git remote -v
	origin  https://github.com/sunbjt/alpharec.github.io.git (fetch)
	origin  https://github.com/sunbjt/alpharec.github.io.git (push)
	upstream        https://github.com/alpharec/alpharec.github.io.git (fetch)
	upstream        https://github.com/alpharec/alpharec.github.io.git (push)

从上游仓库 fetch 分支和提交点，传送到本地，并会被存储在一个本地分支 upstream/master 

	$ git fetch upstream
	remote: Counting objects: 5, done.
	remote: Compressing objects: 100% (3/3), done.
	remote: Total 5 (delta 2), reused 5 (delta 2), pack-reused 0
	Unpacking objects: 100% (5/5), done.
	From https://github.com/alpharec/alpharec.github.io
	* [new branch]      master     -> upstream/master

把 upstream/master 分支合并到 master 上，完成本地同步；最后 push 到fork库，则完成

	$ git merge upstream/master
	Updating 87b7b87..8960f72
	Fast-forward
	_data/author.yml | 4 ++--
	1 file changed, 2 insertions(+), 2 deletions(-)
	$ git push origin master

# 其他细节

## 数学公式


使用了  mathjax JS插件，可以正常书写 LaTeX 格式公式。

$$
\min_{(\beta_0, \beta) \in \mathbb{R}^{p+1}}\frac{1}{2N} \sum_{i=1}^N (y_i -\beta_0-x_i^T \beta)^2+\lambda \left[ (1-\alpha)||\beta||_2^2/2 + \alpha||\beta||_1\right],
$$

## 关于 about

团队成员的简介，需要自行填写。
