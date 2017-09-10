---
title: Ubuntu下CUDA和cuDNN的安装
date: 2017-09-10 13:58:33
tags: 软件安装
---
> 前提条件：已安装NVIDIA显卡驱动
> 安装环境：Ubuntu 16.04 LTS
> Cuda版本：cuda 8.0
> cuDNN版本：cuDNN 5.1
<!--more-->
## 安装Cuda

1. 下载cuda的run安装文件；

2. 进入安装文件所在的文件夹，执行`sudo ./cuda_xxxxx.run`命令；

3. 运行安装命令后会有很多选项需要我们进行选择，第一个选项输入`accept`
   ,第二个选项输入`no`（因为已经安装了nvidia显卡驱动）,其他选项输入`yes`即可；

4. 打开`.bashrc`文件，在文件末尾追加一下几行，配置cuda环境变量：

   ```
   export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
   export CUDA_HOME=/usr/local/cuda
   export PATH=/usr/local/cuda-8.0/bin:$PATH
   ```

5. 关闭`.bashrc`文件，然后在命令行界面输入`source .bashrc`更新设置；

6. 在命令行界面输入`nvcc --version`命令，此时如果界面输出cuda的版本信息，则表名cuda安装成功。



## 安装cuDNN

1. 官网下载cudnn文件，下载需要先注册Nvidia开发者账号；

2. 选择cuDNN v5.1 -> cuDNN v5.1 Library for Linux进行下载；

3. 解压下载文件，然后本地会生成一个cuda文件夹，再进行如下操作：

   ```
   >>>sudo cp cuda/include/cudnn.h /usr/local/cuda/include
   >>>sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
   ```

4. 进入`/usr/local/cuda/lib64`目录，执行如下操作：

   ```
   >>> sudo rm -rf libcudnn.so libcudnn.so.5 #删除原动态链接文件
   >>> sudo ln -s libcudnn.so.5.1.5 libcudnn.so.5  #重新生成软链接
   >>> sudo ln -s libcudnn.so.5 libcudnn.so #重新生成软链接
   ```

5. 如果需要更换cuDNN版本，则替换掉原来的cudnn.h以及libcudnn*文件，再重新生成软链接即可。
