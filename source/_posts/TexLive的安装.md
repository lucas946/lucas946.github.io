---
title: TexLive的安装
date: 2017-10-15 23:24:58
tags: 软件安装
---
## TexLive的安装

>安装环境：Ubuntu 16.04 LTS

### 在线安装

在命令行工具界面输入命令：`sudo apt-get install texlive-full`即可。需要下载的文件大概有好几个G，安装时间会比较长。

<!--more-->
### 离线安装

**第一步**：下载镜像，推荐下载地址为[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/)。

 * 进入站点

![进入开源镜像站点](http://orjn2q9xs.bkt.clouddn.com/2017101501.png)



* 获取安装镜像

![获取下载链接](http://orjn2q9xs.bkt.clouddn.com/2017101502.png)

**第二步**：安装

* 安装`perl-tk`以便启动可视化安装界面

  `sudo apt-get install perl-tk`

* 进入镜像文件所在文件夹，挂载镜像文件：

  `sudo mount -t iso9660 -o loop texlive*.iso /mnt/`

* 执行安装：

  `cd /mnt/`

  `sudo ./install-tl --gui=perltk`

* 安装过程：

  将create symlinks in system directories后面的选项设置为Yes，如下图所示，操作顺序：青－> 红－> 蓝－> 黄。等待安装结束即可。(安装所需的磁盘空间较大，在安装之前确保本地有足够的内存)

  ![texlive-install](http://orjn2q9xs.bkt.clouddn.com/2017101503.png)
