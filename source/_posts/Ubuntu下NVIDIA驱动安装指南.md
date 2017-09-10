---
title: Ubuntu下NVIDIA驱动安装指南
date: 2017-09-10 13:42:31
tags: 软件安装
---
> 安装环境：Ubuntu 16.04 LTS

## 第一步 禁止集成的nouveau驱动

由于Ubuntu自带了集成的第三方nouveau显卡驱动，如果不先去除，将无法安装Nvidia官方驱动。

1. 首先打开命令行界面，输入代码`lsmod | grep nouveau`，这时可以看出命令行有多行输出结果。

2. 在`/etc/modprobe.d/`目录下新建文件名为blacklist-nouveau.conf的文件。

3. 打开blacklist-nouveau.conf，并在其中添加如下代码：

   ```bash
   blacklist nouveau
   options nouveau modeset=0
   ```

4. 更新配置信息，输入命令`sudo update-initramfs -u`，此时需要重启电脑。

5. 重启电脑后会发现电脑显示屏分辨率有明显变化，在命令行界面再次输入代码`lsmod | grep nouveau`，此时无任何输出，说明nouveau驱动已被禁止。

## 第二步 安装Nvidia官方驱动

1. 在命令行界面输入命令`sudo service lightdm stop`以关闭X-window服务。
2. 按住`Ctrl+Alt+F1`进入字符控制台界面。
3. 输入用户名和密码登录系统，并进入显卡驱动所在的文件夹位置。
4. 运行命令`sudo ./NVIDIAXXXXXXXX.run`完成安装。
5. 安装完成后输入命令`sudo service lightdm start`开启X-window服务并进入图形界面，此时可以看到显示屏分辨率已调至最佳。
6. 打开命令行工具，输入命令`nvidia-smi`，此时界面会有显卡信息输出，说明显卡驱动已安装成功。
