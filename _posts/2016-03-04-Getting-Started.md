---
layout: post_layout
title: 开始篇
time: 2016.03.05
author: 李朋飞
published: true
excerpt_separator: "///"
---

我的第一篇 github 博客, 本博客使用 [jekyll](http://jekyll.bootcss.com/) + [bootstrap](http://v3.bootcss.com) 搭建!

感谢 [github](https://github.com) 提供的 Github Pages 功能!

此博客布局参考了 [Monkey Snatch Banana](http://www.monkeysnatchbanana.com/) 博客

个人页面应用了 [resumecard](http://ddbullfrog.github.io/resumecard/) 项目


///


# 关于博客撰写

撰写的博客的开头长得这个样子：

	layout: post_layout
	title: 开始篇
	time: 2016.03.05
	author: 李朋飞
	published: false
	excerpt_separator: "|||"

如以上说明，更改相关的名称，会依次做对应。需要注意

- published 参数，如果为 false 则不会在博客里展示
- excerpt_separator 参数，表示的自定义符号以上，是主页上摘要

# fork以及pull request

可以在自己的github上 fork < https://github.com/alpharec/alpharec.github.io.git> 项目，

在同步代码时有两个问题：

1. 自己 fork 的库修改的代码同步到alpharec，这时候需要手工提交 pull request。
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
