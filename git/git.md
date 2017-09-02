# Git 学习笔记 - 入门教程.md

## 版本控制与 Git

如果你写过论文、项目文档、代码或是设计图什么的，你可能经历过同一份文件修改了很多次的情况。这时，你电脑上的某个文件夹里面的文件可能是这样的：

```
项目文档.doc
项目文档新版.doc
项目文档最新版.doc
项目文档最新版2.doc
未标题-1.doc
项目文档最终版.doc
项目文档最终修改版.doc
项目文档最最终版.doc
项目文档最后一次修改.doc
```

其实你的思维里还是有点版本控制的概念的，你保存了每一次修改的版本，因为你知道，如果不这样做，有时候代价是很大的。一旦文件修改并保存了，就无法恢复到以前的版本了。到时候老板一句“还是改回之前的版本吧”，就让你欲哭无泪。

有时候写代码，写着写着就莫名其妙多了一个 bug 出来，你花了一天的时间，未必就能把 bug 找出来。“这功能上一个版本是正常的啊，我没改过相关代码啊”，你愣愣地对着电脑，无从下手。因为你没有版本控制或备份代码的习惯，你根本不知道自己改动了哪些文件。

我还试过写了几天的代码，发现源码找不到了。那种失落感，不知道你有没有体会过。

可见，版本控制很重要。如果你经常写文字、写文档，或者你是设计师、程序猿，你都应该学点版本控制相关的知识。

吃了一些亏，你学聪明了。你在文档里使用了版本号的概念：

```
项目文档1.0.1.doc
项目文档1.0.2.doc
项目文档1.1.0.doc
项目文档1.1.1.doc
项目文档1.1.2.doc
```

你还为每一个版本写了详尽的说明：

版本 | 说明 | 日期
----|------|----
1.0.1 | 第一版  | 2017-08-20
1.0.2 | 修改目录...  | 2017-08-21
1.0.3 | 修改总结...  | 2017-08-22

但是，这种方式是低效的。尤其是在软件开发方面，手动管理版本更是一种灾难。

而且，这还不涉及多人协作。你知道当多个人同时修改一个文件时，你应该怎么合并多个修改吗？一行一行文字地对比？

所以，一个自动化版本控制软件是必不可少的。从古老的 CVS，到 SVN，再到 Git，版本控制软件也在一步步发展。而 Git，是目前最先进最流行最好用的版本控制系统（VCS, Version Control System），没有之一。

## Git for Windows 安装

我们可以到[官网](https://git-for-windows.github.io/)首页，点击蓝色的【Download】按钮下载最新的安装包。

然后使用默认安装选项，一路点击【Next】就行了。

我下载的是最新的 `2.14.1` 版本。

## 开始使用

我创建了一个文件夹：`D:\yunser\git-demo`，作为项目地址，并在里面新建了一个 Markdown 文件 `hello.md`。

趁着诗兴大发，敲下一行诗：

```
鸟宿池边树，僧开月下门。
```

我觉得“开”字用得不好，应该改改。

在改动之前，我需要备份当前的版本。于是我复制了一份。。。不对，是打开了 Git for Windows。

## 初始化项目 Git

每个项目要使用 Git，都必须初始化一次。

### 图形化界面操作

我在 `git-demo` 文件夹鼠标右键，选择【Git GUI here】，看到了这样的界面：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-2.png)

然后点击【Create New Repository】，便出现这样的界面：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-3.png)

点击【Browser】，选择项目文件夹，再点击【Create】按钮，初始化项目就成功了。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-4.png)

### 命令行操作

如果你不讨厌命令行，你也可以在项目文件夹右键菜单选择【Git Bash here】，在命令行输入 `git init`，一句命令搞定！

```
$ git init
Initialized empty Git repository in D:/yunser/git-demo/.git/
```

## 提交项目

初始化项目后，每一次修改，我们都需要提交（Commit）一次项目，提交就是类似“保存当前版本”的意思。

### 图形化界面操作

我们先来看看软件界面，左侧是这样的：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-5.png)

红色的区域表示你添加/修改/删除了哪些文件，绿色的区域表示你要保存的文件。因为有些修改我们可能并不需要保存。

我们可以点击红色区域的文件，把文件移到到绿色区域；或者点击绿色区域的文件，把文件移到红色域名。

当修改的文件比较多时，我们也可以点击下面的「Stage Changed」按钮，把所有红色域名的文件全部移到绿色域名，表示我们要保存所有的文件。

接下来，在输入框里写下提交信息（Commit Message），即当前版本做了哪些改动。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-6.png)

最后点击【Commit】按钮就可以了。

### 命令行操作

命令行操作也很简单，我们只需记住两条命令：

* `git add -A`：表示保存所有改动过的文件。
* `git commit -m "提交信息"`：就是保存当前版本的意思。

```
$ git add -A
$ git commit -m "第一版，写了一句诗"
[master (root-commit) 75052a5] 第一版，写了一句诗
 1 file changed, 1 insertion(+)
 create mode 100644 hello.md
```

## 继续

提交项目后，我们便可以继续修改项目了。经过一番思考，我决定把“开”字改成“推”字，“推”更符合语境。

修改保存后，使用 Git 提交修改：

```
$ git add -A
$ git commit -m "修改“开”为“推”，更符合语境"
```

又经过一番思考，我决定把“推”字改成“敲”字，“敲”更显出夜的宁静。

```
$ git add -A
$ git commit -m "修改“推”为“敲”，更显出夜的宁静"
```

这时，项目已经经过几次修改了，我们可以点击软件顶部菜单【Repository】->【Visualize All Branch History】，查看项目所有的版本：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-8.png)

还可以看到任意版本的任意文件修改了哪些地方：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-9.png)

如果你看到的是一坨类似这样的乱码：`楦熷®挎睜杈规爲锛屽儳寮€鏈堜笅闂ㄣ€`，你只需在 Git bash 执行以下命令，重启软件即可。

```
$ git config --global gui.encoding utf-8
```

如果你想回退到之前某一版本，你只需在版本列表右键菜单，选择【Reset master branch here】，再选择【Hard】，确定即可。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/git-10.png)

## 后续

Git 还有很多功能，这里不再讲述。当你需要其他的功能时，你可以在网上搜索相关的知识。

推荐几篇 Git 教程：

* [Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/)
* [图解Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)
* [git - 简易指南](http://www.bootcss.com/p/git-guide/)
