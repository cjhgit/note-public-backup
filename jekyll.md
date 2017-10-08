# Jekyll

[Jekyll](1) 是一个静态站点生成器，可以将纯文本转换为静态博客网站。结合 [GitHub Pages](2)，可以搭建一个免费的个人博客网站。

这里有一个非官方的[Jekyll 中文网站](http://jekyllcn.com/)，可以用来参考。

## 环境搭建（Windows）

### 安装 Ruby

安装 Jekyll 需要 Ruby 环境，我们可以到[这里](https://rubyinstaller.org/downloads/)（需翻墙）下载最新安装包（如【Ruby 2.4.2-2 (x64)】），默认安装即可。

也可以到[百度网盘](https://pan.baidu.com/s/1bGc1v4)下载。

命令行执行 `ruby -v`，显示版本信息则说明安装成功。

```text
$ ruby -v
ruby 2.4.2p198 (2017-09-14 revision 59899) [x64-mingw32]
```

Ruby1.9.1 及以后的版本已经自带了 RubyGems（Ruby 的包管理器），无需额外下载。

```text
$ gem -v
2.6.13
```

### 安装 Jekyll

```text
$ gem install jekyll
```

检查一下，已经安装成功了。

```text
$ jekyll -v
jekyll 3.6.0
```

最后，再安装一个库。

```text
$ gem install jekyll-paginate
```

## 下载主题

从[主题列表](http://jekyllthemes.org/)选择一个你喜欢的主题，点击【Download】下载，并解压。

在解压目录打开命令行，执行以下命令：

```text
$ jekyll serve --watch
```

不出意外的外会输出一个网址，在浏览器中打开网址，就可以看到一个静态网站页面。

## 添加自己的文章

项目结构不是很复杂，你可以猜得出每个文件大概是做什么的。

如果要添加一篇文章，在 `_posts` 下有很多示例文章给你参考，你可以把 `_posts` 下的任意一篇文章复制一份，修改文件名和内容（注意格式）。再刷新浏览器就可以看到最新的文章。

你可以将静态网站部署到你的服务器或 GitHub Pages。

## 总结

Jekyll 适合小型的以内容为主的网站。

[1]: http://jekyllrb.com/
[2]: https://pages.github.com/



