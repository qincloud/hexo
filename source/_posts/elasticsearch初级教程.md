title: elasticsearch初级教程
categories: elasticsearch
date: 2018-04-14 10:57:35
tags:
---
### 1.安装elasticsearch

先去elasticsearch[官方网站](https://www.elastic.co/downloads/elasticsearch)下载elasticsearch

由于本人平台是centos7,所以本人选择了tar包

下载完成后解压到/usr/local/下

然后进入elasticsearch/config文件夹下修改elasticsearch.yml文件

``` bash
network.host: 192.168.2.215   #配置ip地址

http.port: 9200 #配置端口号

discovery.zen.ping.unicast.hosts: ["192.168.2.215"] #配置ip地址
```

配置完成后创建一个es用户

``` base
$ useradd es

#创建用户完成后切换到root用户打开/etc/security/limits.conf文件

$ gedit /etc/security/limits.conf

添加以下两行

es hard nofile 65536
es soft  nofile 65536
```

然后进入elasticsearch/bin文件夹下切换到es用户启动elasticsearch

``` base
$ ./elasticsearch
```

然后访问elasticsearch.yml文件里配置的ip地址+端口看到一串json字符串就表示启动成功了,如下

``` base
{
  "name" : "e17kn5H",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "q1W9ZuXySmag-mmqbAjYYw",
  "version" : {
    "number" : "6.2.3",
    "build_hash" : "c59ff00",
    "build_date" : "2018-03-13T10:06:29.741383Z",
    "build_snapshot" : false,
    "lucene_version" : "7.2.1",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```



### 2.curl命令操作elasticsearch

#### 2.1 创建和删除Index

##### 2.1.1 创建一个weather Index
``` bash
[lzq996298643@localhost ~]$ curl -X PUT '192.168.2.215:9200/qincloud'
{"acknowledged":true,"shards_acknowledged":true,"index":"qincloud"}
```

##### 2.1.2 删除weather index
``` bash
curl -X DELETE '192.168.2.215:9200/qincloud'
```

#### 2.2 中文分词器
``` bash

```