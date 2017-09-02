# Node.js 学习笔记 - NPM 介绍

## 简介

NPM 是一个包管理工具，使用它可以很方便地下载别人发布的第三方包来使用，或者发布自己编写的包给其他人使用。

## 安装

新版的 Node.js 已经集成了 NPM。我们可以在命令行执行 `npm -v`，如果显示版本信息，则说明电脑上已经安装了 NPM。

```
$ npm -v
3.10.10
```

## 淘宝 NPM 镜像

由于 NPM 的官方服务器在国外，在国内下载 NPM 包比较慢。我们可以通过使用淘宝 NPM 镜像或者搭建私有 NPM 来解决这个问题。

[淘宝 NPM 镜像](http://npm.taobao.org/)是一个完整 `npmjs.org` 镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。

我们可以在命令行执行以下命令来安装淘宝 NPM 镜像：

```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

安装完成之后，我们可以使用 `cnpm` 来代替 `npm`。`cnpm` 支持 `npm` 除了 `publish` 之外的所有命令。

更多信息可以查阅：[http://npm.taobao.org/](http://npm.taobao.org/)。

## NPM 安装模块

npm 安装 Node.js 模块语法如下：

```
$ npm install <Module Name>
```

安装完成后，会在当前目录下生成一个名为 `node_modules` 的文件夹，所有通过 `npm` 安装的模块都存放在这个目录下。

NPM 默认本地安装（local），你可以加上选项 `-g` 来全局安装（global）:

```
npm install <Module Name> -g
```

## NPM 常用命令

命令 | 说明 | 使用
---- | ---
init | 初始化 package.json | npm init
install | 安装模块 | npm install <Module Name>
update | 更新模块 | npm update <Module Name>

## Http-server 示例

前端有些功能，必须在服务器环境下才能实现，通常我们会在电脑上搭建像 Apache、Tomcat、IIS 之类的服务器环境。如果电脑上没有安装这些软件，还是挺麻烦的。

Http-server 是基于 Node.js 的服务器，它可以把任意目录作为服务器的目录，一行命令搞定，很方便！

第零步，全局安装 `http-server`。注意必须全局安装，这样我们才可以在任意目录下使用 `http-server` 命令。

```
$ npm install http-server -g
```

第一步，新建一个目录，新建 `index.html`，写个 Hello world。

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
</head>
<body>
Hello world.
</body>
</html>
```

第二步，命令行进入项目根目录，执行  `http-server` 命令。

```
$ http-server
Starting up http-server, serving ./
Available on:
  http://192.168.3.52:8080
  http://127.0.0.1:8080
Hit CTRL-C to stop the server
```

第三步，浏览器打开 `http://127.0.0.1:8080`。

## 参考

* [NPM 官网](https://www.npmjs.com/)
