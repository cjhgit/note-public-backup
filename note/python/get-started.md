# 开始


Python 3.6.2 + 

## 环境搭建（Windows）

访问 [http://www.python.org/download/](http://www.python.org/download/)，点击【Download Python 3.6.2】按钮，进入下载页面。

点击【Windows x86-64 executable installer】下载安装包

安装包区别
* executable installer：可以直接安装。
* web-based installer：需要联网安装。

运行安装包，勾选【Add Python 3.6 to PATH】（勾选后就不需要去配置环境变量）,然后点击【Install Now】即可。

命令行执行 `python -V`，显示正确的版本信息则说明安装成功。

```text
$ python -V
Python 3.6.2
```

遇到的问题：电脑上安装多个 Python，命令行执行 `python` 后显示的不是当前安装版本的信息
解决：everything 搜索 python.exe，把其他 python 安装目录删了。


## IDE

进入官方下载页面 [https://www.jetbrains.com/pycharm/download/](https://www.jetbrains.com/pycharm/download/)，点击 Community 下面的【Download】按钮，下载免费的社区版。

百度云下载：https://pan.baidu.com/s/1gfKkInL。

不喜欢折腾的也可以用文本编辑器什么的。

## Hello World


新建一个文件夹，作为项目根目录，新建 `hello.py`：

`python-demo/hello.py`：

```python
print("Hello, World!");
```

在根目录打开命令行，执行 `python hellp.py`：

```python
$ python hello.py
Hello, World!
```
