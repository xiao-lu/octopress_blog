---
layout: post
title: Mac安装Octopress碰到问题
date: 2013-04-10 06:27
comments: true
categories: [Octopress]
---


关于Octopress的介绍，在其官方网站[Octopress.org](http://octopress.org/ "Octopress.org")上有详细介绍,我就不赘述了，而且在基本每个大大在迁移到Octopress之后都会写相关的教程。

接着我要记录一些碰到的问题及相关解决方法：<!-- more -->

+ 在zsh中调用命令 `rake new_post["新的post"]` 会报
	`zsh: no matches found: new_post[新的post]` 
	错误，网上有好多种解决方法，一种是在.zshrc文件中加 `alias rake="noglob rake"` 
	我测试了之后没有效果。 第二种方法是用命令 `rake "new_post[新的post]"` 经测试有效
	最近发现其实最最正统的解决方案用转义符，即用`\[` 显式转义 '[' 以及用 '\]' 显式转义 ']' 能够解决问题

```	
rake new_post\["新的post"\] 
```

+ 第二个很困扰我的问题是写中文，一开始我的post中不能出现中文，出现中文就不能rake gen_deploy， 折腾了很久后发现是系统变量的问题，最简单的解决方法是设置两个系统变量：


```
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```

