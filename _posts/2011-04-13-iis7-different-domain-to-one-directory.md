---
layout: post
title: IIS7多域名绑定同一物理目录，设置不同默认文档的解决方案
---

前两天遇到了IIS7多域名绑定同一物理目录，设置不同的默认文档的问题，因为在一个物理目录下只有一个web.config，并且IIS7把默认文档设置写在这里，导致所有域名的默认文档设置共享，很多人对此束手无策，甚至有人说这是IIS7的bug。

其实IIS7不会比IIS6落后的，这个问题也很好解决，下面是解决方案：

比如我们把www.a.com和www.b.com两个域名都指向c:\wwwroot文件夹
想把www.a.com的默认文档设为目录aaa下的index.htm，www.b.com的默认文档设为目录bbb下的index.htm

1、新建两个站点，一个叫aaa（站点名字自己来起），指向c:\wwwroot文件夹，绑定域名www.a.com；另一个叫bbb，指向c:\wwwroot文件夹，绑定域名www.b.com

2、进入%windir%\system32\inetsrv\config目录（%windir%即windows的安装目录，比如c:\windows）

3、找到applicationHost.config文件，用文本编辑器打开

4、在最后configuration节中加入如下语句

```xml
    <location path="aaa">
         <system.webServer>
            <defaultDocument enabled="true">
               <files>
                     <clear/>
                     <add value="aaa/index.htm"/>
               </files>
            </defaultDocument>
        </system.webServer>
    </location>
    <location path="bbb">
         <system.webServer>
            <defaultDocument enabled="true">
               <files>
                     <clear/>
                     <add value="bbb/index.htm"/>
               </files>
            </defaultDocument>
        </system.webServer>
    </location>
```

5、搞定收工！