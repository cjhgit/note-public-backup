# Linux 子系统

> 在今年的 Build 2016 上，微软向全世界介绍了他们还处于 Beta 阶段的 Windows 下的 Linux 子系统Windows Subsystem for Linux（WSL），它可以让开发者们在 Windows 10 下通过 Bash shell 运行原生的 Ubuntu 用户态二进制程序。如果你参与了 Windows Insider 计划，你就可以在最新的 Windows 10 年度升级版的 Insider 构建版中体验这个功能了。

1. 系统升级到一周年正式版及以上(1607)
2. 依次在【设置】-【更新和安全】-【针对开发人员】选项中，启用"开发人员模式"
3. 在资源管理器中打开【控制面板】\【程序】-【程序和功能】-【所有控制面板项】-【启用或关闭 Windows 功能】，勾选【适用于Linux的Windows子系统(Beta)】。
4. 重启电脑
5. 命令行运行`lxrun /install /y`开始安装。安装速度取决于网络情况，下载的文件在%localappdata%\lxss目录下lxss.tar.gz(181M)，解压后大概500M,rootfs目录即为子系统根目录。
6. 命令行运行bash进入Ubuntu。默认使用的root帐号登录，通过指令passwd设置密码。



备份系统：`xcopy %localappdata%\lxss %localappdata%\lxss.bak /E`

卸载子系统（可重装）：`lxrun /uninstall /full`。




## ubuntu centos 区别

> centos是来自于RedHat，所以centos支持rpm格式的安装，而ubuntu显然是不支持的



查看当前正在运行的 Ubuntu 的版本号：

```
$ cat /etc/issue
Ubuntu 16.04.2 LTS \n \l
```



在子系统上运行nginx




apt-get install 的用法

apt-get remove的用法



operating system


operating system

operating


需求管理，敏捷开发，持续集成，持续交付





在Linux（ubuntu server）上面安装NodeJS的正确姿势

默认情况下，在apt的源中只有比较老的版本（注意，需要先apt-get update)