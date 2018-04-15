title: superset安装教程
date: 2017-12-03 12:29:03
tags:
categories: 大数据
---
### 安装superset
本人环境centos7

需要安装python,centos7有自带python

一.安装python 的依赖库和pip
``` bash
$ yum install libffi-devel python-devel python-pip python-wheel openssl-devel libsasl2-devel openldap-develhi
```
二.Python virtualenv环境
``` bash
$ pip install virtualenv	#安装virtualenv
$ virtualenv venv	#进入virtualenv环境
```
三.安装superset
``` bash
$ pip install	#更新pip
$ pip install superset	#安装superset
```
四.设置superset账号和密码
``` bash
$ fabmanager create-admin --app superset
Username [admin]: admin
User first name [admin]: liao
User last name [user]: zhq
Email [admin@fab.org]: 996298643@qq.com
Password: 
Repeat for confirmation: 
Recognized Database Authentications.
Admin User admin created.
```

五.更新运行初始化运行superset
``` bash
$ superset db upgrade	#更新superset
$ superset init		#初始化superset
$ superset runserver	#运行superset
Starting server with command: 
gunicorn -w 2 --timeout 60 -b  0.0.0.0:8088 --limit-request-line 0 --limit-request-field_size 0 superset:app

[2017-12-03 14:52:30 +0000] [23159] [INFO] Starting gunicorn 19.7.1
[2017-12-03 14:52:30 +0000] [23159] [INFO] Listening at: http://0.0.0.0:8088 (23159)
[2017-12-03 14:52:30 +0000] [23159] [INFO] Using worker: sync
[2017-12-03 14:52:30 +0000] [23164] [INFO] Booting worker with pid: 23164
[2017-12-03 14:52:30 +0000] [23165] [INFO] Booting worker with pid: 23165
```
http://localhost:8088 访问superset
