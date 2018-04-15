title: hexo安装实验
date: 2017-12-02 17:44:32
tags:
categories: hexo
---
### hexo小白傻瓜安装教程

[参考博客](http://www.jianshu.com/p/e99ed60390a8)

安装hexo之前必须安装node.js和git

以下将从我的环境下说明如何安装node.js和hexo

我的电脑环境是centos7

首先下载和安装node.js

###### 第一步下载node.js

node.js[下载地址(我已经上传到csdn)](http://download.csdn.net/download/u013244517/10142740)

###### 第二步安装node.js

解压后使用命令　
``` bash
$ tar --strip-components 1 -xzvf node-v* -C /usr/local 
```
可直接copy到/usr/local对应文件夹下面

使用以下命令如果和下面的结果相同说明已经安装好了node.js

``` bash
$ npm -v
5.5.1

$ node -v
v9.2.0
```

##### 安装好了node.js后就可以开始安装hexo
###### 一.下载安装hexo
``` bash
$ npm install -g hexo
$ npm install -g hexo-cli
```
安装好hexo以后，在终端输入：
``` bash
$ hexo
```
如果没有提示找不到该命令说明安装成功。

###### 二.初始化hexo

// 建立一个博客文件夹，并初始化博客，<folder>为文件夹的名称，可以随便起名字

$ hexo init ${文件夹}

// 进入hexo博客文件夹，${文件夹}为文件夹的名称

$ cd ${文件夹}

// node.js的命令，根据博客既定的dependencies配置安装所有的依赖包

$ npm install

// 安装hexo admin界面功能

$ npm install --save hexo-admin-qiniu

``` bash
$ hexo init /home/lzq996298643/services/hexo
$ cd /home/lzq996298643/services/hexo
$ npm install
$ npm install --save hexo-admin-qiniu
```

安装完成后可以在/home/lzq996298643/services/hexo看到博客文件夹

###### 三.发表一篇文章和启动hexo
###### 必须要在hexo初始化的文件夹下面(/home/lzq996298643/services/hexo)亲测

// 新建一篇文章

hexo new "文章标题"

//启动hexo

hexo server

如果看到以下输出就表明启动成功
``` bash
$ hexo server
(node:6187) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
http://localhost:4000 或 http://localhost:4000/admin 访问

