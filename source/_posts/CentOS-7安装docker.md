---
title: CentOS 7安装docker
author: 布莱恩特科比酱
top: false
cover: false
toc: true
mathjax: false
date: 2019-12-17 15:20:32
img:
coverImg:
password:
summary:
tags: docker
categories:
---

### 想必大家用CentOS都是用CentOS 7 64位的，貌似CentOS 6和7的安装有细微区别，这里只讲下7的安装方法。昨天刚在虚拟机中CentOS 7中装了下docker，由此写这篇文章记录下这个过程.
##### 几步操作就可以搞定，看有些教程说要先卸载旧的docker，昨天试了下，我用的centos中没有旧的docker引擎，所以就直接装了。
+ 卸载旧版本
	`yum -y remove docker docker-engine docker-common docker-selinux`
+ 安装依赖软件包
	`sudo yum install -y yum-utils device-mapper-persistent-data  lvm2`
+ 设置稳定的仓库(用的阿里云仓库,更快)
	`sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo`
+ 更新软件包索引
	`yum makecache fast`
+ 安装docker-ce
	`sudo yum install docker-ce docker-ce-cli containerd.io`
+ 启动docker
	`sudo systemctl start docker`

+ 验证是否安装成功
	`docker --version`
+ 阿里云镜像加速
	`make -p /etc/docker`
	`gedit /etc/docker/daemon.json`

	 ##### 里面填这些括号里内容(包括括号)
	{
	 "registry-mirrors":["https://dttr1kms.mirror.aliyuncs.com"]
	}
	`systemctl daemon-reload`
	`systemctl restart docker`

+ 卸载docker
	`systemctl stop docker`
	`yum -y remove docker-ce`
	`rm -rf /var/lib/docker`

 ```

 ```