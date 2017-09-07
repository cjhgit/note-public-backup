# 爬虫

网上推荐的 Python 爬虫学习之路：

* 学习 Python 的基本语法。
* Scrapy
* 存储（Mongodb）
* 分布式爬虫：[python-rq](https://github.com/nvie/rqrq) 和 [Scrapy(darkrho/scrapy-redis)]()
* 网页析取(grangier/python-goose · GitHub)

## Scrapy

[英文文档](https://doc.scrapy.org/en/latest/intro/install.html)

[中文文档](http://scrapy-chs.readthedocs.io/zh_CN/0.24/)

### pip 安装

pie 是 Python 的包管理工具。

下载 [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py) Python 脚本文件，执行：

```text
$ python get-pip.py
```

执行成功后，在 `Python 安装目录/Scripts` 下可以看到 pip.exe、pip3.6.exe、pip3.exe 等文件，说明安装成功。

### 安装 Scrapy

使用 pip 安装 Scrapy。

```text
$ pip install Scrapy
```

提示：

```text
 error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ Build Tools": http://landinghub.visualstudio.com/visual-cpp-build-tools
```

需要安装 Microsoft Visual C++ 14.0。

弃坑。

