# 阿里云 RDC

### 在阿里云上创建项目 <project-name>。

在应用的根目下创建两个文件。

`<project-name>.release`：

```
# 必填，表示是Node构建
code.language=node8.4

build.command=sh build.sh

build.output = target/*
```

`build.sh`：

```
#!/bin/sh

set -x
echo "====================npm install begin================"
npm install
echo "====================npm install success================"

echo "====================npm build begin================"
npm run build

echo "====================npm build success================"
```

其中，`target` 是项目的构建路径，`npm run build` 命令会生成一个名为 `target` 的目录。

### 服务器配置

在服务器上新建目录 `/root/deploy/<project-name>`，

在目录下新建文件 `deploy.sh`：

```
#!/bin/bash
#任何命令出错则退出停止执行
set -e

TARGET="/usr/local/nginx-app/<project-name>"
SOURCE="/root/deploy/<project-name>"

rm -rfv $TARGET/*

tar zxvf "$SOURCE/package.tgz" -C "$TARGET/"

echo "完成"
```

### 在 RDC 上创建项目，在项目下创建应用。

配置代码内容：

* 程序类型：Web服务器端
* 开发语言：NodeJS
* 版本：8.x

配置应用：

* 应用名：<project-name>
* 部署方式：自定义脚本部署

### 配置环境

【应用】->【环境】->【部署配置】

修改部署方式：RDC 脚本部署

* 下载路径：/root/deploy/<project-name>/package.tgz
* 解压目录：/usr/local/nginx-app/
* Stop：echo "stop"
* start：/root/deploy/<project-name>/deploy.sh
* 执行用户：root


### 编辑流水线

在【发布】那里，编辑流水线。

项目流水线：

开始->构建->日常->预发->正式

流转到下一阶段配置：都不选

预发到正式需要设置为手动部署，预发没出现问题才正式部署。

流水线名称：zktw-front
监听设置：自动触发
master 分支

构建：

* 任务名称：构建
* 代码库地址：<username>/<project-name>.git
* 分支名称：master

日常：

* 任务名称：日常部署
* 包标签：default
* 应用：zktw-front
* 环境：日常环境

预发：

* 任务名称：预发部署
* 包标签：default
* 应用：zktw-front
* 环境：预发环境

正式：

* 任务名称：正式部署
* 包标签：default
* 应用：zktw-front
* 环境：正式环境

【应用】->【环境】->【资源管理】->【关联机器】，可以关联服务器。

## 发布流程

构建阶段会执行项目根目录下的 `<project-name>.release`，设置环境，并执行 `build.sh`，生成构建后的项目资源。并把资源打包，上传到服务器。解压到配置的目录。

## tmp

添加进去的管理员无法修改预发环境  部署配吗？
修改环境里的配置，需要设置为应用的PE
5分钟生效

一般每个项目都有分支，master 分支和 develop 分支。