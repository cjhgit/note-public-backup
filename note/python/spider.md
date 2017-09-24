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

点击[这里](http://www.lfd.uci.edu/~gohlke/pythonlibs)，根据 Python 版本下载以下几个库文件。

* lxml
* zope.interface
* pywin32
* Twisted

百度云：

[lxml-3.7.3-cp36-cp36m-win_amd64.whl](http://pan.baidu.com/s/1bp94n3T)

[zope.interface-4.3.3-cp36-cp36m-win_amd64.whl](http://pan.baidu.com/s/1bOPkdg)

[pywin32-221-cp36-cp36m-win_amd64.whl](http://pan.baidu.com/s/1hsEJK00)

[Twisted-17.1.0-cp36-cp36m-win_amd64.whl](http://pan.baidu.com/s/1i5uyWst)

安装。

```
$ pip install lxml-3.7.3-cp36-cp36m-win_amd64.whl
$ pip install zope.interface-4.3.3-cp36-cp36m-win_amd64.whl
$ pip install pywin32-221-cp36-cp36m-win_amd64.whl
$ pip install Twisted-17.1.0-cp36-cp36m-win_amd64.whl
```

安装 pyOpenSSL。

```
$ pip install pyOpenSSL
```

一般输出：Successfully installed xxx 或 Requirement already satisfied 表示安装成功。

也可以进入 Python 控制台（cmd 执行 `python`）测试是否安装成功（没报错说明安装成功）。

```
$ import lxml
$ import twisted
$ import OpenSSL
$ import zope.interface
```

安装 scrapy。

```
$ pip install scrapy==1.1.0rc3
```

完成。

## 参考

* [Scrapy 0.24 文档](http://scrapy-chs.readthedocs.io/zh_CN/0.24/)







错误：

```
import win32api
ImportError: DLL load failed: 找不到指定的模块。
```

解决：

:\install\python-3.6.2\Lib\site-packages\pywin32_system32 下的 pythoncom36.dll 和 pywintypes36.dll 复制到 :\Windows\System32 文件夹下。

错误：

```
TypeError: 'float' object is not iterable
```

相关 issue [scrapy/issues/2606](https://github.com/scrapy/scrapy/issues/2606)

网上说安装 Twisted 16.6.0 可以解决

```
pip install Twisted==16.6.0
```

运行这个命令一直报错：

```

building 'twisted.test.raiser' extension
    error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ Build Tools": http://landinghub.visualstudio.com/visual-cpp-build-tools
  
```

因为网络原因，又下不到 Twisted-16.6.0-cp27-cp27m-win_amd64.whl。

最后是安装最新版的 scrapy（1.4.0）解决的。

```
pip uninstall twisted
pip install twisted
```

Twisted 16.6 下载地址：https://twistedmatrix.com/Releases/Twisted/16.6/。




 import requests
ModuleNotFoundError: No module named 'requests'


pip install requests




scrapy startproject doubanbook
scrapy crawl dmoz

scrapy genspider dbbook https://www.douban.com/doulist/1264675/


Scapy实现SYN泛洪攻击
http://www.cnblogs.com/mrchige/p/6495147.html


scrapy genspider position http://www.lagou.com/zhaopin/
  

raise RuntimeError("Package 'json' must not be downloaded from pypi")
    RuntimeError: Package 'json' must not be downloaded from pypi
    
    
    
    NameError: name 'json' is not defined
    
    

'{"success":false,"msg":"\xe6\x82\xa8\xe6\x93\x8d\xe4\xbd\x9c\xe5\xa4\xaa\xe9\xa2\x91\xe7\xb9\x81,\xe8\xaf\xb7\xe7\xa8\x8d\xe5\x90\x8e\xe5\x86\x8d\xe8\xae\xbf\xe9\x97\xae","clientIp":"59.41.118.112"}\n'


免费代理：

* [快代理](http://www.kuaidaili.com/)
* [代理66](http://www.66ip.cn/)
* [西刺代理](http://www.xicidaili.com/)
* [guobanjia](http://www.goubanjia.com/free/gngn/index.shtml)

收费代理：

IP 代理常见主要用途：

* 爬虫采集
* 投票发帖
* 注册抢购


编写代码访问http://www.whatismyip.com.tw/，该网站是测试自己IP为多少的网址，服务器会返回访问者的IP。

同类型网站

http://ip.filefab.com/index.php
