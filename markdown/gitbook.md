# GitBook

## GitBook 简介

随着 GIT 和 Markdown 的GootBook


gitbook安装
===========


1. 安装 node 和 npm

略

2. gitbook 安装
npm install -g gitbook-cli


gitbook -V 
查看gitbook是否安装成功。


# Markdown 学习笔记 - Gitbook

## 前言

Markdown 和 Git 是我最喜欢的工具。

我用 Markdown 写作已经一两年了。以前用它来做笔记，最近用它来写博客。

## 准备

1. 安装 NPM。

## Gitbook 安装

全局安装 Gitbook

```
npm install -g gitbook-cli
```

查看 Gitbook 是否安装成功。

```
$ gitbook -V
CLI version: 2.3.0
GitBook version: 3.2.2
```

```
gitbook init
```

## Gitbook 的基本用法

你可以先在本地创建个文件夹，在里面新建两个文件：

* README.md
* SUMMARY.md

这两个文件是必不可少的。

README.md 是书的简介。

SUMMARY.md 是书的目录结构。它的内容一般是这样的：

```
* [第1章](c1.md)
    * [第1节](c1s1.md)
    * [第2节](c1s2.md)
* [第2章](c2.md)
```

想必大家都看得懂，接下来，你只需要完善每一章节的内容。

## 预览

如果你完成文章的撰写，并且把 SUMARY.md 的目录信息补充完整后，你可以执行以下命令：

```
$ gitbook serve -p 8080
...
...
Starting server ...
Serving book on http://localhost:4000
```

然后打开命令行提示的网址。


## Gitbook 客户端

GitBook 并没有限制你用什么编辑器，你可以使用任意一款 Markdown 编辑器或者文本编辑器来写你的文章。

Gitbook 官方也提供了一款编辑器，你可以点击[这里](https://www.gitbook.com/editor/)进入官方的下载页面。点击页面中蓝色的【Download for Windows】按钮进行下载，然后按默认选择安装即可。

菜单选择【Gitbook Editor】->【Open】，打开项目文件夹。

在写这篇文章之前，我没用过 Markdown 编辑器。

注意：不能打开没有配置

## 发布

当你执行命令 `gitbook serve` 时，Gitbook 会在当前文件夹生成一个 `_book` 的目录，你可以直接把该文件夹部署到你的服务器。

Gitbook 官方也提供了相关的服务，你也可以直接

【Sign In】
【Sign in with GitHub】
【+ New】



1. 如果输入gitbook init命令，出现Installing version 2.1.0，
需要耐性等待安装。


