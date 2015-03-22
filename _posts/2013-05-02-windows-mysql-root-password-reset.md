---
layout: post
title: 在Windows下Mysql如何重置root用户密码
---

网上的很多在Windows下重置root用户密码的方式无效，这里提供一种有效的方式：

### 第一步：停止MySQL服务：

这可以通过访问服务窗口（管理工具——服务，或者运行——services.msc），停止MySQL服务。

### 第二步：进入MySQL的bin目录：

打开MS-DOS命令行窗口（运行——cmd），输入命令：cd C:\MySQL\bin（这里是安装MySQL的目录）。

### 第三步：输入命令跳过授权表：

输入命令：mysqld.exe -u root –skip-grant-tables

### 第四步：新打开一个MS-DOS命令行窗口，并进入MySQL的bin目录：

和第二步操作相同，注意不要关闭之前那个命令行窗口。

### 第五步：执行下列命令：

输入mysql，回车；

你应该进入了MySQL命令行，输入 use mysql; 回车；

输入 `UPDATE user SET Password = PASSWORD(‘NEW_PASSWORD’) WHERE User = ‘root’;` 回车（注意把里面的NEW_PASSWORD替换成你要修改成的新密码）；

输入 exit; 回车，你应该退出了MySQL命令行。

### 第六步：启动MySQL服务：

关闭所有的MS-DOS命令行窗口，按照第一步的操作找到MySQL服务并启动，如果启动半天没响应，在任务管理器中结束mysqld进程。

执行完以上六步，大功告成。

