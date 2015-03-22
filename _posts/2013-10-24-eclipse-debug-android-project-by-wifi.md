---
layout: post
title: 脱离数据线，使用Eclipse通过WIFI调试Android程序
---

通过如下步骤，可以很方便的通过wifi调试Android程序：

<!--more-->

1、root手机；

2、到市场下载Android Terminal Emulator应用并安装（Android Terminal Emulator是一款安卓手机上使用的终端模拟器，可以进行linux命令集），或者到[这里下载](http://as.baidu.com/a/item?docid=3185735)；

3、安装后打开，输入如下命令：

```csharp
su //获取超级用户权限
setprop service.adb.tcp.port 5555  //设置监听的端口，端口可以自定义，如5554，5555是默认的
stop adbd  //关闭adbd
start adbd  //重新启动adbd
```

4、看一下手机的IP，并记下来，比如：192.168.1.111；

5、在电脑上，上运行cmd命令提示符，切换目录至adb文件所对应文件夹，如：D:\Android\android-sdk\platform-tools，键入如下命令：

`adb connect 192.168.1.111:5555`

如果提示连接成功，则说明搞定了。

6、在Eclipse中运行调试应用吧，Enjoy~

