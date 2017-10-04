# Gradle 学习笔记 - 环境搭建

## 前言

以前一直使用 Eclipse 开发 Android，最近换上了 Android Studio。Android Studio 使用 Gradle 作为编译工具，Gradle 就不得不学了。

Gradle 是一个基于 Apache Ant 和 Apache Maven 概念的项目自动化构建工具。这是一篇 Gradle 4.1 的安装教程。

你也可以直接浏览官方的安装教程：[https://gradle.org/install/](https://gradle.org/install/)。

## 准备环境

Windows 10 + Java 1.8.0，并且配置 Java 环境变量 JAVA_HOME。

Gradle 支持主流的操作系统，要求 JDK 或 JRE 版本 7 或以上。你可以执行 `java -version` 来查看 Java 版本。

```powershell
$ java -version
java version "1.8.0_144"
```

## 安装

### 使用包管理器安装

略。

### 手动安装

#### 第一步。[下载](https://gradle.org/releases) 最新的 Gradle 发行包。

官方发行包有两种版本：带源码的（Binary-only）和编译好的（Complete），我们选择第二种。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/gradle-0.png)

#### 第二步，解压发行包。

我的解压目录是：`D:\install\gradle-4.1`。

#### 第三步，配置系统环境变量

把解压目录下的 bin 文件夹路径（我的是`D:\install\gradle-4.1\bin`）添加到 Path 环境变量。

#### 第四步，检查安装

命令行执行 `gradle -v`，显示 Gradle 版本，则说明安装配置成功。

```powershell
$ gradle -v

------------------------------------------------------------
Gradle 4.1
------------------------------------------------------------

Build time:   2017-08-07 14:38:48 UTC
Revision:     941559e020f6c357ebb08d5c67acdb858a3defc2

Groovy:       2.4.11
Ant:          Apache Ant(TM) version 1.9.6 compiled on June 29 2015
JVM:          1.8.0_144 (Oracle Corporation 25.144-b01)
OS:           Windows 10 10.0 amd64
```

如果 环境变量 `JAVA_HOME ` 配置不正确，这时会提示：

```text
ERROR: JAVA_HOME is set to an invalid directory: ...
```

## 参考

* [Gradle 官网](https://gradle.org)

















```
如果我们使用的操作系统是Windows或Linux，我们可以根据以下步骤安装Gradle：
1. 从这个页面下载二进制文件。
2. 解压Zip文件，加入环境变量（在PATH中加入GRADLE_HOME/bin目录）。

如果在安装过程中遇到问题，可以进一步查看官方的安装指南。





1，安装JDK，并配置JAVA_HOME环境变量。因为Gradle是用Groovy编写的，而Groovy基于JAVA。另外，Java版本要不小于1.5.
2，下载。地址是：http://www.gradle.org/downloads。在这里下载你要的版本。


https://gradle.org/docs/


```








```
Gradle 使用指南

Gradle，这是一个基于 JVM 的富有突破性构建工具。Gradle 正迅速成为许多开源项目和前沿企业构建系统的选择，同时也在挑战遗留的自动化构建项目。本教程主要讲解了如何使用 Gradle 构建系统和构建系统过程中涉及的插件。

适合人群
适用于自动化地进行软件构建、测试、发布、部署、软件打包的项目。

学习前提
你需要有 Groovy 语言基础，对 Java 应用开发有一定的了解。


版本信息
书中演示代码基于以下版本：

工具	版本信息
Gradle	1.5
```