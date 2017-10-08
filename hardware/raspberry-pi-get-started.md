## 树莓派入门教程

树莓派入门比较容易。

需要的工具：

* 联网的笔记本电脑
* 树莓派 3B
* Micro SD 卡
* 

下载 [NOOBS](https://www.raspberrypi.org/downloads/noobs/)。进入后，选择左边的，下载，得到 `NOOBS_v2_4_4.zip`。

格式化 Micro SD 卡为 FAT 格式（操作指导）。

192.168.191.4

ping 192.168.191.1
telnet 192.168.191.1 22
ssh -l pi 192.168.191.1

arp -a


## 点亮 LED 灯


# tmp


E:\desktop>ssh -l pi 192.168.191.1
ssh: connect to host 192.168.191.1 port 22: Bad file number

E:\desktop>telnet 192.168.191.1 22
正在连接192.168.191.1...无法打开到主机的连接。 在端口 22: 连接失败


树莓派所使用的系统和软件
http://pan.baidu.com/s/1eSmnU4i 
 
视频教程：  http://pan.baidu.com/s/1jHEZl10 
 
技术讨论群：RPi树莓派技术全国总群 498021441
   
账户名：pi  密码：raspberry
 
树莓派3自编手册：  http://pan.baidu.com/s/1mhDWoCo 
树莓派自编书籍满300送书籍，需要自行下载： 链接：http://pan.baidu.com/s/1c2MpvW0 密码：yzqd
说明书链接：http://pan.baidu.com/s/1jHVYzOE 密码：936c

不用判斷，幾乎所有都是輸出

如果有HDMI线，就能使用笔记本屏幕，对吧？
笔记本上的借口必须是HDMI in借口

上电都是只亮红灯
刷了系统绿灯才亮

红灯闪烁说明电源供电不足
系统运行路灯是闪烁的
进入系统后绿灯闪烁是读取


> Raspbian安装方式有两种，一种是用NOOBS方式安装，还有一种就是把官方的img烧录到Micro SD卡里，前者简单，跟着指引一步一步安装即可，后者相当于Ghost镜像，烧录到SD卡后就等于还原一个已经安装好的系统，只需要配置一下即可运行！
第一种方式，如果你的Micro SD本身就是FAT32那么就不用格式化，只要把NOOBS解压到根目录即可，如果不是，就要格式化，烧录就更不用说了，只是无需你自己格式化……

> 网上找SDFormatter 工具，用这个格式化。树莓派官网上有下载。。。
  因为会把16G分区，分成几个Linux区，windows 只识别五十M的FAT32分区，所以只有50M。。



