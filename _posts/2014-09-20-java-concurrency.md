---
layout: default
title: 利用github和git来构建博客
---


## 具体步骤

第一步,安装好git,在ubuntu中,可以利用sudo apt-get install git 来安装git
第二步,在github网站中注册一个帐号,然后新建一个项目,在新建好的项目中,点击settings菜单来进行项目设置,在项目设置的options中,有个Automatic page  generator的设置项,然后点击可以自动生成网页代码.
第三步,在终端配置git来连接到github注册的帐号上面,如何连接,可以谷歌之
第四步,建立一个目录,然后cd到这个目录中,运行git init命令,然后运行git remote add 之前在github建立的项目的git文件,然后运行git pull origin master将生成的代码文件下载到本地,然后进行修改


