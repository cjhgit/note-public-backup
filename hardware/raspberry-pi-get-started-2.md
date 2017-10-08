下载镜像文件

下载：https://www.raspberrypi.org/downloads/raspbian/

如果不需要桌面，可以下载右边的精简版，尤其是网络不好的时候。

2017-09-07-raspbian-stretch.zip

解压得到镜像文件（.img）。

内存卡插入读卡器，读卡器插入电脑。

我的电脑那里找到储存卡，右键，【格式化】。

【文件系统】选择【FAT（默认）】，【开始】。

（格式化的目的是什么？）

> 听说lite版本是精简本，有些驱动都没有


## 下载 win32diskimager

[官方下载](https://sourceforge.net/projects/win32diskimager/)，点击大大的【Download】按钮。

[百度云盘](http://pan.baidu.com/s/1hspIiES)

打开 win32diskimager，选择解压得到的镜像和设备，点击【写入】。等了会儿，系统弹出提示【写入成功】。然后安全弹出TF卡。

新建 `ssh` 文件，根目录

树莓派插入 TF 卡，接通电源，红灯亮起，绿灯闪烁。

网线一端口链接树莓派，另一端链接电脑（已经链接 WiFi，可能不是必须的）。

> 2、共享互联网。
如果现在笔记本已经通过WIFI连接到互联网，可以将无线网卡的互联网资源共享给本地连接。以win7系统为例，
开始——【控制面板】——【网络和 Internet】——【网络和共享中心】——查看网络状态和任务——【更改适配器设置】，找到无线网络连接右键【属性】，
在【共享】选项卡上选中【允许其他网络用户通过此计算机的Internet连接来连接（N）】选项，点确定。
  
运行DOS窗口，输入arp -a，在接口192.168.137.1下的为【动态类型】的IP地址就是树莓派的地址

```text
ping 192.168.191.1
```

## Putty

https://www.chiark.greenend.org.uk/~sgtatham/putty/

点击【Download it here】选择64-bit: 【putty-64bit-0.70-installer.msi】，默认安装即可。

connection refused
  
二、开启 SSH 服务

和 WiFi 配置相似，同样在 boot 分区新建一个文件，空白的即可，文件命名为 ssh。注意要小写且不要有任何扩展名。
树莓派在启动之后会在检测到这个文件之后自动启用 ssh 服务。随后即可通过登录路由器找到树莓派的 IP 地址，通过 ssh 连接到树莓派了。

> Raspbian的基础是Debian操作系统。两位志愿者针对树莓派硬件对Debian进行了专门的优化和移植。
而Raspbian不仅仅是一个OS，它附带着35000个软件包以及预编译的软件。


http://downloads.raspberrypi.org/raspbian/release_notes.txt

> 2017-02-16:
>  * Detection of SSH enabled with default password moved into PAM
  
> 2016-11-25:
>  * SSH disabled by default; can be enabled by creating a file with name "ssh" in boot partition
>  * Prompt for password change at boot when SSH enabled with default password unchanged



https://pan.baidu.com/s/1slG4h5N


## formatter_4

https://www.sdcard.org/downloads/formatter_4/eula_windows/index.html，点击【Accept】下载，默认安装即可。

打开软件，选择要格式化的盘，点击【Format】格式化。


ssh文件在启动一次之后就会删除

绿灯是SD卡的