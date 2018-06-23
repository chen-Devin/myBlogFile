---
title: 我的hexo搭建学习过程
date: 2017-03-19 18:23:37
tags: 学习
---
#hexo使用介绍

```
Hexo是1个工具,可以快速的将markdown文件转换为一个博客网站.
```

* [Hexo官网](https://hexo.io/)
* 台湾人开发. 有比较详尽的中文文档.
* hexo是基于nodejs开发的一个工具.
* 
<!-- more -->

## 1. 简单使用

* 使用npm工具全局安装hexo环境

  * `npm install hexo-cli -g`
    * cli  --commandline 命令行. ping npm 
    * gui 图形界面.

* 初始化博客目录

  * 在需要创建博客的目录下.
  * `hexo init myBlog`   
  * 会在当前目录下创建1个myBlog文件夹. 并联网下载一些初始化文件

* 启动服务

  * `hexo server`
  * 打开提示的网页地址 就可以看见博客页面

  ***

  ​

## 2.发表新文章

* 使用命令来发表新文章

* `hexo new 学习使用hexo`

* 会生出一个.md文件

* 在这个文件中编辑.md文件. 该md文件的内容就是发布的博客.

* 重新启动`hexo s` 打开网页就可以看到新发表的文章.

  ***

  ​

## 3. 主题安装

* 许多第三方为hexo提供了主题, 我们可以搜索并使用.

* 选择你想用的主题

* 按照官方文档下载最新版本

* 将解压缩后的目录复制到博客目录下的themes目录下.

* 并将其改为1个较为简单的名字如：`yilia`

* 修改博客目录下的_config.yml文件.

* 修改theme: l配置项为yilia

* 重启服务

* 就可以看到新使用的主题效果了.

  ***


## 4. 部署博客

1: Hexo deploy 提供了快速方便的一键部署功能，只需一条命令就能将网站部署到服务器上。

2:在开始之前，您必须先在 _config.yml 中修改参数，一个正确的部署配置中至少要有 type 参数，如部署到github上

	deploy:
		type: git
		repo: git@github.com:chen-Devin/chen-Devin.github.io.git<>
		branch: master
		message: '这是我的博客'

3 hexo g  生成静态html网页
	
	会在页面中增加一个public文件夹，里面就是最终生成的博客网页

4 hexo d 将代码部署到服务器




  ​