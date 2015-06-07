---
layout: default
title:  linux 使用备忘录
---  
-----
##linux的/boot空间不足解决方法  
在使用Ubuntu过程中，Ubuntu会经常更新内核的版本，在桌面系统中，一般都会自动弹出跟新的窗口。然后有时候
会遇到/boot空间不足的情况从而导致系统更新失败。出现这种情况的原因是Ubuntu不会自动删除掉旧的的内核版本，
从而导致/boot的空间被一些旧的内内核占据，而这些旧的内核对于我们来说是没有用的，所以可以将其删掉，这样就
可以腾出空间来更新了。当然，最好不要直接到/boot目录下删掉相关的目录文件，可以使用sudo apt-get autoremove
这个命令来删掉一些不需要的内核文件。但是这个命令会删的不彻底，这个时候需要找出系统中安装哪些内核文件，
然后使用sudo apt-get remove的命令将其删掉。具体步骤如下:  
> *运行 uname -a 来查看当前系统使用的是那个版本的内核，然后记下其版本号  

> *运行dpkg --get-selecttions | grep linux-image来查找出系统已经安装的内核版本，在系统中的运行结果如下:  
> linux-image-3.13.0-52-generic         deinstall  
> linux-image-3.13.0-53-generic         deinstall  
> linux-image-3.16.0-30-generic         deinstall  
> linux-image-3.16.0-33-generic         deinstall  
> linux-image-3.16.0-34-generic         deinstall  
> linux-image-3.16.0-36-generic         install  
> linux-image-3.16.0-37-generic         install  
> linux-image-extra-3.13.0-52-generic       deinstall  
> linux-image-extra-3.13.0-53-generic       deinstall  
> linux-image-extra-3.16.0-30-generic       deinstall  
> linux-image-extra-3.16.0-33-generic       deinstall  
> linux-image-extra-3.16.0-34-generic       deinstall  
> linux-image-extra-3.16.0-36-generic       install  
> linux-image-extra-3.16.0-37-generic       install  
> linux-image-generic-lts-utopic            install  
> 其中linux-image-3开头的为系统安装的内核版本，deinstall表示已经卸载,
> install表示已经安装的内核版本。然后使用sudo apt-get remove 删除不需要的内核版本即可，一般留下最近两个版本的内核。因为新版的内核可能不稳定，这样可以
> 切换之前稳定的版本。  

---------  
##Ubuntu下查看和下载命令的源码  
----------  
在Ubuntu有一些常用的命令，这些命令很强大高效。若想了解其的内在实现，在网上搜其源代码也是一件麻烦费时的事情。可以通过如下方法方便获取命令的源码。  
+查询命令源码所在的包是是什么。dpkg -S $(which comman)  
+下载对应包的源码。 sudo apt-get -d source "package"  
如要查看more命令的源码:  
```
dpkg -S $(which more)  

``` 
结果如下:
```  
[liang@liang-xing:~]$dpkg -S $(which more)
util-linux: /bin/more
sudo apt-get -d source "util-linux"  

```    
