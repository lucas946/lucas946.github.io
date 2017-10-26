---
title: mac下彻底删除软件技巧
date: 2017-10-26 20:10:58
tags: 软件安装
---
本文介绍了在macOS下手动完全卸载GUI软件的方法
<!--more-->
1. 删除app内容包

   ```
   rm -r /Applications/softwarename.app
   ```

2. 删除配置文件（config）

   ```
   rm -r ~/Library/Preferences/softwarename
   ```

3. 删除系统文件（system）

   ```
   rm -r ~/Library/Caches/softwarename
   ```

4. 删除插件（Plugins）

   ```
   rm -r ~/Library/Application\ Support/softwarename
   ```

5. 删除日志（Logs）

   ```
   rm -r ~/Library/Logs/softwarename
   ```
